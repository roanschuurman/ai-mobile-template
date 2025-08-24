# Mobile Development Instructions (Flutter/Dart)

## Development Environment Requirements

### Flutter SDK
- **Version**: Flutter 3.24.1 (stable channel)
- **Dart**: 3.5.1 (included with Flutter)
- **Installation**: `flutter doctor` must show no issues

### IDE Setup
- **Primary**: VS Code with Flutter/Dart extensions
- **Alternative**: Android Studio with Flutter plugin
- **Required Extensions**:
  - Flutter (Dart-Code.flutter)
  - Dart (Dart-Code.dart-code)
  - Error Lens (usernamehw.errorlens)
  - GitLens (eamodio.gitlens)

### Platform Requirements
- **iOS**: Xcode 15.0+, iOS Simulator 17.0+
- **Android**: Android Studio, API level 21+ (Android 5.0)
- **Device Testing**: Physical device or simulator required

## Code Quality Standards

### Linting & Formatting
```yaml
# analysis_options.yaml (required in project root)
include: package:flutter_lints/flutter.yaml

analyzer:
  exclude:
    - "**/*.g.dart"
    - "**/*.freezed.dart"
  strong-mode:
    implicit-casts: false
    implicit-dynamic: false

linter:
  rules:
    - prefer_const_constructors
    - prefer_const_literals_to_create_immutables
    - avoid_print
    - prefer_final_locals
    - unnecessary_null_checks
```

### Dependency Management
```yaml
# pubspec.yaml constraints
dependencies:
  flutter:
    sdk: flutter
  flutter_riverpod: ^2.4.9
  freezed_annotation: ^2.4.1
  go_router: ^12.1.3
  
dev_dependencies:
  flutter_test:
    sdk: flutter
  build_runner: ^2.4.7
  freezed: ^2.4.6
  json_serializable: ^6.7.1
  flutter_lints: ^3.0.1
  mockito: ^5.4.2
```

## Architecture Patterns

### Clean Architecture Layers
```
lib/
├── core/                   # Shared utilities, constants
│   ├── errors/            # Exception classes
│   ├── constants/         # App constants
│   └── utils/             # Helper functions
├── shared/                # Reusable UI components
│   ├── widgets/           # Common widgets
│   ├── theme/             # App theme & styles
│   └── extensions/        # Dart extensions
└── modules/{feature}/
    ├── domain/            # Business logic (entities, repositories)
    ├── data/              # Data layer (models, data sources)
    ├── presentation/      # UI layer
    │   ├── screens/       # Screen widgets
    │   ├── widgets/       # Feature-specific widgets
    │   └── controllers/   # Riverpod providers
    └── tests/             # All test files
```

### State Management Rules
- **Global State**: Use Riverpod providers in `lib/core/providers/`
- **Local State**: Use `useState` hooks or `StatefulWidget`
- **Async State**: Always use `AsyncValue<T>` for API calls
- **Error Handling**: Wrap all async operations in try-catch

### Data Classes (Freezed)
```dart
// Required pattern for all data models
@freezed
class User with _$User {
  const factory User({
    required String id,
    required String name,
    String? email,
  }) = _User;
  
  factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);
}
```

## Testing Requirements

### Test Coverage Targets
- **Unit Tests**: >90% for services/controllers
- **Widget Tests**: >80% for screens/widgets
- **Integration Tests**: Critical user flows only

### Test Structure
```dart
// Required test pattern
void main() {
  group('UserService', () {
    late UserService userService;
    late MockApiClient mockApiClient;
    
    setUp(() {
      mockApiClient = MockApiClient();
      userService = UserService(mockApiClient);
    });
    
    testWidgets('should fetch user successfully', (tester) async {
      // Arrange
      when(mockApiClient.getUser(any))
          .thenAnswer((_) async => mockUserResponse);
      
      // Act
      final result = await userService.getUser('123');
      
      // Assert
      expect(result.isSuccess, true);
      expect(result.data?.name, 'John Doe');
    });
  });
}
```

### Testing Commands
```bash
# Run all tests
flutter test

# Run with coverage
flutter test --coverage
genhtml coverage/lcov.info -o coverage/html

# Run specific test file
flutter test test/modules/auth/auth_service_test.dart
```

## Performance Standards

