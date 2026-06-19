# Code Quality Standards for Cristian's Portfolio

## TypeScript & Linting

- **Strict Mode**: `strict: true` in `tsconfig.json` — mandatory.
- **No `any`**: Use proper types. If unsure, use generics or `unknown` with proper narrowing.
- **Naming Conventions**:
  - Components: PascalCase (`Hero.tsx`, `ProjectCard.tsx`)
  - Utilities/Hooks: camelCase (`useGsapAnimation.ts`, `animationUtils.ts`)
  - Constants: UPPER_SNAKE_CASE (`ANIMATION_DURATION`, `COLORS`)
  - Files: kebab-case for utilities, PascalCase for components

## Code Style

- **Prettier Config**:
  ```json
  {
    "semi": true,
    "singleQuote": true,
    "trailingComma": "es5",
    "tabWidth": 2,
    "useTabs": false,
    "printWidth": 100
  }
  ```

- **ESLint**: Use `next/recommended` + `plugin:react-hooks/recommended` + custom rules for GSAP best practices.

- **Imports**: Always organize alphabetically and by type:
  ```typescript
  // Built-ins
  import { useEffect } from 'react';

  // Next.js
  import { useRouter } from 'next/navigation';

  // Third-party
  import { gsap } from 'gsap';
  import { Lucide } from 'lucide-react';

  // Internal
  import { Button } from '@/components/ui/Button';
  import { useGsapAnimation } from '@/hooks/useGsapAnimation';
  ```

## Comments & Documentation

- **JSDoc for functions**: Document parameters, returns, and example usage for complex functions.
- **Complex logic**: Add inline comments explaining why, not what.
- **Component props**: Use TypeScript interfaces with JSDoc:
  ```typescript
  /**
   * Hero section component with parallax background.
   * @param title - Main heading text
   * @param subtitle - Secondary text
   * @param animate - Whether to enable GSAP animations
   */
  export interface HeroProps {
    title: string;
    subtitle: string;
    animate?: boolean;
  }
  ```

## Error Handling

- Always handle errors explicitly. No silent failures.
- Use try-catch for async operations; provide meaningful error messages.
- Catch missing DOM elements in GSAP animations gracefully.

## Performance Guardrails

- No unnecessary re-renders: use `React.memo` for expensive components.
- No inline functions in JSX (use `useCallback` if needed).
- No synchronous large operations on the main thread.
- GSAP: Always cleanup animations in `useEffect` cleanup to prevent memory leaks.

---

**Reference**: Review the `.cursor/rules/gsap-patterns.md` for animation-specific code quality.
