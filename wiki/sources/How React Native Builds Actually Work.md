# How React Native Builds Actually Work

Original clipping: [YouTube](https://www.youtube.com/watch?v=1o0pEjYGUWM)  
Author: Code with Beto  
Published: 2026-04-30  
Processed: 2026-05-10

## Summary

The clipping explains the main React Native mobile release artifacts: Android APK, Android AAB, iOS `.app`, and iOS IPA. It also compares local native builds, EAS local builds, and EAS cloud builds.

## Verified Updates

- Android App Bundles are the required Google Play publishing format for new apps, and Google Play generates optimized APKs from the uploaded bundle for device-specific delivery.
- React Native's current Android publishing guide documents `npx react-native build-android --mode=release`, which uses Gradle `bundleRelease` and outputs `android/app/build/outputs/bundle/release/app-release.aab`.
- Expo `prebuild` generates native `android/` and `ios/` directories from app configuration.
- EAS Build is a hosted service for building Expo and React Native binaries, and `eas build --local` runs the EAS build process on the local machine with documented limitations.
- For iOS distribution, Xcode creates an archive and uploads or exports it through the Archives organizer for TestFlight or App Store distribution.

## Web Sources Checked

- [Expo EAS Build](https://docs.expo.dev/build/introduction/)
- [Expo local EAS builds](https://docs.expo.dev/build-reference/local-builds/)
- [Expo prebuild](https://docs.expo.dev/workflow/prebuild)
- [React Native publishing to Google Play](https://reactnative.dev/docs/signed-apk-android.html)
- [Android App Bundles](https://developer.android.google.cn/guide/app-bundle?hl=en)
- [Apple app distribution](https://developer.apple.com/documentation/Xcode/distributing-your-app-for-beta-testing-and-releases)

## Related Pages

- [[Mobile Development/React Native/Build Artifacts and Release Builds]]
