---
applyTo: "**/*.ts"
---

# Angular Best Practices and Standards

**Purpose** – Provide comprehensive guidelines for writing clean, maintainable, and efficient Angular applications following official Angular style guide principles.

**Core Principles:**
- **Single Responsibility**: Each component, service, and symbol should have one responsibility
- **LIFT Structure**: Locate code quickly, Identify at a glance, Flat structure, Try to be DRY
- **Consistent Naming**: Use descriptive names that clearly convey purpose and type
- **Modularity**: Organize code into logical modules with clear boundaries

**File Structure & Naming:**
- Use kebab-case for file names: `hero-detail.component.ts`
- Include type suffix: `.component.ts`, `.service.ts`, `.directive.ts`, `.pipe.ts`
- Limit files to 400 lines maximum for better maintainability
- Use descriptive folder names that reflect feature areas
- Place related files together in dedicated folders for complex features

**Component Guidelines:**
- Extract templates and styles to separate files when >3 lines
- Use `@Input()` and `@Output()` decorators for property bindings
- Avoid aliasing inputs/outputs unless serving important purpose
- Place public properties before private, methods after properties
- Delegate complex logic to services; keep components focused on presentation
- Use lifecycle hooks interfaces (`OnInit`, `OnDestroy`) for type safety
- Initialize input properties with default values or mark as optional
- Don't prefix output properties with "on" (use `click` not `onClick`)

**Service Guidelines:**
- Use `@Injectable({ providedIn: 'root' })` for singleton services
- Create services with single responsibility principle
- Use dependency injection for service dependencies
- Handle errors appropriately with proper error handling patterns
- Make services stateless when possible for better testability

**Module Organization:**
- Create feature modules for distinct application areas
- Use shared modules for reusable components, directives, and pipes
- Implement lazy loading for feature modules to improve performance
- Keep root module (`AppModule`) minimal and focused on bootstrapping
- Export only what other modules need from shared modules

**Performance Best Practices:**
- Use OnPush change detection strategy when possible
- Implement trackBy functions for *ngFor loops
- Avoid complex calculations in templates; use getters or pipes
- Unsubscribe from observables in ngOnDestroy to prevent memory leaks
- Use async pipe for automatic subscription management
- Precompute filtering and sorting logic in components, not pipes

**TypeScript & Code Quality:**
- Use strict TypeScript configuration for better type safety
- Implement proper error handling with try-catch blocks
- Use readonly for properties that shouldn't change
- Prefer interfaces over classes for type definitions
- Use enums for constants with multiple related values

**Testing Guidelines:**
- Write unit tests for all components and services
- Use TestBed for component testing setup
- Mock dependencies appropriately in tests
- Test user interactions and component outputs
- Maintain test coverage above 80% for critical business logic

**Accessibility Standards:**
- Use semantic HTML elements appropriately
- Implement proper ARIA attributes for complex interactions
- Ensure keyboard navigation works for all interactive elements
- Provide meaningful alt text for images
- Use proper heading hierarchy (h1, h2, h3, etc.)

**Security Considerations:**
- Sanitize user inputs to prevent XSS attacks
- Use Angular's built-in security features
- Validate data on both client and server sides
- Implement proper authentication and authorization
- Use HTTPS for all production applications

**When to Apply:**
1. Starting new Angular projects or features
2. Refactoring existing Angular applications
3. Code reviews and quality assessments
4. Onboarding new team members to Angular projects
5. Establishing team coding standards

**Output Format:**
- Follow Angular's official style guide conventions
- Use consistent indentation (2 spaces) and formatting
- Include proper JSDoc comments for public APIs
- Organize imports: Angular core first, then third-party, then local
- Use meaningful variable and function names that express intent
