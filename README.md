# CW06 Android Host Application

## About
CW06 is the Android platform host layer for a Flutter mobile application. This repository contains the Android-specific project configuration required to build, run, package, and launch the Flutter experience on Android devices and emulators.

Rather than holding the complete Flutter feature code, this codebase focuses on the Android runtime integration points—Gradle build setup, application manifest configuration, launch theme resources, and Flutter embedding entry point.

## Project Description
This project is structured as a modern Android application module that uses:

- **Flutter embedding v2** for rendering Dart/Flutter UI inside an Android activity.
- **Kotlin-based Android entry point** (`MainActivity`) extending `FlutterActivity`.
- **Gradle-based Android build pipeline** with Android and Kotlin plugins managed through Flutter's tooling.
- **Environment-aware build settings** (SDK levels, NDK version, version code/name) inherited from the parent Flutter configuration.
- **Firebase-ready setup** via `google-services.json` for Android service integration.
- **Android launch and theme resources** for polished startup UX and compatibility across API levels.

## Architecture at a Glance
- `settings.gradle` wires Flutter's Gradle tooling and plugin management.
- Root `build.gradle` defines shared repositories and output directory structure.
- `app/build.gradle` defines Android application build behavior, signing behavior for release profile defaults, and Flutter source linkage.
- `app/src/main/AndroidManifest.xml` configures app metadata, launcher activity behavior, intent filters, and Flutter embedding metadata.
- `app/src/main/kotlin/.../MainActivity.kt` provides the Android entry class that hosts Flutter.

## Key Capabilities
- Launches as a standard Android app with Flutter-rendered UI.
- Supports debug and release build types through Gradle.
- Maintains compatibility with Flutter-managed SDK and versioning inputs.
- Includes resource scaffolding for app icons and launch backgrounds.
- Ready for extension with Android-native integrations when platform-specific features are required.

## Typical Use Cases
This repository is most useful when you need to:

- Customize Android app identity (application ID, label, icons, themes).
- Add Android permissions, activities, services, or intent filters.
- Integrate Android-native SDKs or Firebase services.
- Tune Android build, signing, and deployment behavior for CI/CD.

## Build & Run
From the parent Flutter project root (the directory that contains `pubspec.yaml`), use standard Flutter commands:

```bash
flutter pub get
flutter run
```

To build Android artifacts:

```bash
flutter build apk
# or
flutter build appbundle
```

If you are operating specifically within the Android module, Gradle tasks are available through:

```bash
./gradlew assembleDebug
./gradlew assembleRelease
```

## Notes
- The Android module references Flutter-managed values for SDK and versioning; keep Flutter and Android toolchains aligned.
- Release signing is currently configured to use debug signing defaults in this scaffold and should be replaced with production signing configuration before store distribution.

---

If you want, I can also produce a companion **developer onboarding guide** (setup prerequisites, folder ownership, and release checklist) tailored to your team workflow.
