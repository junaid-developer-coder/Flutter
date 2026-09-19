<p align="center">
  <img src="assets/Flutter_logo.png" alt="Flutter Setup Logo" width="140" />
</p>

<h1 align="center">Flutter Setup Guide</h1>

<p align="center">
  A clean, step-by-step guide to installing and configuring Flutter on <b>Windows</b> and <b>Linux</b>.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Flutter-Stable-02569B?logo=flutter&logoColor=white" alt="Flutter" />
  <img src="https://img.shields.io/badge/Dart-Included-0175C2?logo=dart&logoColor=white" alt="Dart" />
  <img src="https://img.shields.io/badge/Windows-10%2F11-0078D6?logo=windows&logoColor=white" alt="Windows" />
  <img src="https://img.shields.io/badge/Linux-Ubuntu%20%7C%20Debian%20%7C%20Fedora-FCC624?logo=linux&logoColor=black" alt="Linux" />
  <img src="https://img.shields.io/badge/License-MIT-green" alt="MIT License" />
</p>

---

## Table of Contents

- [Overview](#overview)
- [System Requirements](#system-requirements)
- [Install on Windows](#install-on-windows)
- [Install on Linux](#install-on-linux)
- [Verify the Installation](#verify-the-installation)
- [Create and Run Your First App](#create-and-run-your-first-app)
- [Recommended Editor Setup](#recommended-editor-setup)
- [Troubleshooting](#troubleshooting)
- [Push This Repository to GitHub](#push-this-repository-to-github)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

Flutter is Google's open-source UI toolkit for building apps for mobile, web, and desktop from a single codebase. This repository documents a reliable, repeatable setup process for developer machines.

> Always check the official docs for the latest requirements: <https://docs.flutter.dev/get-started/install>

## System Requirements

| Requirement | Windows | Linux |
|---|---|---|
| OS | Windows 10 or 11 (64-bit) | 64-bit distro (Ubuntu, Debian, Fedora, etc.) |
| Disk space | ~2.5 GB + IDE and tools | ~2.5 GB + IDE and tools |
| Tools | Git for Windows, PowerShell | `bash`, `curl`, `git`, `unzip`, `xz-utils`, `zip` |

---

## Install on Windows

### 1. Install Git

```powershell
winget install --id Git.Git -e
```

### 2. Get the Flutter SDK

**Option A: Git clone (recommended, easy to update)**

```powershell
mkdir C:\src
cd C:\src
git clone https://github.com/flutter/flutter.git -b stable
```

**Option B: Manual download**

Download the stable ZIP from <https://docs.flutter.dev/get-started/install/windows>, then extract it to `C:\src\flutter`.

> Do not install Flutter in a folder that needs elevated permissions, such as `C:\Program Files\`.

### 3. Add Flutter to your PATH

```powershell
[Environment]::SetEnvironmentVariable(
  "Path",
  $env:Path + ";C:\src\flutter\bin",
  [EnvironmentVariableTarget]::User
)
```

Close and reopen your terminal afterwards.

### 4. Install Android tooling (for Android apps)

1. Install [Android Studio](https://developer.android.com/studio).
2. Open **SDK Manager** and install:
   - Android SDK Platform (latest)
   - Android SDK Command-line Tools
   - Android SDK Build-Tools
3. Accept licenses:

```powershell
flutter doctor --android-licenses
```

### 5. Install Visual Studio (for Windows desktop apps)

Install [Visual Studio 2022](https://visualstudio.microsoft.com/downloads/) (Community edition is fine) with the **Desktop development with C++** workload.

---

## Install on Linux

### 1. Install dependencies

**Ubuntu / Debian**

```bash
sudo apt update
sudo apt install -y curl git unzip xz-utils zip libglu1-mesa
```

For Linux desktop development also install:

```bash
sudo apt install -y clang cmake ninja-build pkg-config libgtk-3-dev liblzma-dev
```

**Fedora**

```bash
sudo dnf install -y curl git unzip xz zip mesa-libGLU
sudo dnf install -y clang cmake ninja-build pkgconf-pkg-config gtk3-devel xz-devel
```

### 2. Get the Flutter SDK

**Option A: Git clone (recommended)**

```bash
mkdir -p ~/development
cd ~/development
git clone https://github.com/flutter/flutter.git -b stable
```

**Option B: Snap**

```bash
sudo snap install flutter --classic
```

### 3. Add Flutter to your PATH

```bash
echo 'export PATH="$HOME/development/flutter/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

If you use Zsh, replace `~/.bashrc` with `~/.zshrc`.

### 4. Install Android tooling (for Android apps)

1. Install [Android Studio](https://developer.android.com/studio).
2. Install the SDK, Command-line Tools, and Build-Tools from **SDK Manager**.
3. Accept licenses:

```bash
flutter doctor --android-licenses
```

---

## Verify the Installation

```bash
flutter --version
flutter doctor -v
```

Every section should show a green check. Fix anything marked with `[!]` or `[✗]` by following the hints in the output.

## Create and Run Your First App

```bash
flutter create my_app
cd my_app
flutter run
```

To pick a target explicitly:

```bash
flutter devices
flutter run -d windows   # or: linux, chrome, <device-id>
```

## Recommended Editor Setup

- **VS Code**: install the *Flutter* and *Dart* extensions.
- **Android Studio / IntelliJ**: install the *Flutter* plugin.

## Troubleshooting

| Problem | Fix |
|---|---|
| `flutter` is not recognized / command not found | Re-check your PATH entry and restart the terminal. |
| Android licenses not accepted | Run `flutter doctor --android-licenses`. |
| `cmdline-tools component is missing` | Install *Android SDK Command-line Tools* in SDK Manager. |
| Visual Studio not found (Windows) | Install the *Desktop development with C++* workload. |
| `Unable to find git in your PATH` | Install Git and reopen your terminal. |
| Linux desktop build fails | Install `clang`, `cmake`, `ninja-build`, `pkg-config`, `libgtk-3-dev`. |

Keep Flutter up to date:

```bash
flutter upgrade
```

Without GitHub CLI, create an empty repo on github.com and run:

```bash
git remote add origin https://github.com/YOUR_USERNAME/flutter-setup.git
git push -u origin main
```

## Contributing

1. Fork the repository
2. Create a branch: `git checkout -b docs/improve-linux-section`
3. Commit using [Conventional Commits](https://www.conventionalcommits.org/): `git commit -m "docs: improve Linux section"`
4. Push and open a Pull Request

## License

Released under the [MIT License](LICENSE).

## Trademark Notice

Flutter and the Flutter logo are trademarks of Google LLC. This repository is an independent guide and is not affiliated with or endorsed by Google. The logo in `assets/` is an original design created for this repository. To use the official Flutter logo, follow Google's brand guidelines.
