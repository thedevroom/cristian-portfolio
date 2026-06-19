# Design System & Tailwind Configuration

## Color System

### Semantic Colors

```typescript
// tailwind.config.ts
export const colors = {
  // Backgrounds
  navy: '#0A0C10',
  'navy-light': '#0F1117',
  'navy-lighter': '#1A1E26',

  // Text
  cream: '#F5F3F0',
  'cream-muted': '#A8A4A0',

  // Accents (Barcelona-inspired)
  terracotta: '#C75B39',
  'terracotta-dark': '#B84D2F',
  gold: '#D4A373',
  'coral-light': '#E8A084',

  // Utility
  success: '#10B981',
  warning: '#F59E0B',
  error: '#EF4444',
  info: '#3B82F6',
};
```

### Usage
```typescript
// Component
<div className="bg-navy text-cream border-2 border-terracotta">
  Content
</div>

// Hover state
<button className="bg-terracotta hover:bg-terracotta-dark">
  Click me
</button>
```

## Typography

### Font Stack

```typescript
// next.config.ts
import { Space_Grotesk, Inter } from 'next/font/google';

const spaceGrotesk = Space_Grotesk({
  subsets: ['latin'],
  weight: ['400', '500', '600', '700'],
  variable: '--font-space-grotesk',
});

const inter = Inter({
  subsets: ['latin'],
  weight: ['400', '500', '600', '700'],
  variable: '--font-inter',
});
```

### Tailwind Typography Scale

```typescript
// tailwind.config.ts
extend: {
  fontSize: {
    // Hero
    'hero': ['5rem', { lineHeight: '1.2', fontFamily: 'var(--font-space-grotesk)' }],
    'hero-mobile': ['2.5rem', { lineHeight: '1.2', fontFamily: 'var(--font-space-grotesk)' }],

    // Section titles
    'section': ['3rem', { lineHeight: '1.2', fontFamily: 'var(--font-space-grotesk)' }],
    'section-mobile': ['1.5rem', { lineHeight: '1.2', fontFamily: 'var(--font-space-grotesk)' }],

    // Subsection titles
    'subsection': ['1.5rem', { lineHeight: '1.3', fontFamily: 'var(--font-space-grotesk)' }],

    // Body
    'body': ['1rem', { lineHeight: '1.6', fontFamily: 'var(--font-inter)' }],
    'body-sm': ['0.875rem', { lineHeight: '1.5', fontFamily: 'var(--font-inter)' }],

    // Metadata / Tags
    'meta': ['0.75rem', { lineHeight: '1.4', fontFamily: 'var(--font-inter)' }],
  },
}
```

### Usage
```typescript
<h1 className="text-hero md:text-hero-mobile font-space-grotesk font-bold">
  Cristian Querol Alves
</h1>
<p className="text-body font-inter">Body text with optimal line height.</p>
```

## Spacing System

### Predefined Scales

```typescript
// tailwind.config.ts
extend: {
  spacing: {
    'xs': '0.5rem',      // 4px
    'sm': '1rem',        // 8px
    'md': '1.5rem',      // 12px
    'lg': '2rem',        // 16px
    'xl': '3rem',        // 24px
    '2xl': '4rem',       // 32px
    '3xl': '6rem',       // 48px
    '4xl': '8rem',       // 64px
    '5xl': '12rem',      // 96px
  },
}
```

### Section Spacing

```typescript
// Component sections
<section className="py-4xl md:py-5xl px-lg md:px-2xl">
  <div className="max-w-6xl mx-auto">Content</div>
</section>
```

## Shadow System

```typescript
// tailwind.config.ts
extend: {
  boxShadow: {
    'card-sm': '0 2px 8px rgba(0,0,0,0.15)',
    'card': '0 8px 24px rgba(0,0,0,0.25)',
    'card-lg': '0 16px 48px rgba(0,0,0,0.35)',
    'card-xl': '0 24px 64px rgba(0,0,0,0.40)',
    'glow': '0 0 20px rgba(199,91,57,0.3)',
  },
}
```

