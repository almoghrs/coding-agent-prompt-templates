---
applyTo: "**"
---

# MEMORY_SYSTEM.instructions.md

**Purpose** – Create and maintain a memory file (`MEMORY.md`) that captures the project's context, state, and important decisions to provide continuity across sessions.

**Reading the Memory File**

- **ALWAYS Check First**: Before starting work on any project, YOU MUST check if `MEMORY.md` exists in the project root (and if not, create one)
- **Read for Context**: If the memory file exists, read it to understand the project's current state, architecture, and recent context
- **Use as Reference**: The memory file contains essential information about the project structure, key decisions, and current focus areas
- **Link in Responses**: When providing project-related guidance, reference relevant sections from the memory file to maintain consistency with established patterns and decisions


**When to Update Memory**

1. **Project Setup** – Initial project creation, framework selection, or major architecture decisions
2. **Feature Development** – New features added, core functionality implemented, or significant components created
3. **Data/Schema Changes** – Database schema modifications, API changes, data structure updates, or file format changes
4. **Configuration Changes** – Environment setup, build configuration, or tool configurations
5. **Bug Fixes** – Important bugs resolved that might affect future development
6. **Code Refactoring** – Major code reorganization, architectural improvements, or pattern changes
7. **External Integrations** – New APIs, services, libraries, or third-party tool integrations
8. **User Feedback** – Important user requirements, design decisions, or feature requests
9. **Performance Optimizations** – Significant performance improvements or bottleneck resolutions
10. **Security Updates** – Security-related changes or vulnerability fixes

**Memory File Structure**

The `MEMORY.md` file should contain:

```markdown
# Project Memory

## Project Overview
- **Name**: [Project Name]
- **Type**: [Web App, API, CLI Tool, Library, Desktop App, Script, etc.]
- **Main Technologies**: [List key technologies]
- **Current Status**: [Development stage]

## Recent Context
- **Last Updated**: [Date]
- **Current Focus**: [What's being worked on now]
- **Next Steps**: [Immediate next actions]

## Technical Stack
- **Main Technologies**: [Core technologies, frameworks, libraries]
- **Language(s)**: [Programming languages used]
- **Tools & Dependencies**: [Build tools, testing frameworks, key dependencies]
- **Infrastructure**: [Database, cloud services, deployment platforms - if applicable]

## Key Decisions
- **Architecture**: [Important architectural choices]
- **Design Patterns**: [Key patterns used]
- **Conventions**: [Coding standards, naming conventions]

## Current Features
- [List implemented features]
- [Feature status: completed/in-progress/planned]

## Known Issues
- [Current bugs or limitations]
- [Workarounds in place]

## Important Files
- [Key files and their purposes]
- [Configuration files and their significance]

## Environment & Setup
- [Development environment requirements]
- [Setup instructions or gotchas]

## Notes for Future Development
- [Important considerations for future work]
- [Areas that need attention]
```

**Procedure**

1. **Check for Existing Memory**: Before creating, check if `MEMORY.md` exists in the project root
2. **Create if Missing**: If no memory file exists, create one with the basic structure
3. **Update on Significant Changes**: After implementing any of the trigger events above, update the relevant sections
4. **Keep Recent Context Fresh**: Always update the "Recent Context" section with current work
5. **Maintain Brevity**: Keep entries concise but informative - focus on decisions and context that would be valuable later
6. **Archive Old Context**: If the memory file becomes too long, archive older context to keep it manageable

**Update Guidelines**

- Always update the "Last Updated" timestamp
- Update "Current Focus" to reflect what's actively being worked on
- Add new features to the "Current Features" section
- Document any important decisions in "Key Decisions"
- Update "Next Steps" to guide future sessions
- Add any new important files to the "Important Files" section
- Only update when changes are significant enough to affect future development context

**Example Update Triggers**

- ✅ Added user authentication system
- ✅ Integrated payment processing (web app example)
- ✅ Refactored database schema (backend example)
- ✅ Fixed critical performance issue
- ✅ Added new CLI commands (CLI tool example)
- ✅ Implemented new algorithm (any project type)
- ❌ Fixed typo in comment
- ❌ Updated single variable name
- ❌ Minor styling adjustment
