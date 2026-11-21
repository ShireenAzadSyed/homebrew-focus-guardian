# 🍎 Focus Guardian on macOS

Complete installation, permission configuration, and management guide for macOS.

---

## 🚀 Installation Options

### Option 1: Official Homebrew Tap (Recommended)
```bash
# 1. Tap the repository
brew tap shireenazadsyed/focus-guardian https://github.com/ShireenAzadSyed/focus-guardian.git

# 2. Trust the formula (Required on macOS)
brew trust shireenazadsyed/focus-guardian

# 3. Install Focus Guardian
brew install focus-guardian

# 4. Start the 24/7 background service
brew services start focus-guardian
```

### Option 2: 1-Line Universal Curl Installer
```bash
curl -fsSL https://raw.githubusercontent.com/ShireenAzadSyed/focus-guardian/main/install.sh | bash
```

---

## 🛠️ Management CLI Commands

```bash
# Check service health and running processes
focus-guardian status

# Trigger in-place hot reload of rules and code (zero downtime)
focus-guardian reload

# Run in foreground test mode (view live tab intercepts in terminal)
focus-guardian start

# Lock daemon with root privileges (tamper-proof)
focus-guardian install-root

# Attempt shutdown (triggers 3-stage anti-tamper confirmation shield)
focus-guardian stop

# Uninstall service
focus-guardian uninstall
```

---

## 🔒 macOS Permissions & Automation

Focus Guardian operates natively using AppleScript application dictionaries (`Google Chrome`, `Safari`, `Brave Browser`, `Arc`, `Microsoft Edge`, `Opera`, `Vivaldi`).

### Granting Automation Permissions:
When first launched, macOS may prompt:
> *"Focus Guardian would like to control Google Chrome.app"*

Click **OK** to allow Focus Guardian to inspect active distraction tabs and redirect them.
If prompted again or to verify permissions:
1. Open **System Settings ➔ Privacy & Security ➔ Automation**.
2. Ensure **Focus Guardian** (or your Terminal / Python) has checkmarks next to your installed browsers.

---

## 🛡️ Anti-Tamper Protection

Running `focus-guardian install-root` installs Focus Guardian under `/Library/LaunchDaemons/com.focusguardian.daemon.plist` owned by `root:wheel`. It automatically restarts if killed via Activity Monitor and cannot be terminated without root authorization.

