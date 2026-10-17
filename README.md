# 🍱 BatchBite

**Know exactly what each serving costs — before you shop.**

BatchBite is a per-meal batch budget calculator. Tell it what a batch costs and how many servings it makes, and it shows you the precise cost per serving, a cost breakdown per ingredient, and a pantry surplus report for partially used ingredients (so you know what's already paid for). Built as a tight, dark single-page app with a mobile-first mindset.

Built by [Marusame00](https://github.com/Marusame00) with AI assistance from [Abacus AI Agent](https://abacus.ai) — the app concept, the original HTML/CSS/JS, and the Android packaging were a collaboration between the developer and the agent stack.

## ✨ Features

- **Cost per serving** — live KPI as you type: total batch cost ÷ servings
- **Ingredient-level breakdown** — per-ingredient cost badges, a stacked cost bar, and a full legend
- **Pantry surplus** — partially-used ingredients report what's left and what it's worth
- **Batch & servings controls** — quick steppers, plus anchor-ingredient logic
- **Load Example / Reset** — one tap to see it in action ("Burger Night")
- **100% offline** — styles, icons, and fonts are bundled; no network calls
- **Native Android app** — edge-to-edge aware (status bar, camera cutout, gesture navigation), adaptive launcher icon

## 📂 Project layout

| Path | What it is |
| --- | --- |
| `index.html` | Original browser version (uses CDN dependencies) |
| `www/` | Offline bundle consumed by the Android app (Tailwind, Lucide and fonts vendored locally) |
| `android/` | Native Android project that packages `www/` into an installable APK |

The Android app is a WebView that loads `www/index.html` straight from the APK's assets. Everything else (Tailwind, icons, fonts) ships inside APK files.

## 📲 Install on an Android phone

The easiest way — no build tools required:

1. On your phone, open: **github.com/Marusame00/batchbite → Releases → latest** (or download the APK directly from the `app-debug.apk` asset on the release page)
2. Tap the downloaded `app-debug.apk`
3. If prompted, allow installing from your browser ("Allow from this source")
4. Tap **Install anyway** when Android warns about an unknown source — it is a debug-signed build, which is expected
5. Open **BatchBite** from your app drawer

> Prefer USB? Install with ADB instead: enable **Settings → Developer options → USB debugging**, connect the phone, then from a PC with the Android platform-tools:
>
> ```powershell
> adb install -r app-debug.apk
> ```
>
> Use a cable that supports data (charge-only cables are the usual reason a phone never shows up in `adb devices`).

## 🛠 Build the APK yourself

Requires **Git, Android Studio (which includes the Android SDK), and a JDK** (any recent one; Android Studio bundles JBR).

```powershell
git clone https://github.com/Marusame00/batchbite.git
cd batchbite\android
.\gradlew.bat :app:assembleDebug
```

The APK is named after the version (e.g. `BatchBite-1.2.apk`) and lands in `app\dist\` (AGP's stock `app-debug.apk` stays in `app\build\outputs\apk\debug\`).

Or just open the `android` folder in **Android Studio** and press **Run** — it builds, installs, and launches on whatever device or emulator is attached.

## ▶️ Emulator notes

The emulator wants hardware virtualization: **Intel VT-x / AMD SVM** enabled in your BIOS/UEFI, plus the **Android Emulator Hypervisor Driver** (SDK Manager → SDK Tools) or the Windows **Hypervisor Platform** feature. Heads-up from real-world testing: on some machines (an ASUS Prime X570-P is one of them) enabling SVM has caused Windows boot trouble — if that happens, set SVM back to Disabled (Windows will boot again; nothing is lost) and just use a physical phone. The app needs nothing special on-device (minSdk 26 = Android 8.0+).

## 🧑‍💻 Editing the app

- **UI changes:** edit `www/index.html` — it is the single file that gets packaged into the apps (the root `index.html` is the legacy CDN version; keep them in sync if you want the browser copy identical)
- **Rebuild:** run the Gradle command above again, or press Run in Android Studio
- **Release number:** bump `versionCode` and `versionName` in `android\app\build.gradle`, rebuild, and publish a tagged GitHub Release with the new APK attached

Signing for distribution (Play Store) needs a release keystore — in Android Studio: **Build → Generate Signed App Bundle / APK**.

## 📄 License

MIT, see [LICENSE](LICENSE).