## Border Radius

```typescript
// tailwind.config.ts
extend: {
  borderRadius: {
    'sm': '0.25rem',   // Minimal
    'md': '0.5rem',    // Standard
    'lg': '1rem',      // Cards
    'xl': '1.5rem',    // Large elements
    'full': '9999px',  // Circles/pills
  },
}
```

## Animation & Duration

```typescript
// tailwind.config.ts
extend: {
  duration: {
    'micro': '200ms',
    'subtle': '300ms',
    'standard': '600ms',
    'cinematic': '1000ms',
  },
  transitionTimingFunction: {
    'smooth': 'cubic-bezier(0.4, 0, 0.2, 1)',
    'emphasis': 'cubic-bezier(0.34, 1.56, 0.64, 1)',
  },
}
```

## Responsive Breakpoints

```typescript
// Default Tailwind breakpoints
sm: '640px',   // Mobile landscape
md: '768px',   // Tablet
lg: '1024px',  // Desktop
xl: '1280px',  // Large desktop
2xl: '1536px', // Extra large
```

### Mobile-First Approach

```typescript
// Always start with mobile styles, then use md: / lg: prefixes

// Mobile (320px – 767px)
<div className="text-hero-mobile">Title</div>

// Tablet and up (768px+)
<div className="md:text-hero">Title</div>

// Desktop and up (1024px+)
<div className="lg:max-w-6xl">Content</div>
```

## Utility Classes for Common Patterns

```css
/* globals.css */

/* Flex center */
.flex-center {
  @apply flex items-center justify-center;
}

/* Smooth transitions */
.transition-smooth {
  @apply transition-all duration-300 ease-smooth;
}

/* Text truncation */
.truncate-line {
  @apply truncate;
}

.truncate-2 {
  @apply line-clamp-2;
}

/* Glass morphism */
.glass {
  @apply bg-white/5 backdrop-blur-md border border-white/10;
}

/* Screen reader only */
.sr-only {
  @apply sr-only;
}

.focus\:not-sr-only:focus {
  @apply not-sr-only;
}
```

## Dark Mode (Default)

```typescript
// tailwind.config.ts
module.exports = {
  darkMode: 'class', // Explicit dark mode
  theme: {
    extend: {
      // All colors already defined above for dark theme
    },
  },
};
```

## Accessibility in Tailwind

```typescript
// Focus states
<button className="focus:outline-none focus:ring-2 focus:ring-terracotta focus:ring-offset-2 focus:ring-offset-navy">
  Accessible Button
</button>

// Reduced motion
<div className="motion-safe:animate-fade motion-reduce:opacity-100">
  Motion-aware content
</div>

// High contrast
<div className="contrast-more:border-2">
  High contrast border
</div>
```

## Configuration File Reference

```typescript
// tailwind.config.ts
import type { Config } from 'tailwindcss';

const config: Config = {
  content: [
    './src/pages/**/*.{js,ts,jsx,tsx,mdx}',
    './src/components/**/*.{js,ts,jsx,tsx,mdx}',
    './src/app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: {
        navy: '#0A0C10',
        'navy-light': '#0F1117',
        cream: '#F5F3F0',
        terracotta: '#C75B39',
        gold: '#D4A373',
      },
      fontFamily: {
        'space-grotesk': 'var(--font-space-grotesk)',
        'inter': 'var(--font-inter)',
      },
      spacing: {
        'xs': '0.5rem',
        'sm': '1rem',
        'md': '1.5rem',
        'lg': '2rem',
        'xl': '3rem',
        '2xl': '4rem',
        '3xl': '6rem',
        '4xl': '8rem',
      },
    },
  },
  plugins: [],
};

export default config;
```

---

**Principle**: Every design decision in Tailwind should reflect the premium, intentional aesthetic. No shortcuts.