### Metrics Targets
- **App Startup**: <2s cold start, <1s warm start
- **Frame Rate**: 60fps minimum, 120fps preferred
- **Memory Usage**: <150MB RAM for basic screens
- **Bundle Size**: <50MB APK, <100MB iOS app

### Performance Monitoring
```dart
// Required: Add to main.dart
void main() {
  if (kReleaseMode) {
    // Initialize crash reporting
    FirebaseCrashlytics.instance.setCrashlyticsCollectionEnabled(true);
  }
  
  runApp(
    ProviderScope(
      observers: [if (kDebugMode) ProviderLogger()],
      child: MyApp(),
    ),
  );
}
```

## Security Requirements

### Data Protection
- **Sensitive Data**: Never store in SharedPreferences
- **API Keys**: Use flutter_config for environment variables
- **Authentication**: Implement proper token refresh logic
- **Local Storage**: Use flutter_secure_storage for sensitive data

### Network Security
```dart
// Required: Certificate pinning for production
class ApiClient {
  static final dio = Dio()
    ..interceptors.add(
      CertificatePinningInterceptor(
        allowedSHAFingerprints: ['YOUR_CERT_FINGERPRINT'],
      ),
    );
}
```

## Error Handling Patterns

### Exception Classes
```dart
// Required base exception
abstract class AppException implements Exception {
  const AppException(this.message, [this.code]);
  final String message;
  final String? code;
}

class NetworkException extends AppException {
  const NetworkException(super.message, [super.code]);
}

class ValidationException extends AppException {
  const ValidationException(super.message, [super.code]);
}
```

### Error UI Patterns
- **Network Errors**: Show retry button with exponential backoff
- **Validation Errors**: Inline form field errors
- **Critical Errors**: Full-screen error with support contact

## UI/UX Standards

### Accessibility Requirements
- **Semantic Labels**: All interactive elements must have semanticLabels
- **Color Contrast**: WCAG AA compliance (4.5:1 ratio)
- **Screen Reader**: Test with TalkBack/VoiceOver
- **Focus Management**: Proper tab order for navigation

### Design System
```dart
// Required: Consistent spacing scale
class AppSpacing {
  static const double xs = 4.0;
  static const double sm = 8.0;
  static const double md = 16.0;
  static const double lg = 24.0;
  static const double xl = 32.0;
}

// Required: Consistent color palette
class AppColors {
  static const Color primary = Color(0xFF007AFF);
  static const Color secondary = Color(0xFF5856D6);
  static const Color success = Color(0xFF34C759);
  static const Color warning = Color(0xFFFF9500);
  static const Color error = Color(0xFFFF3B30);
}
```

## Git Workflow

### Branch Strategy
- **main**: Production-ready code only
- **develop**: Integration branch
- **feature/**: Feature branches from develop
- **hotfix/**: Critical fixes from main

### Commit Standards
```
feat(auth): add biometric login support [i01]

- Implement TouchID/FaceID authentication
- Add fallback to PIN entry
- Update login flow with biometric option
- Add unit tests for biometric service

Closes: #123
```

### Pre-commit Requirements
- Code must pass `flutter analyze`
- All tests must pass `flutter test`
- Code coverage must not decrease
- No TODO comments in production code

## Release Process

### Build Configuration
```bash
# Debug build
flutter build apk --debug

# Release build (Android)
flutter build apk --release --obfuscate --split-debug-info=build/debug-info

# Release build (iOS)
flutter build ipa --release --obfuscate --split-debug-info=build/debug-info
```

### Quality Gates
1. **Code Review**: Required for all PRs
2. **Automated Tests**: Must pass CI pipeline
3. **Manual Testing**: Device testing required
4. **Performance Check**: Profile mode testing
5. **Security Scan**: Dependency audit clean

## Monitoring & Analytics

### Required Integrations
- **Crashlytics**: Crash reporting and non-fatal errors
- **Analytics**: User behavior tracking (Firebase Analytics)
- **Performance**: App performance monitoring
- **Remote Config**: Feature flags and A/B testing

### Key Metrics to Track
- Crash-free session rate (>99.5%)
- App startup time
- Screen load times
- User engagement metrics
- Conversion funnel performance

---
*This document is living and should be updated as standards evolve.*
