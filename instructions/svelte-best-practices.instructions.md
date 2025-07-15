---
applyTo: "**/*.svelte"
---

# Svelte Best Practices and Standards

**Purpose** – Provide comprehensive guidelines for writing clean, maintainable, and efficient Svelte applications leveraging the framework's unique compilation approach.

**Core Principles:**
- **Reactive by Design**: Embrace Svelte's reactive statements and stores
- **Compile-time Optimization**: Write code that compiles to efficient vanilla JavaScript
- **Minimal Runtime**: Keep bundle sizes small with tree-shaking and dead code elimination
- **Developer Experience**: Leverage Svelte's intuitive syntax and tooling

**Component Structure:**
- Keep components small and focused on single responsibilities
- Use `<script>`, `<style>`, and markup sections in proper order
- Place component logic in `<script>` tag, styles in `<style>` tag
- Use `export let` for component props with default values when appropriate
- Implement proper prop validation for complex data types
- Use `$$props` and `$$restProps` for advanced prop handling

**Reactive Programming:**
- Use reactive statements (`$:`) for computed values and side effects
- Avoid complex expressions in reactive statements; break them into smaller pieces
- Use `$:` for cleanup operations when dependencies change
- Implement proper dependency tracking in reactive statements
- Use `beforeUpdate` and `afterUpdate` for DOM-related side effects

**State Management:**
- Use component state for local data that doesn't need to be shared
- Implement Svelte stores for shared state across components
- Use `writable` stores for mutable state, `readable` for immutable data
- Create custom stores for complex state logic with proper encapsulation
- Use `derived` stores for computed values based on other stores
- Implement proper store cleanup in component destruction

**Event Handling:**
- Use `on:` directive for DOM events with proper event handling
- Implement custom events with `createEventDispatcher()` for component communication
- Use event forwarding (`on:click`) for passing events up the component tree
- Implement proper event cleanup to prevent memory leaks
- Use event modifiers (`preventDefault`, `stopPropagation`) appropriately

**Styling Guidelines:**
- Use scoped styles (default behavior) for component-specific styling
- Implement global styles with `:global()` modifier when necessary
- Use CSS custom properties for theme-able components
- Leverage Svelte's built-in CSS preprocessor support (Sass, Less, etc.)
- Implement responsive design with mobile-first approach
- Use CSS transitions and animations for smooth user interactions

**Performance Optimization:**
- Use `{#key}` blocks to control component re-rendering
- Implement `tick()` for coordinating DOM updates
- Use `bind:` directives efficiently to avoid unnecessary re-renders
- Optimize list rendering with proper key usage in `{#each}` blocks
- Implement virtual scrolling for large lists when necessary
- Use `import()` for code splitting and lazy loading

**TypeScript Integration:**
- Use TypeScript for type safety and better developer experience
- Define proper interfaces for component props and event payloads
- Implement generic components when appropriate
- Use proper type annotations for store contents
- Configure TypeScript strict mode for better error catching

**Testing Strategies:**
- Write unit tests using Vitest or Jest with Svelte testing utilities
- Test component behavior, not implementation details
- Use `@testing-library/svelte` for user-centric testing
- Mock external dependencies and stores in tests
- Implement integration tests for complex component interactions
- Test accessibility features and keyboard navigation

**Build and Development:**
- Use Vite for fast development and optimized builds
- Configure proper build optimizations for production
- Implement proper source maps for debugging
- Use proper linting configuration with ESLint and Prettier
- Set up pre-commit hooks for code quality enforcement

**Accessibility Standards:**
- Use semantic HTML elements within Svelte components
- Implement proper ARIA attributes for complex interactions
- Ensure keyboard navigation works for all interactive elements
- Use proper heading hierarchy and landmark elements
- Implement proper focus management for dynamic content
- Test with screen readers and accessibility tools

**Security Considerations:**
- Sanitize user inputs to prevent XSS attacks
- Use `@html` directive cautiously with trusted content only
- Implement proper Content Security Policy (CSP)
- Validate and sanitize data from external sources
- Use proper authentication patterns with stores

**File Organization:**
- Organize components in logical folder structures
- Use consistent naming conventions (kebab-case recommended)
- Separate concerns: components, stores, utilities, and types
- Implement proper barrel exports for cleaner imports
- Use `src/lib` for reusable components and utilities

**When to Apply:**
1. Building new Svelte applications or components
2. Refactoring existing Svelte code for better performance
3. Code reviews and quality assessments
4. Onboarding team members to Svelte development
5. Establishing team coding standards for Svelte projects

**Output Format:**
- Follow Svelte's recommended code style and conventions
- Use consistent indentation and formatting with Prettier
- Include proper JSDoc comments for complex components
- Organize imports logically: external libraries first, then internal
- Use meaningful variable and function names that express intent clearly
