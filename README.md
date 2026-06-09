<div align="center">

<img src="logo.png" alt="SinType Logo" width="80"/>

# SinType Desktop

### Type Sinhala anywhere on Windows — instantly.

[![Version](https://img.shields.io/badge/version-2.0.0--beta-cyan?style=flat-square)](https://sintype.lk/download)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-blue?style=flat-square)](https://sintype.lk/download)
[![License](https://img.shields.io/badge/license-Free-green?style=flat-square)](https://sintype.lk/download)
[![Python](https://img.shields.io/badge/python-3.10%2B-yellow?style=flat-square)](https://python.org)

[Download](https://sintype.lk/download) · [Website](https://sintype.lk) · [FAQ](https://sintype.lk/faq) · [Report Bug](https://sintype.lk/feedback)

![SinType Demo](assets/<img width="512" height="512" alt="logo" src="https://github.com/user-attachments/assets/748610f6-4c2c-40a2-9930-169800697155" />
<img width="512" height="512" alt="sintype_icon - Copy" src="https://github.com/user-attachments/assets/6f889de0-d5a1-4665-a5e2-4f66bf170b29" />
demo.gif)

</div>

-----

## What is SinType?

SinType is a free, open-architecture Windows desktop application that converts **Singlish** (phonetic Sinhala typed in English letters) into beautiful **Sinhala Unicode** in real time — system-wide, across every app on your PC.

No copy-paste. No browser tab. Just type.

```
api     →  අපි
mama    →  මම  
koheda  →  කොහේද
```

-----

## Key Features

### 🌐 Type Sinhala Anywhere

Works system-wide using low-level Windows keyboard hooks. Type Sinhala in **Photoshop, Word, WhatsApp, Discord, Chrome, VS Code** — any app, no exceptions.

### ⚡ Two Typing Modes

- **Real-time mode** — converts as you type, word by word
- **Word mode** — manual trigger via hotkey for precision control

### 📱 Mobile Sync (v2.0)

Scan a QR code and use your phone as a **wireless keyboard and touchpad** for your PC — over your local Wi-Fi. No cloud. No app install on phone.

### 📁 Offline File Sharing (v2.0)

Drag and drop files from your phone to your PC over your local network. No internet, no USB, no cloud storage required.

### 🔤 Unicode & Legacy Support

Switch between **Unicode Sinhala**, **Legacy FM Abhaya fonts**, and **English** — directly from your phone remote or the floating toolbar.

### ✏️ Custom Key Mapping

Edit your own Singlish-to-Sinhala mapping rules. Your personal dictionary is always preserved across updates.

### 🔒 Everything Stays Private

All keystrokes and conversion happen **locally on your PC**. Nothing is sent to the internet. Your typing is yours.

-----

## Download

|Channel |Version    |Link                                               |
|--------|-----------|---------------------------------------------------|
|✅ Stable|v1.0.0     |[Download for Windows]([https://sintype.lk/download](https://github.com/udaperuweaththadassi-dotcom/SinType-Dektop-App/releases/download/Desktop_App/SinType.1.0_Setup.exe))|
|✅ Stable|v1.1.0     |[Download for Windows]([https://sintype.lk/download](https://github.com/udaperuweaththadassi-dotcom/SinType-Dektop-App/releases/download/Desktop_App.2/SinType.1.1_Setup.exe))       |
|✅ Stable|v2.0.0     |[Download for Windows]([https://sintype.lk/download](https://github.com/udaperuweaththadassi-dotcom/SinType-Dektop-App/releases/download/Desktop_App.3/SinType.2.0_Setup.exe))|


> **System Requirements:** Windows 10 / 11 (64-bit) · 4GB RAM · 50MB disk space

-----

## Getting Started

### Installation

```
1. Download the installer from sintype.lk/download
2. Run SinType_Setup.exe
3. Generate your free 30-day key at sintype.lk/download
4. Open SinType → License tab → Enter email + key
5. Start typing Sinhala anywhere!
```

### Quick Usage

```
1. SinType starts in the system tray
2. The floating toolbar shows your current mode
3. Type Singlish in any app
4. Text converts to Sinhala automatically
```

### Mobile Sync Setup

```
1. Open SinType → Mobile Sync tab
2. Scan the QR code with your phone camera
3. Both devices must be on the same Wi-Fi
4. Type from your phone — text appears on PC
```

-----

## Architecture

```
SinType Desktop App
│
├── main_app.py                  # App bootstrap, license, engine
├── src/
│   ├── sintype_ui.py            # Primary desktop UI (customtkinter)
│   ├── realtime_converter.py    # Real-time transliteration engine
│   ├── singlish_mapper.py       # Mapping trie & word-mode engine
│   ├── text_inject.py           # Windows text injection
│   ├── typing_pipeline.py       # Keyboard event queues
│   ├── floating_toolbar.py      # Floating toolbar UI
│   ├── hotkey_manager.py        # Global hotkeys
│   ├── startup_manager.py       # Windows autostart (registry)
│   ├── sintype_config.py        # User config & preferences
│   ├── supabase_config.py       # Cloud backend config
│   ├── supabase_services.py     # Feedback, reviews, notifications
│   ├── license_binding.py       # Device-bound license encryption
│   ├── paths.py                 # Bundle & user path resolution
│   ├── install_utils.py         # Installer/updater utilities
│   └── uninstall_helper.py      # Windows uninstall integration
│
└── mobile_server/
    ├── server.py                # Flask + Socket.IO local server
    ├── file_share.py            # Chunked file transfer manager
    └── qr_generator.py          # QR code for mobile connect
```

### How Real-time Conversion Works

```
User types "amma"
        │
        ▼
pynput keyboard listener captures keystrokes
        │
        ▼
ConverterEngine processes composing buffer
        │
        ▼
SinglishMapper trie lookup → "අම්මා"
        │
        ▼
text_inject.py backspaces + injects Unicode
        │
        ▼
"අම්මා" appears in active window
```

### How Mobile Sync Works

```
Phone (browser)  ──QR scan──►  PC (SinType)
                               │
                          Flask server
                          Socket.IO
                               │
                    Keystrokes stream to PC
                               │
                    remote_injector.py
                               │
                    Text injected to active window
```

-----

## Tech Stack

|Layer         |Technology                 |
|--------------|---------------------------|
|UI Framework  |`customtkinter` + `pystray`|
|Input Capture |`pynput`                   |
|Text Injection|`Win32 API` (pywin32)      |
|Mobile Server |`Flask` + `Flask-SocketIO` |
|License Crypto|`cryptography` (Fernet)    |
|Cloud Backend |`Supabase`                 |
|QR Generation |`qrcode`                   |
|Packaging     |`PyInstaller`              |
|Notifications |`plyer`                    |

-----

## License

SinType is **free to use**. A 30-day renewable license key is required to ensure you always receive the latest updates.

**→ [Generate your free key](https://sintype.lk/download)**

The license key system exists to:

- Notify you about important updates and new versions
- Ensure you are running a stable, supported build

There is no paid tier. SinType will always be free.

-----

## Privacy

SinType is built with privacy as a core principle:

- ✅ All keystroke processing happens **locally on your PC**
- ✅ Typing data is **never sent to the internet**
- ✅ Mobile sync works over **local Wi-Fi only** — no cloud relay
- ✅ File sharing is **peer-to-peer** on your local network
- ✅ License validation is the **only** external network call

-----

## Contributing

SinType is developed and maintained by a solo developer.  
Bug reports, feature suggestions, and feedback are welcome.

- 🐛 **Bug Report:** [sintype.lk/feedback](https://sintype.lk/feedback)
- 💬 **Discussion:** [sintype.lk/faq](https://sintype.lk/faq)
- 📧 **Contact:** [support@sintype.lk](mailto:support@sintype.lk)

-----

## Release Notes

### v2.0.0 (Latest)

- ✅ Built-in Local Web Server for mobile remote control
- ✅ Wireless touchpad & keyboard from phone via QR
- ✅ Mobile-to-PC file sync over local network
- ✅ Switch between Unicode, Legacy FM Abhaya, and English from phone
- ✅ Improved real-time conversion engine
- ✅ Redesigned floating toolbar

### v1.x

- Initial release with real-time Singlish to Unicode conversion
- Word mode with manual hotkey trigger
- Custom mapping support
- System tray integration

-----

## About

SinType was built by an 18-year-old Sri Lankan A/L student with a simple goal — to make typing Sinhala on Windows effortless for **designers, content creators, and everyday users** who deserve great local software.

> *“Sri Lankan users deserve tools built for them.”*

-----

<div align="center">

**[sintype.lk](https://sintype.lk)** · Built with ❤️ in Sri Lanka

</div>
