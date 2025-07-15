---
applyTo: "**/*.vue"
---

# Nuxt.js Best Practices and Standards

**Purpose** – Provide comprehensive guidelines for building robust, performant, and maintainable full-stack Vue.js applications using Nuxt.js framework.

**Core Architecture:**
- **Auto-routing**: Leverage Nuxt's file-based routing system
- **Universal Rendering**: Optimize for SSR, SPA, and static generation
- **Module Ecosystem**: Use official and community modules for common functionality
- **Developer Experience**: Utilize Nuxt's conventions and tooling for rapid development

**Project Structure:**
- Use conventional directory structure (`pages/`, `components/`, `layouts/`, `middleware/`)
- Organize components by feature or domain in `components/` directory
- Use `layouts/` for shared page structures and navigation
- Implement proper middleware for authentication and route guards
- Use `plugins/` for Vue.js plugins and third-party integrations
- Store static assets in `static/` and processed assets in `assets/`

**Page and Route Management:**
- Use file-based routing with proper folder structure in `pages/`
- Implement dynamic routes with `_slug.vue` syntax
- Use nested routes with proper folder organization
- Implement proper error handling with `error.vue` pages
- Use `validate()` method for route parameter validation
- Implement proper meta tags and SEO optimization with `head()` method

**Data Fetching Patterns:**
- Use `asyncData()` for server-side data fetching before component creation
- Implement `fetch()` method for client-side data fetching and store population
- Use `$nuxt.context` for accessing request context in universal mode
- Implement proper loading states and error handling in data fetching
- Use `watchQuery` property for reactive query parameter handling
- Implement proper caching strategies for API calls

**State Management:**
- Use Vuex store for complex application state management
- Implement proper store structure with modules and namespacing
- Use store actions for asynchronous operations and API calls
- Implement proper state normalization for complex data structures
- Use `nuxtServerInit` for server-side store initialization
- Consider Pinia as modern alternative to Vuex for newer projects

**Component Development:**
- Use Vue.js Single File Components (SFCs) with proper structure
- Implement proper prop validation and default values
- Use scoped styles for component-specific styling
- Implement proper event handling and emission patterns
- Use Vue.js composition API for complex component logic
- Implement proper lifecycle hooks for component behavior

**Performance Optimization:**
- Use lazy loading for routes and components with dynamic imports
- Implement proper code splitting with webpack's dynamic imports
- Use `<nuxt-link>` for client-side navigation with prefetching
- Implement proper image optimization with `@nuxt/image` module
- Use proper caching strategies for static and dynamic content
- Implement proper bundle analysis and optimization

**Build and Deployment:**
- Configure proper build target (static, server, spa) based on requirements
- Use environment variables properly with `@nuxtjs/dotenv` or native support
- Implement proper build optimization and minification
- Use proper source maps configuration for debugging
- Configure proper CSP headers and security settings
- Implement proper asset optimization and compression

**Module Integration:**
- Use official Nuxt modules for common functionality (`@nuxtjs/axios`, `@nuxtjs/auth`)
- Implement proper module configuration in `nuxt.config.js`
- Use `@nuxtjs/pwa` for Progressive Web App features
- Implement proper SEO optimization with `@nuxtjs/sitemap`
- Use styling modules like `@nuxtjs/tailwindcss` or `@nuxtjs/bulma`
- Implement proper analytics and tracking with appropriate modules

**TypeScript Integration:**
- Use TypeScript for type safety with `@nuxt/typescript-build`
- Define proper types for Vuex store state and actions
- Implement generic types for reusable components and composables
- Use proper type annotations for asyncData and fetch methods
- Configure strict TypeScript settings for better error catching
- Use proper type inference with Nuxt's generated types

**Testing Strategies:**
- Write unit tests for components using Vue Test Utils
- Use Jest for testing utilities and business logic
- Implement integration tests for complex page interactions
- Test Vuex store actions and mutations thoroughly
- Use Cypress or Playwright for end-to-end testing
- Test accessibility features and keyboard navigation

**Security Best Practices:**
- Implement proper CSRF protection for form submissions
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

**SEO and Meta Management:**
- Use `head()` method or `@nuxtjs/meta` for dynamic meta tags
- Implement proper structured data with JSON-LD
- Use proper canonical URLs and hreflang attributes
- Implement proper Open Graph and Twitter Card meta tags
- Use proper sitemap generation with `@nuxtjs/sitemap`
- Implement proper robots.txt configuration

**Error Handling:**
- Implement proper error pages with custom `error.vue` layout
- Use try-catch blocks in asyncData and fetch methods
- Implement proper error reporting and monitoring
- Use proper HTTP status codes for error responses
- Implement proper user feedback for errors
- Use proper logging for debugging and monitoring

**Development Workflow:**
- Use Nuxt's development server for fast iteration
- Implement proper linting with ESLint and Prettier
- Use pre-commit hooks for code quality enforcement
- Implement proper debugging with Vue.js devtools
- Use proper logging for development and production
- Implement proper hot reloading and live editing

**When to Apply:**
1. Building new Nuxt.js applications or features
2. Migrating from Vue.js SPA to universal applications
3. Refactoring existing Nuxt.js code for better performance
4. Code reviews and architecture decisions
5. Onboarding team members to Nuxt.js development
6. Establishing team coding standards for Nuxt.js projects

**Output Format:**
- Follow Nuxt.js recommended project structure and conventions
- Use consistent indentation and formatting with Prettier
- Include proper TypeScript types and JSDoc comments where applicable
- Organize imports: Nuxt modules first, then Vue, then external, then internal
- Use meaningful variable and function names that express intent clearly
- Implement proper error handling and user feedback patterns
