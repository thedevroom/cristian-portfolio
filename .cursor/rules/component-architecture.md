# Component Architecture Standards

## Principles

1. **Single Responsibility**: Each component does one thing well.
2. **Composition Over Inheritance**: Build complex UIs from simple, reusable pieces.
3. **Props Interface**: Clear, typed props. Use TypeScript interfaces for all components.
4. **Accessibility First**: Every component accessible out-of-the-box.
5. **Responsive by Default**: Mobile-first design in all components.

## Component Structure

### UI Components (`src/components/ui/`)
**Purpose**: Atomic, reusable building blocks.

**Example: Button Component**
```typescript
import { forwardRef, ReactNode, ButtonHTMLAttributes } from 'react';

interface ButtonProps extends ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: 'primary' | 'secondary' | 'ghost';
  size?: 'sm' | 'md' | 'lg';
  children: ReactNode;
  isLoading?: boolean;
  disabled?: boolean;
}

export const Button = forwardRef<HTMLButtonElement, ButtonProps>(
  (
    { variant = 'primary', size = 'md', children, isLoading, disabled, ...props },
    ref
  ) => {
    const baseStyles = 'font-medium transition-all duration-300 focus:outline-none focus:ring-2 focus:ring-offset-2';
    const variants = {
      primary: 'bg-terracotta hover:bg-terracotta-dark text-cream',
      secondary: 'bg-gray-700 hover:bg-gray-600 text-cream',
      ghost: 'bg-transparent hover:bg-gray-800 text-cream border border-gray-600',
    };
    const sizes = {
      sm: 'px-3 py-2 text-sm',
      md: 'px-4 py-2 text-base',
      lg: 'px-6 py-3 text-lg',
    };

    return (
      <button
        ref={ref}
        className={`${baseStyles} ${variants[variant]} ${sizes[size]}`}
        disabled={isLoading || disabled}
        {...props}
      >
        {isLoading ? 'Loading...' : children}
      </button>
    );
  }
);

Button.displayName = 'Button';
```

### Section Components (`src/components/sections/`)
**Purpose**: Full-screen or large layout blocks. Each section manages its own GSAP animations.

**Structure**:
- Use `useEffect` with `useRef` for GSAP setup
- Cleanup animations in return function
- Pass animation configuration as props if needed
- Respect `prefers-reduced-motion`

**Example: Hero Section**
```typescript
'use client';

import { useEffect, useRef } from 'react';
import gsap from 'gsap';
import { Button } from '@/components/ui/Button';
import { useMotionPreference } from '@/hooks/useMotionPreference';

export const Hero = () => {
  const containerRef = useRef<HTMLDivElement>(null);
  const prefersReducedMotion = useMotionPreference();

  useEffect(() => {
    if (!containerRef.current || prefersReducedMotion) return;

    const timeline = gsap.timeline();
    timeline
      .from('.hero-title', { opacity: 0, y: 30, duration: 0.8 }, 0)
      .from('.hero-subtitle', { opacity: 0, y: 20, duration: 0.6 }, 0.2)
      .from('.hero-ctas button', { opacity: 0, scale: 0.9, duration: 0.5, stagger: 0.1 }, 0.4);

    return () => timeline.kill();
  }, [prefersReducedMotion]);

  return (
    <section ref={containerRef} className="min-h-screen flex items-center justify-center">
      <div className="hero-title text-5xl font-bold">Cristian Querol Alves</div>
      <p className="hero-subtitle text-xl text-gray-400">Fullstack Developer · Barcelona</p>
      <div className="hero-ctas flex gap-4">
        <Button variant="primary">Explore Work</Button>
        <Button variant="secondary">Let's Talk</Button>
      </div>
    </section>
  );
};
```

### Layout Components (`src/components/layout/`)
**Purpose**: Persistent UI elements (Header, Footer, Navigation).

- Keep minimal logic
- Pass props for content variation
- Ensure sticky/fixed positioning works with animations

## Props Best Practices

1. **Keep props minimal**: Pass only what's necessary.
2. **Use discriminated unions** for complex variant logic:
   ```typescript
   type ButtonProps = 
     | { variant: 'primary'; onClick: () => void }
     | { variant: 'secondary'; href: string };
   ```
3. **Provide sensible defaults**: Most props should have defaults.
4. **Avoid prop drilling**: Use Context for deeply nested props if needed.

## Component Composition Example

```typescript
// Page combining sections
import { Hero } from '@/components/sections/Hero';
import { About } from '@/components/sections/About';
import { SelectedWork } from '@/components/sections/SelectedWork';

export default function Home() {
  return (
    <main>
      <Hero />
      <About />
      <SelectedWork />
    </main>
  );
}
```

## Animations & Component State

- **Global animation state**: Use Zustand or Context if multiple sections need to coordinate.
- **Local animation state**: Use `useRef` + `useEffect` for component-scoped animations.
- **Cleanup is mandatory**: Always kill GSAP animations in `useEffect` cleanup.

---

**Convention**: All components export both named and default (where applicable) to support various import styles.
