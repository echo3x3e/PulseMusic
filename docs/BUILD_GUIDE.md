# 🛠️ PulseMusic Build & Development Guide

## 1. Prerequisites

- **Python:** 3.10+ with `pip` and virtual environment support
- **C++ Compiler:** GCC 11+ or Clang 14+ (for compiling native C++ DSP core)
- **Android SDK:** API Level 34+ with JDK 17 (for compiling the Android APK)

---

## 2. Desktop Client (Linux / Windows / macOS)

### Set up development environment
```bash
python3 -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r desktop_qt/requirements-desktop.txt
```

### Compile Native C++ DSP Core
```bash
# Linux
sh desktop_qt/cpp/build_linux.sh

# macOS
sh desktop_qt/cpp/build_macos.sh

# Windows (Command Prompt)
desktop_qt\cpp\build_windows.bat
```

### Run Desktop Application
```bash
python3 desktop_qt/main.py
```

### Build Standalone Executables
```bash
# Linux (tarball package)
python3 desktop_qt/build_linux.py --work /tmp/pulse-work --out dist/

# Windows Installer (InnoSetup + PyInstaller)
build-desktop-exe.bat
```

---

## 3. Android Client (APK)

```bash
# Debug APK
./gradlew assembleDebug

# Release APK
./gradlew assembleRelease
```
Compiled APK artifacts are located under `app/build/outputs/apk/`.
