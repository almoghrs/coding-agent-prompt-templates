---
applyTo: "**/*.{jsx,tsx}"
---

# React Best Practices and Standards

**Purpose** – Enforce consistent React development patterns, performance optimizations, and modern best practices across all React components and applications.

**Guidelines:**
- Follow functional components with hooks over class components
- Use TypeScript for type safety and better developer experience
- Implement proper state management with useState, useReducer, or external libraries
- Apply component composition patterns over inheritance
- Ensure proper prop validation and default values
- Use semantic HTML and accessibility best practices
- Implement proper error boundaries and error handling
- Follow consistent naming conventions and file organization
- Optimize performance with React.memo, useMemo, and useCallback when appropriate
- Use custom hooks for reusable logic
- Implement proper testing strategies with Jest and React Testing Library
- Follow ESLint and Prettier configuration for code consistency

**When to Apply:**
1. **Component Creation** – When creating new React components or refactoring existing ones
2. **State Management** – When implementing local or global state management solutions
3. **Performance Optimization** – When components show performance issues or unnecessary re-renders
4. **Code Reviews** – When reviewing React code for consistency and best practices
5. **Project Setup** – When initializing new React projects or configuring build tools
6. **Testing Implementation** – When writing unit, integration, or end-to-end tests
7. **Accessibility Improvements** – When enhancing components for better accessibility
8. **API Integration** – When connecting components to external APIs or data sources
9. **Form Handling** – When implementing form validation and submission logic
10. **Routing Implementation** – When setting up client-side routing with React Router

**Component Structure:**
```tsx
// imports (external libraries first, then internal)
import React, { useState, useEffect, memo } from 'react';
import { Button } from '@/components/ui/button';
import { useCustomHook } from '@/hooks/useCustomHook';
import { ComponentProps } from './types';
import styles from './Component.module.css';

// interfaces/types
interface Props {
  title: string;
  onAction: (data: string) => void;
  isLoading?: boolean;
}

// component implementation
const Component: React.FC<Props> = memo(({ 
  title, 
  onAction, 
  isLoading = false 
}) => {
  // hooks (useState, useEffect, custom hooks)
  const [localState, setLocalState] = useState<string>('');
  const { data, error } = useCustomHook();

  // event handlers
  const handleAction = useCallback((value: string) => {
    onAction(value);
  }, [onAction]);

  // effects
  useEffect(() => {
    // side effects
  }, []);

  // early returns
  if (error) return <ErrorComponent error={error} />;
  if (isLoading) return <LoadingSpinner />;

  // main render
  return (
    <div className={styles.container}>
      <h1>{title}</h1>
      <Button onClick={() => handleAction(localState)}>
        Submit
      </Button>
    </div>
  );
});

Component.displayName = 'Component';

export default Component;
```

**State Management Patterns:**
- Use `useState` for simple local state
- Use `useReducer` for complex state logic
- Use `useContext` for component tree-wide state
- Consider Redux Toolkit or Zustand for global state management
- Implement proper state normalization for complex data structures

**Performance Best Practices:**
- Wrap components with `React.memo` only when necessary
- Use `useMemo` for expensive calculations
- Use `useCallback` for event handlers passed to child components
- Implement code splitting with `React.lazy` and `Suspense`
- Optimize bundle size with tree shaking and dynamic imports

**Accessibility Standards:**
- Use semantic HTML elements
- Implement proper ARIA attributes
- Ensure keyboard navigation support
- Provide meaningful alt text for images
- Maintain proper color contrast ratios
- Use focus management for dynamic content

**Testing Requirements:**
- Write unit tests for component logic
- Test user interactions and state changes
- Mock external dependencies and API calls
- Test accessibility features
- Implement integration tests for complex workflows
- Maintain test coverage above 80%

**Error Handling:**
- Implement error boundaries for component trees
- Use try-catch blocks for async operations
- Provide user-friendly error messages
- Log errors to monitoring services
- Implement fallback UI for error states

**File Organization:**
```
src/
├── components/
│   ├── ui/              # Reusable UI components
│   ├── forms/           # Form components
│   └── layout/          # Layout components
├── hooks/               # Custom hooks
├── contexts/            # React contexts
├── utils/               # Utility functions
├── types/               # TypeScript type definitions
├── services/            # API services
└── __tests__/           # Test files
```

**Output Format:**
- Components should be self-contained and reusable
- Follow TypeScript strict mode requirements
- Include proper JSDoc comments for complex logic
- Export components with proper display names
- Implement proper prop validation and defaults
- Use consistent naming conventions (PascalCase for components, camelCase for functions)
