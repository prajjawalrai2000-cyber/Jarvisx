# ⚡ JARVIS X — Android Native AI Assistant

A fully native Android AI assistant with:
- 🤚 **12 Real Hand Gestures** detected via MediaPipe + CameraX
- ⚡ **System Floating Orb** (SYSTEM_ALERT_WINDOW) always visible
- 🔀 **Real App Switching** via AccessibilityService
- 📱 **30+ App Launcher** with PackageManager
- 🎙️ **Voice Commands** (multilingual: English, Hindi, Hinglish, Bengali, Tamil...)
- 🔋 **Battery Safety Mode** (5fps when <20%)

---

## 🚀 QUICK START (5 Steps)

### Step 1: Download MediaPipe Model
```bash
curl -o app/src/main/assets/hand_landmarker.task \
  https://storage.googleapis.com/mediapipe-models/hand_landmarker/hand_landmarker/float16/1/hand_landmarker.task
```

### Step 2: Open in Android Studio
1. Open Android Studio (Hedgehog or newer)
2. File → Open → select this `JarvisX` folder
3. Wait for Gradle sync to complete

### Step 3: Build & Run
1. Connect Android phone (API 29+ / Android 10+)
2. Enable Developer Options + USB Debugging
3. Click ▶ Run in Android Studio

### Step 4: Grant Permissions (Setup Wizard)
1. **Overlay** → Settings → Apps → Special Access → Display Over Other Apps → JARVIS X → Allow
2. **Accessibility** → Settings → Accessibility → Installed Services → JARVIS X → Enable
3. **Camera** → Allow when app prompts

### Step 5: Start JARVIS X
1. Tap "⚡ Start Orb" on home screen
2. A cyan orb appears on screen edge
3. Tap orb → opens JARVIS
4. Long press orb → Quick Panel
5. Go to Gesture tab → Start camera → Show hand!

---

## 🤚 12 Gestures

| Gesture | Action |
|---------|--------|
| 🤚 Open Palm | Activate Voice |
| ✊ Fist | Go Home |
| 👈 Swipe Left | Previous App |
| 👉 Swipe Right | Next App |
| ✌️ V Sign | Answer Call |
| 👍 Thumbs Up | Open YouTube |
| 🤟 Three Fingers | Open Instagram |
| 🖐️ Four Fingers | Open WhatsApp |
| 👌 OK Sign | Open Settings |
| 🤏 Pinch | Go Back |
| ☝️ Index Point | Open Maps |
| 🤙 Shaka | Open Phone |

---

## 📁 Project Structure

```
app/src/main/java/com/jarvisx/app/
├── core/
│   ├── accessibility/   → JarvisAccessibilityService (app switching, global actions)
│   ├── events/          → JarvisEventBus (SharedFlow-based communication)
│   ├── gesture/         → GestureEngine + GestureClassifier (12 gestures)
│   └── overlay/         → FloatingOrbService (system overlay)
├── feature/
│   ├── apps/            → AppRegistry + LaunchEngine (PackageManager)
│   ├── camera/          → GestureCameraService (CameraX foreground service)
│   ├── panel/           → PanelActivity (quick overlay panel)
│   ├── settings/        → SettingsActivity
│   └── voice/           → VoiceEngine (SpeechRecognizer + TTS)
├── data/
│   ├── AppHistoryStack  → In-memory app history (swipe navigation)
│   └── GesturePrefsRepo → DataStore gesture→app mappings
├── ml/
│   └── HandLandmarkerHelper → MediaPipe Tasks wrapper
└── ui/                  → Compose screens, theme, components
```

---

## ⚙️ Requirements

- **Android:** API 29+ (Android 10 or higher)
- **RAM:** 3GB minimum (4GB+ recommended)
- **Camera:** Front-facing camera required
- **Android Studio:** Hedgehog (2023.1.1) or newer
- **JDK:** 17
- **MediaPipe model:** ~9MB (download separately, see Step 1)

---

## 🔑 Gemini AI (Optional)
1. Get free API key: https://aistudio.google.com
2. Open app → Settings → Paste key → Save

---

## 🔒 Privacy
- Camera frames processed **entirely on-device** via MediaPipe
- No frames stored or transmitted
- No personal data collected
- Accessibility service only performs navigation actions
