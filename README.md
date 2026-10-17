# BatchBite

Per-meal batch budget calculator: enter what a batch costs and how many servings it makes, and BatchBite tells you the cost per serving — plus a pantry surplus breakdown for partially-used ingredients.

## Layout

| Path | What it is |
| --- | --- |
| `index.html` | Original browser version (CDN dependencies) |
| `www/` | Offline bundle used by the Android app (Tailwind, Lucide, fonts vendored locally) |
| `android/` | Native Android project that packages `www/` into an APK |

## Android app

The app is a WebView that loads `www/index.html` from the APK — everything else (Tailwind, icons, fonts) is bundled, so it works fully offline.rand

### Build

Open the `android/` folder in Android Studio and press Run, or from a terminal:

```
cd android
.\gradlew.bat :app:assembleDebug
```

### Run it

**On a real phone (easiest):** enable Developer Options > USB debugging, plug in the phone, then:

```
adb install -r app\build\outputs\apk\debug\app-debug.apk
```

Or copy the APK to the phone and tap it (allow "install unknown apps").

**On the emulator:** the emulator needs hardware virtualization enabled — either in the BIOS/UEFI firmware (Intel VT-x / AMD SVM), plus the "Windows Hypervisor Platform" Windows feature or the Android Emulator Hypervisor Driver (installable from Android Studio's SDK Manager). Without it the emulator will not boot. Once enabled, run the AVD from Android Studio or:

```
emulator -avd <your-avd-name>
```

### Update the app after editing the CSS/JS

Edit `www/index.html` (this single file is what gets packaged) and rebuild — the Gradle build copies `www/` into the app automatically.

### Release builds

`android/app/build/outputs/apk/release/app-release-unsigned.apk` is unsigned; to put BatchBite on the Play Store, generate a signing key in Android Studio (Build > Generate Signed App Bundle / APK).

Requires: Android SDK, Java / Android Studio. The launcher icon is an adaptive icon (minSdk 26).
