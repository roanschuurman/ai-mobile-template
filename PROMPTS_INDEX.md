# Mobile Development Prompt Index

| Category | Path | Purpose |
|----------|------|---------|
| Workflow | prompts/workflow/workflow.md | Unified 8-step mobile development workflow |
| Action | prompts/actions/start-project.prompt.md | Initialize mobile project + load Flutter stack |
| Action | prompts/actions/create-feature.prompt.md | Orchestrate new mobile feature lifecycle |
| Action | prompts/actions/update-feature.prompt.md | Orchestrate mobile feature update |
| Stack | prompts/stacks/stack-mobile.md | Flutter mobile stack definition |
| Instructions | prompts/stacks/instructions_mobile.md | Complete Flutter development standards |
| Quality | docs/quality-gates.md | Measurable quality criteria for mobile development |
| Documentation | docs/CHANGELOG.md | Mobile release documentation template |
| Documentation | docs/BACKLOG.md | Mobile feature backlog management |
| Documentation | docs/ARCHITECTURE.md | Mobile system architecture documentation |
| CI/CD | .github/workflows/mobile-ci.yml | Flutter automated testing pipeline |

## Cross References

| Artifact | Generated/Updated By | Notes |
|----------|----------------------|-------|
| README.md (feature/module) | 01,02,07,08 | Mobile feature iteration sections appended |
| tasks.md | 01,02,03,04,06,07 | Trace each mobile task to acceptance test IDs |
| user-test.md | 01,05,06 | Mobile app testing: planned vs automated vs manual results |
| CHANGELOG.md | 07 | Mobile app semantic version entry |
| BACKLOG.md | 08 | Deferred mobile improvements |
| quality-gates.md | All steps | Mobile quality criteria validation at each gate |
| instructions_mobile.md | 01,02,03 | Flutter technical standards and setup requirements |
| mobile-ci.yml | 05,07 | Flutter automated testing and deployment validation |

## Mobile-Specific Metrics Tracked
- Flutter widget test coverage
- Integration test pass rates
- iOS/Android build success rates
- App store deployment metrics
- Mobile performance benchmarks (startup time, memory usage)
- Platform-specific compatibility scores
- Mobile accessibility compliance (iOS/Android guidelines)
- Device testing coverage across form factors

## Flutter Development Quality Gates
- **Unit Testing**: >85% code coverage for business logic
- **Widget Testing**: All custom widgets must have tests
- **Integration Testing**: Critical user flows tested end-to-end
- **Performance**: App startup time <3 seconds on mid-range devices
- **Accessibility**: VoiceOver/TalkBack compatibility
- **Platform Compliance**: iOS Human Interface Guidelines & Material Design
- **Security**: Mobile security best practices (secure storage, network security)
- **Compatibility**: Support for iOS 12+ and Android API 21+
