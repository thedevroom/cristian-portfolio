# GSAP Animation Patterns & Best Practices

**Foundation**: Study https://github.com/greensock/gsap-skills before implementing animations.

## Core Principles

1. **Performance First**: Use hardware acceleration (transform, opacity only when possible).
2. **Cleanup Always**: Every animation must be killed in `useEffect` cleanup.
3. **Respect Motion Preferences**: Check `prefers-reduced-motion` before animating.
4. **Timeline > Individual Tweens**: Use timelines for coordinated animations.
5. **Precise Timing**: Use millisecond-level control for premium feel.

## Essential Pattern: useGsapAnimation Hook

```typescript
// src/hooks/useGsapAnimation.ts
import { useEffect, useRef } from 'react';
import gsap from 'gsap';

/**
 * Custom hook for managing GSAP animations with automatic cleanup.
 * @param callback - Function that returns the animation timeline or tween
 * @param dependencies - Effect dependencies
 */
export const useGsapAnimation = (
  callback: () => gsap.core.Timeline | gsap.core.Tween,
  dependencies: React.DependencyList = []
) => {
  const animationRef = useRef<gsap.core.Timeline | gsap.core.Tween | null>(null);

  useEffect(() => {
    animationRef.current = callback();

    return () => {
      if (animationRef.current) {
        animationRef.current.kill();
      }
    };
  }, dependencies);

  return animationRef;
};
```

## Animation Patterns by Use Case

### 1. Entrance Animations (On Mount)

```typescript
'use client';

import { useRef } from 'react';
import gsap from 'gsap';
import { useGsapAnimation } from '@/hooks/useGsapAnimation';

export const AnimatedSection = () => {
  const containerRef = useRef<HTMLDivElement>(null);

  useGsapAnimation(() => {
    if (!containerRef.current) return gsap.timeline();

    const timeline = gsap.timeline();
    timeline
      .from(containerRef.current.querySelector('.title'), {
        opacity: 0,
        y: 30,
        duration: 0.8,
        ease: 'power2.out',
      })
      .from(
        containerRef.current.querySelectorAll('.item'),
        {
          opacity: 0,
          y: 20,
          duration: 0.6,
          stagger: 0.1,
          ease: 'power2.out',
        },
        0.2
      );

    return timeline;
  }, []);

  return (
    <div ref={containerRef}>
      <h2 className="title">Title</h2>
      <div className="item">Item 1</div>
      <div className="item">Item 2</div>
    </div>
  );
};
```

### 2. Scroll-Triggered Animations

```typescript
'use client';

import { useRef, useEffect } from 'react';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

export const ScrollAnimatedSection = () => {
  const containerRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (!containerRef.current) return;

    const timeline = gsap.timeline({
      scrollTrigger: {
        trigger: containerRef.current,
        start: 'top center',
        end: 'center center',
        scrub: 1, // smooth scrubbing (1 = 1 second lag)
        markers: false, // disable in production
      },
    });

    timeline
      .from('.parallax-bg', { y: -100, opacity: 0 })
      .from('.parallax-text', { y: 50, opacity: 0 }, 0);

    return () => {
      timeline.kill();
      ScrollTrigger.getAll().forEach((trigger) => trigger.kill());
    };
  }, []);

  return (
    <section ref={containerRef} className="min-h-screen">
      <div className="parallax-bg">Background</div>
      <div className="parallax-text">Text</div>
    </section>
  );
};
```

### 3. Hover Effects (Interactive)

```typescript
'use client';

import { useRef } from 'react';
import gsap from 'gsap';

export const InteractiveCard = () => {
  const cardRef = useRef<HTMLDivElement>(null);

  const handleMouseEnter = () => {
    if (!cardRef.current) return;
    gsap.to(cardRef.current, {
      duration: 0.4,
      scale: 1.05,
      y: -10,
      boxShadow: '0 24px 64px rgba(0,0,0,0.4)',
      ease: 'power2.out',
    });
  };

  const handleMouseLeave = () => {
    if (!cardRef.current) return;
    gsap.to(cardRef.current, {
      duration: 0.4,
      scale: 1,
      y: 0,
      boxShadow: '0 8px 24px rgba(0,0,0,0.25)',
      ease: 'power2.out',
    });
  };

  return (
    <div
      ref={cardRef}
      onMouseEnter={handleMouseEnter}
      onMouseLeave={handleMouseLeave}
      className="bg-gray-800 p-6 rounded-lg cursor-pointer"
    >
      Content
    </div>
  );
};
```

