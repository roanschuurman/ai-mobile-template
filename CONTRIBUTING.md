# Contributing to AI Mobile Template

Thank you for your interest in contributing to the AI Mobile Template! This document provides guidelines and information for contributors.

## Code of Conduct

This project adheres to a code of conduct. By participating, you are expected to uphold this code. Please report unacceptable behavior to the project maintainers.

## How to Contribute

### Reporting Bugs

Before creating bug reports, please check the existing issues to avoid duplicates. When you are creating a bug report, please include as many details as possible:

- Use a clear and descriptive title
- Describe the exact steps to reproduce the problem
- Provide specific examples and code snippets
- Include Flutter/Dart version information
- Mention the platform (iOS/Android) where the issue occurs

### Suggesting Enhancements

Enhancement suggestions are welcome! Please provide:

- A clear and descriptive title
- A detailed description of the proposed feature
- Examples of how the feature would be used
- Any relevant mockups or diagrams

### Pull Requests

1. Fork the repository
2. Create a feature branch from `develop`
3. Make your changes following the coding standards
4. Add or update tests as necessary
5. Update documentation if needed
6. Ensure all tests pass
7. Create a pull request

#### Pull Request Guidelines

- Follow the conventional commit format
- Include the iteration marker `[iNN]` in commits
- Provide a clear description of changes
- Reference related issues
- Ensure CI pipeline passes

## Development Setup

### Prerequisites

- Flutter 3.24.1 (stable)
- Dart 3.5.1
- VS Code with Flutter/Dart extensions
- Git

### Local Development

1. Clone the repository
2. Run `flutter doctor` to verify setup
3. Follow the instructions in `prompts/stacks/instructions_mobile.md`

## Coding Standards

### Code Style

- Follow the Dart style guide
- Use `dart format` for consistent formatting
- Run `flutter analyze` and fix all warnings
- Maintain >90% test coverage for new code

### Testing

- Write unit tests for all business logic
- Add widget tests for UI components
- Include integration tests for critical flows
- Follow the test patterns in `instructions_mobile.md`

### Documentation

- Update README.md for significant changes
- Add inline documentation for complex logic
- Update relevant prompt files if workflow changes
- Keep CHANGELOG.md current

## Project Structure

```
├── docs/                    # Documentation
├── prompts/
│   ├── actions/            # Entry point prompts
│   ├── stacks/             # Technology stack definitions
│   └── workflow/           # 8-step development workflow
├── .github/
│   └── workflows/          # CI/CD configuration
└── README.md
```

## Versioning

This project uses semantic versioning with iteration markers:
- Template updates: `X.Y.Z`
- Feature iterations: `X.Y.Z+feature-slug.iNN`

## Questions?

If you have questions about contributing, please:
1. Check existing documentation
2. Search existing issues
3. Create a new issue with the "question" label

Thank you for contributing!
