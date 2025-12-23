Here are clean **step-by-step Fedora GNOME notes** (copy into Notion). This is exactly what we did in our chat: prerequisites → install bridge → install via Chrome → toggle ON → (logout if needed).

---

# Fedora GNOME Extensions Setup Notes (Dash-to-Dock + Desktop Icons)

## Goal

Install GNOME Shell extensions on Fedora so that:

* You can add **Dash-to-Dock** (macOS-like dock)
* You can enable **Desktop icons + right-click → New Folder** (Windows/Mint-like)
* You can manage these extensions locally from Fedora

---

## 0) What you must understand (1 line)

Extensions are installed from **GNOME Extensions website**, but they become active on your Fedora because your browser talks to a local service (`gnome-browser-connector`).

---

## 1) Prerequisites (Fedora side)

### 1.1 Install Extensions Manager app (local GUI)

```bash
sudo dnf install gnome-extensions-app
```

This app helps you **enable/disable/configure** extensions after they’re installed.

### 1.2 Install browser connector (bridge between browser ↔ GNOME)

```bash
sudo dnf install gnome-browser-connector
```

✅ If Fedora says “already installed”, that’s fine.

---

## 2) Browser side (Chrome)

### 2.1 Install Chrome GNOME Shell Integration extension

Install this in Chrome:

```text
https://chromewebstore.google.com/detail/gnome-shell-integration/
```

This is required so the website toggle can install extensions into Fedora.

---

## 3) Install Dash-to-Dock (Dock like macOS)

### 3.1 Open Dash-to-Dock extension page

```text
https://extensions.gnome.org/extension/307/dash-to-dock/
```

### 3.2 Enable it

* On top-right, toggle **OFF → ON**
* Confirm **Install**

### 3.3 If it asks for “Shell version”

Don’t guess. Check your GNOME Shell version:

```bash
gnome-shell --version
```

Pick the same major version (45/46/47…) on the website dropdown.

### 3.4 Configure Dock (recommended settings)

Open **Extensions** app → find **Dash to Dock** → ⚙️ settings:

* Position: **Bottom**
* Alignment: **Center**
* Panel mode: **OFF**
* Intelligent auto-hide: **ON**
* Show Desktop button: **ON** ⭐

(Optional) Keyboard shortcut for “Show Desktop”:

```bash
gsettings set org.gnome.desktop.wm.keybindings show-desktop "['<Super>d']"
```

---

## 4) Enable Desktop right-click “New Folder” (Desktop Icons)

### 4.1 Why this is needed

On Fedora GNOME, the **desktop is not a real folder** by default, so desktop right-click shows only:

* Change Background
* Display Settings
* Settings

To get Windows/Mint-style desktop behavior, install **Desktop Icons NG (DING)**.

### 4.2 Install Desktop Icons NG (DING)

Open:

```text
https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/
```

Toggle **OFF → ON** → confirm **Install**

### 4.3 IMPORTANT: Log out / Log back in

After installing DING:

* **Log out** once
* Log back in

Now desktop supports:

* Desktop icons
* Right-click desktop → **New Folder**
* Drag/drop on desktop

---

## 5) Where “New Folder” exists without any extension (FYI)

Inside **Files app** (Nautilus):

* Right-click on **empty space** → New Folder
* Shortcut:

```text
Ctrl + Shift + N
```

---

## 6) Troubleshooting checklist

### 6.1 Website toggle doesn’t work / no toggle appears

* Make sure **Chrome GNOME Shell Integration** is installed
* Make sure Fedora package is installed:

```bash
sudo dnf install gnome-browser-connector
```

* Log out / log in once, then retry

### 6.2 Extension installed but not visible

Open **Extensions** app and ensure it’s toggled **ON**.

### 6.3 Confirm installed extensions from terminal

```bash
gnome-extensions list
```

---

## 7) Optional cleanup (if you installed gesture tools like touchegg earlier)

If you’re not using touchegg/touche on Wayland, you can remove:

```bash
sudo systemctl disable touchegg --now
sudo dnf remove touchegg
flatpak uninstall com.github.joseexposito.touche
```

---

If you want, tell me which Fedora/GNOME version you’re on (`gnome-shell --version`) and I’ll suggest the **best 5 safe extensions** for a Node/React dev setup (no glitches).