### 4. Parallax Scrolling

```typescript
'use client';

import { useEffect, useRef } from 'react';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

export const ParallaxSection = () => {
  const bgRef = useRef<HTMLDivElement>(null);
  const textRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (!bgRef.current || !textRef.current) return;

    const timeline = gsap.timeline({
      scrollTrigger: {
        trigger: bgRef.current.parentElement,
        start: 'top top',
        end: 'bottom top',
        scrub: 0.5,
      },
    });

    timeline
      .to(bgRef.current, { y: 150, ease: 'none' }, 0)
      .to(textRef.current, { y: -100, ease: 'none' }, 0);

    return () => {
      timeline.kill();
      ScrollTrigger.getAll().forEach((trigger) => trigger.kill());
    };
  }, []);

  return (
    <div>
      <div ref={bgRef} className="h-96 bg-gradient-to-b from-navy to-dark-navy" />
      <div ref={textRef} className="text-4xl font-bold">Parallax Text</div>
    </div>
  );
};
```

### 5. Modal Animations

```typescript
'use client';

import { useRef, useEffect } from 'react';
import gsap from 'gsap';

interface ModalProps {
  isOpen: boolean;
  onClose: () => void;
  children: React.ReactNode;
}

export const Modal = ({ isOpen, onClose, children }: ModalProps) => {
  const backdropRef = useRef<HTMLDivElement>(null);
  const contentRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (!backdropRef.current || !contentRef.current) return;

    if (isOpen) {
      // Open animation
      gsap.timeline()
        .to(backdropRef.current, { opacity: 1, duration: 0.3 })
        .to(contentRef.current, { opacity: 1, y: 0, duration: 0.4, ease: 'back.out' }, 0);
    } else {
      // Close animation
      gsap.timeline()
        .to(contentRef.current, { opacity: 0, y: 20, duration: 0.3, ease: 'power2.in' })
        .to(backdropRef.current, { opacity: 0, duration: 0.2 }, 0);
    }
  }, [isOpen]);

  if (!isOpen && !backdropRef.current) return null;

  return (
    <div ref={backdropRef} className="fixed inset-0 bg-black/50 opacity-0" onClick={onClose}>
      <div ref={contentRef} className="bg-dark-navy opacity-0 translate-y-20 max-w-2xl mx-auto mt-20 rounded-lg">
        {children}
      </div>
    </div>
  );
};
```

## Easing Functions (Recommended)

```typescript
// For GSAP, use these easing functions:
// - 'power1.out' / 'power2.out' / 'power3.out' — natural, smooth exits
// - 'power1.inOut' / 'power2.inOut' — balanced motion
// - 'back.out' — overshoot slightly (good for entrances)
// - 'elastic.out' — bouncy (use sparingly, premium feel requires restraint)
// - 'linear' — for parallax and continuous motion
// - 'sine.inOut' — subtle, elegant

const EASING = {
  SMOOTH: 'power2.out',
  BALANCED: 'power2.inOut',
  ENTRANCE: 'back.out',
  EXIT: 'power2.in',
  PARALLAX: 'linear',
} as const;
```

## Timing Guidelines

```typescript
const TIMING = {
  MICRO: 200, // milliseconds — micro-interactions
  SUBTLE: 300,
  STANDARD: 600, // most animations
  CINEMATIC: 1000, // hero entrances
} as const;
```

## Performance Optimization

1. **Use `transform` and `opacity` only**:
   ```typescript
   // Good
   gsap.to(element, { x: 100, opacity: 0.5 });

   // Bad (repaints)
   gsap.to(element, { width: 100, height: 50 });
   ```

2. **Batch animations when possible**:
   ```typescript
   // Good
   gsap.to('.item', { opacity: 1, duration: 0.6, stagger: 0.1 });

   // Bad (multiple individual tweens)
   document.querySelectorAll('.item').forEach((el) => {
     gsap.to(el, { opacity: 1, duration: 0.6 });
   });
   ```

3. **Disable animations on mobile if performance suffers**:
   ```typescript
   const isMobile = window.innerWidth < 768;
   if (!isMobile && !prefersReducedMotion) {
     // Run animation
   }
   ```

## Debugging

- Use `ScrollTrigger.enable()` / `disable()` for development.
- Enable `markers: true` on ScrollTrigger during development to visualize triggers.
- Use browser DevTools Performance tab to check for jank.

---

**Golden Rule**: Every animation should feel intentional and purposeful. Gratuitous motion is the enemy of premium design.
