# Accessibility Standards (WCAG 2.1 AA+)

## Motion & Animation

### `prefers-reduced-motion`
All animations must respect user preferences:

```typescript
// src/hooks/useMotionPreference.ts
export const useMotionPreference = (): boolean => {
  const [prefersReducedMotion, setPrefersReducedMotion] = React.useState(false);

  React.useEffect(() => {
    const mediaQuery = window.matchMedia('(prefers-reduced-motion: reduce)');
    setPrefersReducedMotion(mediaQuery.matches);

    const handleChange = (e: MediaQueryListEvent) => {
      setPrefersReducedMotion(e.matches);
    };

    mediaQuery.addEventListener('change', handleChange);
    return () => mediaQuery.removeEventListener('change', handleChange);
  }, []);

  return prefersReducedMotion;
};
```

Usage in components:
```typescript
const prefersReducedMotion = useMotionPreference();

useGsapAnimation(() => {
  if (prefersReducedMotion) return gsap.timeline();
  // Animation code here
}, [prefersReducedMotion]);
```

## Keyboard Navigation

### Focus Management
- **Visible focus indicators**: Never remove `outline` without providing alternative.
- **Tab order**: Follow DOM order or use `tabIndex` strategically.
- **Focus trap in modals**: Trap focus within modal, return on close.

Example:
```typescript
export const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  (props, ref) => (
    <button
      ref={ref}
      className="focus:outline-none focus:ring-2 focus:ring-terracotta focus:ring-offset-2"
      {...props}
    />
  )
);
```

### Keyboard Event Handling
```typescript
const handleKeyDown = (e: React.KeyboardEvent) => {
  if (e.key === 'Escape') {
    // Close modal or overlay
  }
  if (e.key === 'Enter' || e.key === ' ') {
    // Trigger action
  }
};
```

## Color Contrast

**Minimum ratios (WCAG AA)**:
- Normal text: 4.5:1
- Large text (18pt+): 3:1
- UI components: 3:1

**Portfolio Colors**:
- Cream (#F5F3F0) on Navy (#0A0C10): ~15:1 ✓ (Excellent)
- Terracotta (#C75B39) on Navy: ~7:1 ✓ (Good)
- Gold (#D4A373) on Navy: ~6:1 ✓ (Good)

Test with: https://webaim.org/resources/contrastchecker/

## Semantic HTML

```typescript
// Good
<header>Navigation</header>
<main>
  <section aria-labelledby="about-title">
    <h1 id="about-title">About</h1>
  </section>
</main>
<footer>Footer</footer>

// Bad
<div>Navigation</div>
<div>
  <div>
    <div>About</div>
  </div>
</div>
```

## Images & Media

### Alt Text
```typescript
// Good
<img src="hero.jpg" alt="Cristian at his desk in Barcelona" />

// Bad
<img src="hero.jpg" alt="photo" />
<img src="hero.jpg" /> {/* Missing alt */}
```

### Decorative Images
```typescript
// Decorative images should have empty alt
<img src="decoration.svg" alt="" aria-hidden="true" />
```

## Forms

### Labels
```typescript
// Good
<label htmlFor="email">Email</label>
<input id="email" type="email" />

// Bad
<input placeholder="Email" /> {/* Placeholder != label */}
```

### Error Messages
```typescript
<input aria-invalid={!!error} aria-describedby={error ? 'error-msg' : undefined} />
{error && <p id="error-msg" role="alert">{error}</p>}
```

## Screen Reader Support

### ARIA Attributes
```typescript
// Navigation
<nav aria-label="Main navigation">
  <ul role="menubar">
    <li role="none"><a href="/">Home</a></li>
  </ul>
</nav>

// Buttons with icons only
<button aria-label="Close menu">
  <X size={24} />
</button>

// Loading states
<button disabled aria-busy={isLoading}>
  {isLoading ? 'Loading...' : 'Submit'}
</button>
```

### Skip Links
```typescript
<a href="#main-content" className="sr-only focus:not-sr-only">
  Skip to main content
</a>
<main id="main-content">...</main>
```

## Text & Readability

- **Line height**: 1.5+ for body text
- **Font size**: Minimum 16px for body text
- **Line length**: 45–75 characters (optimal)
- **Avoid justified text**: Use left-aligned for better readability

## Interactive Elements

### Touch Targets
- Minimum 44×44px (48×48px recommended)
- Adequate spacing between targets (8px minimum)

### Button States
```typescript
<button
  className={`
    px-4 py-2
    disabled:opacity-50 disabled:cursor-not-allowed
    focus:outline-none focus:ring-2 focus:ring-offset-2
    active:scale-95 transition-transform
  `}
/>
```

## Video & Audio

- Captions for video
- Transcripts for audio
- Autoplay disabled

## Testing

- Use axe DevTools or WAVE to audit
- Test keyboard navigation manually
- Test with screen readers (NVDA, JAWS)
- Verify color contrast with tools
- Resize text 200% and verify readability
- Test with `prefers-reduced-motion: reduce` enabled

---

**Target**: WCAG 2.1 AA+ compliance. Aim higher where possible.
