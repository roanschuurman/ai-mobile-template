# 📦 Mobile Stack

## 🧱 Project Type

**Cross-platform Mobile Application** built using Flutter and Dart. This stack emphasizes modularity, testability, and iterative development using Clean Architecture principles.

---

## 🧰 Technology Choices & Rationale

### Core Stack
* **Framework:** Flutter 3.24.1 (stable) — Cross-platform native performance, mature ecosystem
* **Language:** Dart 3.5.1 — Null safety, strong typing, optimized for Flutter
* **State Management:** Riverpod v2.4.9 — Provider-based architecture, compile-time safety
* **Code Generation:** Freezed v2.4.6 — Immutable data classes, pattern matching
* **Architecture:** Clean Architecture — Clear separation of concerns, testable business logic

### Supporting Technologies
* **Routing:** go_router v12.1.3 — Declarative navigation with type safety
* **Testing:** flutter_test + mockito v5.4.2 — Comprehensive unit and widget testing
* **UI Design:** Atomic Design + Material Design 3 — Scalable component hierarchy
* **Build Tools:** Flutter CLI, Xcode 15.0+, Android Studio (API 21+)

### Architecture Decisions
* **Provider-Based DI:** Riverpod's provider system for dependency injection
* **Immutable State:** Freezed classes for all data models and state
* **Layered Architecture:** UI → Controller → Service → Repository pattern

---

## 📋 Quality Framework Summary

* **Testing Standards:** >90% code coverage, unit + widget + integration testing
* **Performance Targets:** App startup <3s, 60fps UI, memory usage <100MB baseline
* **Security Requirements:** Certificate pinning, secure storage, biometric auth
* **Accessibility Standards:** VoiceOver/TalkBack support, contrast >4.5:1, touch targets >44px
* **CI/CD Pipeline:** Automated testing, security scanning, app store deployment

> **Complete Quality Gates:** See `docs/quality-gates.md` for detailed measurable criteria

---

## 📁 Architecture Pattern

### Folder Structure Philosophy
```
lib/
├── modules/             # Feature-based organization
│   └── {feature}/       # Isolated feature modules
│       ├── presentation/ # UI layer (widgets, pages, controllers)
│       ├── domain/      # Business logic (entities, repositories, usecases)
│       ├── data/        # Data layer (models, datasources, implementations)
│       └── tests/       # Feature-specific tests
├── shared/              # Common utilities and components
└── infrastructure/      # App-level configuration (DI, routing, themes)
```

### Design Principles
* **Clean Architecture:** Clear separation between UI, business logic, and data layers
* **Provider-Based State:** All state management through Riverpod providers
* **Immutable Data:** Freezed classes for type-safe, immutable data structures
* **Atomic Design:** UI components organized in scalable hierarchy

### State Management Pattern
```dart
// Clean Architecture with Riverpod
Controller (Presentation) → Repository (Domain) → DataSource (Data)
     ↓                           ↓                      ↓
StateNotifierProvider    →  Abstract Interface  →  Implementation
```

---

## 🔄 Integration with Workflow

This stack definition is consumed by:
* `start-project.prompt.md` — Project initialization and stack selection
* `create-feature.prompt.md` — Feature development orchestration
* `update-feature.prompt.md` — Feature modification workflows
* Generic 8-step development flow — Technology-specific implementations

### Implementation Details
> **Complete Setup Guide:** See `prompts/stacks/instructions_mobile.md` for:
> - Detailed installation and configuration steps
> - Coding standards and best practices
> - State management patterns and examples
> - Testing strategies and templates
> - Performance optimization techniques

### Quality Assurance
> **Quality Framework:** See `docs/quality-gates.md` for measurable success criteria at each workflow step

### Automation
> **CI/CD Pipeline:** See `.github/workflows/mobile-ci.yml` for automated testing and app store deployment configuration
