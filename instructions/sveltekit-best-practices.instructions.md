---
applyTo: "**/*.svelte"
---

# SvelteKit Best Practices and Standards

**Purpose** – Provide comprehensive guidelines for building robust, performant, and maintainable full-stack web applications using SvelteKit.

**Core Architecture:**
- **File-based Routing**: Leverage SvelteKit's intuitive file-system routing
- **Universal Rendering**: Optimize for SSR, CSR, and static generation as needed
- **Type Safety**: Use TypeScript throughout the entire application stack
- **Performance First**: Implement optimal loading strategies and code splitting

**Routing and Navigation:**
- Use file-based routing with proper folder structure in `src/routes/`
- Implement dynamic routes with `[slug]` syntax for parametric URLs
- Use `(groups)` for layout organization without affecting URL structure
- Implement proper error handling with `+error.svelte` pages
- Use `goto()` function for programmatic navigation
- Implement proper client-side routing with `data-sveltekit-preload-data`

**Data Loading Patterns:**
- Use `+page.server.ts` for server-side data loading and form actions
- Implement `+page.ts` for universal data loading (runs on server and client)
- Use `+layout.server.ts` for shared server-side data across routes
- Implement proper loading states and error handling in load functions
- Use `depends()` for manual cache invalidation when needed
- Implement streaming with `Promise.all()` for parallel data fetching

**State Management:**
- Use SvelteKit's built-in stores (`$page`, `$navigating`, `$updated`)
- Implement custom stores for application-wide state management
- Use `$page.data` for accessing loaded data in components
- Implement proper state persistence with browser storage when needed
- Use context API for deeply nested component communication
- Implement proper reactive patterns with Svelte stores

**Form Handling:**
- Use progressive enhancement with `+page.server.ts` actions
- Implement proper form validation on both client and server
- Use `enhance` action for better form UX with JavaScript enabled
- Implement proper error handling and success feedback
- Use `$page.form` for accessing form data and validation errors
- Implement file upload handling with proper validation

**API Routes and Endpoints:**
- Create API routes using `+server.ts` files in route directories
- Implement proper HTTP methods (GET, POST, PUT, DELETE, PATCH)
- Use proper status codes and error handling in API responses
- Implement request validation and sanitization
- Use proper authentication and authorization patterns
- Implement rate limiting and security headers

**Performance Optimization:**
- Use preloading strategically with `data-sveltekit-preload-data`
- Implement proper code splitting with dynamic imports
- Use `+page.server.ts` for server-side rendering when appropriate
- Implement proper caching strategies for static and dynamic content
- Use image optimization with responsive images and lazy loading
- Implement proper bundle analysis and optimization

**Build and Deployment:**
- Configure proper adapter for deployment target (Node, static, etc.)
- Use environment variables properly with `$env/static` and `$env/dynamic`
- Implement proper build optimization and minification
- Use proper source maps configuration for debugging
- Configure proper CSP headers for security
- Implement proper asset optimization and compression

**Testing Strategies:**
- Write unit tests for utility functions and business logic
- Use Playwright for end-to-end testing of user flows
- Test form actions and API endpoints with proper mocking
- Implement integration tests for complex page interactions
- Test accessibility features and keyboard navigation
- Use proper test data setup and teardown

**TypeScript Integration:**
- Use TypeScript for all `.ts` and `.svelte` files
- Define proper types for `PageData`, `ActionData`, and `LayoutData`
- Implement generic types for reusable components and functions
- Use proper type guards for runtime type checking
- Configure strict TypeScript settings for better error catching
- Use proper type inference with SvelteKit's generated types

**Security Best Practices:**
- Implement proper CSRF protection for form actions
- Use proper input validation and sanitization
- Implement proper authentication and session management
- Use secure headers and Content Security Policy
- Implement proper rate limiting and request validation
- Use environment variables for sensitive configuration

**Accessibility Standards:**
- Use semantic HTML elements in all components
- Implement proper ARIA attributes for complex interactions
- Ensure keyboard navigation works throughout the application
- Use proper heading hierarchy and landmark elements
- Implement proper focus management for SPAs
- Test with screen readers and accessibility tools

**File Organization:**
- Structure routes logically with proper nesting
- Use `src/lib` for reusable components and utilities
- Organize components by feature or domain
- Use proper naming conventions for files and folders
- Implement proper barrel exports for cleaner imports
- Separate concerns: components, stores, utilities, and types

**Development Workflow:**
- Use SvelteKit's development server for fast iteration
- Implement proper linting with ESLint and Prettier
- Use pre-commit hooks for code quality enforcement
- Implement proper debugging with browser dev tools
- Use proper logging for development and production
- Implement proper error monitoring and reporting

**When to Apply:**
1. Building new SvelteKit applications or features
2. Migrating from other frameworks to SvelteKit
3. Refactoring existing SvelteKit code for better performance
4. Code reviews and architecture decisions
5. Onboarding team members to SvelteKit development
6. Establishing team coding standards for SvelteKit projects

**Output Format:**
- Follow SvelteKit's recommended project structure and conventions
- Use consistent indentation and formatting with Prettier
- Include proper TypeScript types and JSDoc comments
- Organize imports: SvelteKit modules first, then external, then internal
- Use meaningful variable and function names that express intent clearly
- Implement proper error handling and user feedback patterns
