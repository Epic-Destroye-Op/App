# MacroX — Android starter project

A pure-black, restrained red-accent Android macro controller UI. No game profiles and no floating overlay.

## Included
- Jetpack Compose UI with Home, Macros, History and Settings tabs
- Large power control to arm/disarm the engine
- Foreground service with persistent notification
- Accessibility service configured to listen for Volume Up or Volume Down
- Repeat-mode preference and starter macro runner structure

## Build
Open this folder in Android Studio (JDK 17), allow Gradle sync, then use **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

## Important Android limitation
The Android public SDK does not provide ordinary apps with a general-purpose API to inject arbitrary keyboard events (for example, synthesize `Z` inside another app). The included macro runner is deliberately a safe starter adapter: it accepts trigger events and demonstrates the execution lifecycle, but it does not pretend arbitrary key injection works. Accessibility gestures can perform screen taps when the user has explicitly configured targets; support and behavior vary by app and Android version.

Volume-key filtering through AccessibilityService is device-dependent. Some Android builds reserve hardware keys for system behavior. Android 13+ notification permission is requested at launch. The foreground service notification remains visible while the engine is armed.

## Suggested next implementation step
Add a user-editable action list with Delay and Accessibility Tap actions, then implement screen-coordinate capture with a clear preview and a stop mechanism. Do not add hidden input capture or bypass Android security controls.
