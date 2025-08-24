# AI-Assisted Mobile Development Template

Opinionated prompt architecture for Flutter/Dart mobile applications, enabling small, fully testable iterations with strict separation between PROCESS (workflow) and SOLUTION (mobile technology stack).

## Mobile Stack Focus

This template is specifically designed for **Flutter mobile applications** with:
- Flutter/Dart framework
- Comprehensive testing strategies
- Mobile-specific CI/CD pipelines
- Platform deployment (iOS/Android)

## Structure

```
prompts/
  workflow/         # Unified 8-step workflow (consolidated)
  actions/          # Entry orchestration prompts (create/update feature, start project)
  stacks/           # Mobile/Flutter specific stack descriptors
docs/               # Global docs (changelog, architecture, backlog)
.github/workflows/  # Mobile CI/CD pipeline
```

## Core Principles
- One question at a time
- Each iteration = deployable slice (requirements → deploy cycle complete)
- Automated + manual test coverage every slice
- Workflow agnostic of stack; mobile stack injects Flutter structure & tooling
- Traceability: acceptance tests ↔ tasks ↔ code stubs ↔ commits

## Usage Flow
1. Run `start-project` action prompt → loads Flutter mobile stack.
2. Use `create-feature` (or `update-feature`).
3. Step through 01–08 prompts; each iteration loops until value delivered.

## Mobile-Specific Features
- Flutter widget testing and integration tests
- Platform-specific deployment strategies
- Mobile performance optimization
- Device compatibility testing
- App store deployment workflows

## Versioning & Commits
- Conventional Commits + iteration marker `[iNN]`
- Tag: `vMAJOR.MINOR.PATCH+feature-slug.iNN`

## Mobile Stack Configuration
The included stack configuration (`prompts/stacks/stack-mobile.md`) provides:
- Flutter/Dart tech stack details
- Mobile folder structure patterns
- Testing strategy for mobile apps
- iOS/Android deployment targets

## Prompt Index
See `PROMPTS_INDEX.md` for detailed cross-reference of mobile-specific prompts.

## Backlog
Maintain optional `docs/BACKLOG.md` for deferred mobile features surfaced during Iteration prompt.

## Extensibility
New mobile-specific steps may be added (e.g., App Store Review, Performance Testing) without modifying the core workflow.

---
© 2025 Mobile Development Template
