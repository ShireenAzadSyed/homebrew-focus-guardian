# 🐧 Focus Guardian on Linux

Complete installation, background service setup, and desktop environment guide for Linux (Ubuntu, Debian, Fedora, Arch, Mint, Pop!_OS).

---

## 🚀 Installation Options

### Option 1: 1-Line Universal Installer (Recommended)
```bash
curl -fsSL https://raw.githubusercontent.com/ShireenAzadSyed/focus-guardian/main/install.sh | bash
```
*Automatically detects systemd, installs the user service, and links `focus-guardian` into `/usr/local/bin`.*

### Option 2: Debian / Ubuntu (.deb)
```bash
sudo dpkg -i focus-guardian_latest_amd64.deb
focus-guardian start
```

### Option 3: Arch Linux (AUR)
```bash
yay -S focus-guardian
```

---

## 🛠️ Management Commands

```bash
# Check service health and running processes
focus-guardian status
# or native systemd:
systemctl --user status focus-guardian

# Trigger hot reload of rules (zero downtime)
focus-guardian reload

# Run in foreground interactive mode
focus-guardian start

# Stop service
focus-guardian stop
# or
systemctl --user stop focus-guardian
```

---

## 🌐 Supported Linux Browsers

Focus Guardian operates natively across both X11 and Wayland desktops for:
* **Google Chrome & Chromium**
* **Mozilla Firefox**
* **Brave Browser**
* **Microsoft Edge for Linux**
* **Opera**
* **Vivaldi**

---

## ⚙️ How it Works on Linux

1. **X11 Window Introspection:**
   Uses `xdotool` and `xprop` to query `_NET_ACTIVE_WINDOW` and `_NET_WM_NAME` to detect active browser tab titles with sub-millisecond response times.
2. **Wayland & AT-SPI2 Accessibility:**
   Connects to the desktop accessibility bus (`org.a11y.atspi`) over D-Bus to inspect accessible elements without browser extensions.
3. **Tab Redirection & Tab Close:**
   Navigates the browser to `http://127.0.0.1:8989/blocked` and closes tabs using native keystroke injection (`Ctrl + W`) via `xdotool` or `ydotool`.
4. **Desktop Notifications:**
   Uses standard `notify-send` via libnotify.

---

## 🛡️ Anti-Tamper Protection

Running `focus-guardian install-root` on Linux creates a system-wide root daemon in `/etc/systemd/system/focus-guardian.service`. Non-root users cannot kill or disable the service without `sudo` privileges.

