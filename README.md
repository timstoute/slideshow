# Decoupled HDMI Digital Signage Slideshow

A lightweight, web-based digital signage slideshow application designed for HDMI displays and TV screens. It independently cycles through a local folder of images and text overlay quotes loaded from a published Google Sheet or CSV.

---

## 🚀 Quick Start (Running Locally on macOS)

Opening HTML files directly from Finder (`file://` protocol) causes web browsers to block remote Google Sheets requests due to CORS security policies. 

Running a lightweight local web server is the most reliable way to run the slideshow:

1. Open **Terminal** on your Mac.
2. Run the following command:
   ```bash
   cd /Users/timstoute/Projects/slideshow && python3 -m http.server 8000
   ```
3. Open your browser to: **[http://localhost:8000](http://localhost:8000)**

---

## ⚙️ Setup & Configuration

### 1. Google Sheet (Text Overlay)
Create a Google Sheet with 2 columns:
- **Column A**: `Title`
- **Column B**: `Subtitle`

**Currently Configured Google Sheet CSV URL:**
```
https://docs.google.com/spreadsheets/d/e/2PACX-1vRE0zA9CCIbNCvq0iVxrA24CKg9aud-IJ-h6UkN2BtcVc0zADwi0bs9QoZvFwhu9bowJafPeleHnTNA/pub?output=csv
```

**Publishing Your Own Sheet to Web:**
1. Click **File** ➔ **Share** ➔ **Publish to web**.
2. Change *Web page* to **Comma-separated values (.csv)**.
3. Copy the URL and paste it into the **Settings Drawer [C]** inside the application.

### 2. Local Image Folder
- **Default Image Folder**: The app now automatically loads all images inside the project's local `images/` directory on startup! Simply drop new photos into `images/` and refresh.
- **Custom Folder / Drag & Drop**: Press `C` to open the Settings menu to pick a different folder on your computer, or **drag and drop** any image folder directly onto the browser screen.

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
| :--- | :--- |
| **`F`** | Toggle Native Fullscreen mode |
| **`L`** | Toggle Layout Style (Split Layout vs Floating Overlay) |
| **`Space`** | Pause / Resume slide transitions |
| **`➔` (Right Arrow)** | Skip to the next slide immediately |
| **`C`** | Toggle Settings & Configuration drawer |

---

## 📺 Connecting Your Laptop to a TV (No HDMI Port)

If your laptop lacks a built-in HDMI port and your TV is not a Smart TV, here are the best options to display the slideshow:

### Option A: USB-C / Thunderbolt to HDMI Adapter (Recommended)
- **Equipment**: USB-C to HDMI Adapter or Multiport Dongle (~$10–$15).
- **Setup**: Plug the adapter into your laptop's USB-C/Thunderbolt port and connect a standard HDMI cable from the adapter to your TV.
- **Why it's best**: 100% reliable, zero network dependency or lag, crisp 4K/1080p display, and perfect for dedicated digital signage.

### Option B: Google Chromecast (Best Wireless Option)
- **Equipment**: Google Chromecast or Chromecast with Google TV (~$30) plugged into the TV's HDMI port.
- **Setup**:
  1. Connect both your laptop and Chromecast to the same Wi-Fi network.
  2. Open **Google Chrome** browser on your laptop and navigate to `http://localhost:8000`.
  3. Click Chrome's 3-dot menu ➔ **Save and Share** (or **Cast...**) ➔ Select your **Chromecast**.
  4. Choose **Cast Tab** or **Cast Screen**, then press `F` for Fullscreen.

### Option C: Apple TV / AirPlay Streaming Stick
- **Equipment**: Apple TV box or an AirPlay-compatible streaming dongle plugged into the TV's HDMI port.
- **Setup**: Click **Control Center** in your Mac menu bar (top right) ➔ **Screen Mirroring** ➔ Select your Apple TV.

---

## 🌙 Preventing Screensaver & Display Sleep

To ensure your Mac screen never dims, locks, or goes into screensaver mode during a presentation:

### 1. Automatic Web Screen Wake Lock (Built-in)
The app now automatically requests a **Screen Wake Lock** via the browser whenever `index.html` is open. Keep the browser tab visible and active.

### 2. Built-in Mac Terminal Command (`caffeinate`)
macOS includes a built-in keep-awake tool called `caffeinate`. You can run it alongside your web server:
```bash
caffeinate -d
```
*(This prevents the display from sleeping for as long as Terminal is open).*

### 3. macOS System Settings
1. Open **System Settings** on your Mac.
2. Go to **Lock Screen**.
3. Set **Turn display off on power adapter when inactive** ➔ **Never**.
4. Set **Start Screen Saver when inactive** ➔ **Never**.
