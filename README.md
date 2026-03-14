<div align="center">

# 🔴 TRINETRA
### ESP32 Surveillance System

![Version](https://img.shields.io/badge/version-3.2-dc2626?style=for-the-badge)
![Platform](https://img.shields.io/badge/ESP32--CAM-AI--Thinker-0f172a?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-10b981?style=for-the-badge)
![UI](https://img.shields.io/badge/UI-Immersive_v3.2-dc2626?style=for-the-badge)

**Enterprise-grade surveillance solution with immersive stream-first web interface**

[Features](#-key-features) • [Installation](#-installation) • [Quick Start](#-quick-start) • [API](#-api-reference) • [Documentation](#-documentation)

---

</div>

## 📋 Overview

**TRINETRA** (Sanskrit: त्रिनेत्र, meaning "three eyes") is a cutting-edge, production-ready surveillance system built on the ESP32-CAM platform. Featuring a revolutionary **immersive stream-first web interface** with professional red theme, floating glassmorphic controls, and zero-configuration WiFi management.

### 🎯 Design Philosophy

- **Stream-First**: Full viewport video display with overlay controls
- **Zero Friction**: No code edits needed for WiFi configuration  
- **Professional UI**: Modern red theme with glassmorphism and curved edges
- **Mobile-Ready**: Responsive design optimized for all screen sizes
- **Accessible Anywhere**: Dual WiFi modes (Station + Access Point)

### 🔑 What Makes Trinetra Different

| Feature | Trinetra v3.2 | Typical Solutions |
|---------|---------------|-------------------|
| **UI Design** | Immersive stream-first, professional red theme | Basic HTML forms |
| **WiFi Setup** | Web-based scan & connect (no code) | Hard-coded credentials |
| **Controls** | Floating glassmorphic dock, real-time feedback | Static buttons |
| **Stream Display** | Full-screen with curved edges | Small fixed-size iframe |
| **Notifications** | Minimal auto-hiding pill | Disruptive alerts |
| **Camera Adjustments** | Live sliders with instant preview | Refresh-required forms |
| **Accessibility** | ARIA labels, keyboard shortcuts, **physical button** | Mouse-only |

---

## ✨ Key Features

### 🎥 Video Streaming & Recording
- **Real-time MJPEG streaming** on dedicated port (81) with sub-100ms latency
- **Immersive full-viewport display** with curved edges (20px radius)
- **Dynamic resolution switching** (QQVGA → SXGA) with instant reload
- **PSRAM-optimized dual frame buffer** for buttery-smooth playback
- **Adjustable JPEG quality** (4-63) with real-time compression control
- **Live FPS monitoring** with total frame counter
- **🆕 Video recording to SD card** with MJPEG format (`video_00001.mjpeg`)
- **🆕 Live recording indicator** with frame counter and duration timer
- **🆕 Simultaneous streaming & recording** without interruption

### 📸 Photo Capture
- **Instant browser download** with shutter flash animation
- **SD card storage** with auto-incrementing filenames (`trinetra_00001.jpg`)
- **Visual feedback system**: Green glow (success) / Red glow (error)
- **Graceful degradation**: Works without SD card
- **Flash LED control** with animated glow effect
- **🆕 Physical shutter button** — Capture photos with hardware button (GPIO 13)
- **🆕 Flash blink indicator** — LED blinks during capture for visual confirmation
- **🆕 Status feedback** — Double-blink on success / Triple-blink on error

### 💾 SD Card Management
- **🆕 Real-time storage monitoring** (total, used, free space in GB)
- **🆕 Usage percentage display** with color-coded progress bar
- **🆕 Visual warnings** when storage is nearly full (>75% yellow, >90% red)
- **🆕 Automatic space calculation** refreshed every 3 seconds
- **🆕 Gallery browser** (view all saved photos and videos from web interface)
- **🆕 File preview & download** (click to view photos or download videos)
- **🆕 Delete files** (individual or bulk deletion from gallery)
- **Supports FAT32 formatted cards** (Class 10 recommended)

### 🎨 Professional Web Interface v3.0

#### Design & Aesthetics
- **Deep slate background** (`#060a11`) with professional red accents (`#dc2626`)
- **Curved stream container** with 8px margins and subtle shadow
- **Floating glassmorphic control dock** with 24px blur backdrop
- **Gradient buttons** with hover scale effects and glow animations
- **Minimal notification pill** (auto-hides in 2.2s)
- **Shutter flash animation** on capture (no disruptive toasts)

#### Layout & Navigation
- **Stream-first hero layout**: Video fills 100% viewport height
- **Floating control bar**: Positioned at bottom with rounded dock design (32px radius)
- **Slide-in drawers**: Settings, Monitor, WiFi, Gallery (transform-based smooth transitions)
- **Dual navigation**: Desktop appbar icons + Mobile bottom nav
- **Responsive breakpoints**: Mobile (<640px), Tablet, Desktop

#### Controls & Interactions
- **7 professional buttons**: Play/Stop (gradient), Capture, Save SD, LED Toggle, Resolution, Fullscreen
- **Button feedback**: 500ms color flash (green/red) on action completion
- **Real-time settings**: Quality, Brightness, Contrast, Saturation sliders
- **8 toggle switches**: AWB, AGC, AEC, H-Mirror, V-Flip, BPC, WPC, Lens Correction
- **Effects & WB dropdowns**: Negative, Grayscale, Sepia, Tints + WB modes
- **Keyboard shortcuts**: `Space` (toggle stream), `F` (fullscreen), `Escape` (close)

#### System Monitoring
- **8 stat cards** with color-coded progress bars:
  - Uptime (days, hours, minutes)
  - ESP32 chip temperature (°C)
  - Streaming FPS + total frames
  - WiFi signal strength (RSSI dBm) with quality label
  - Connected clients counter
  - Heap memory (free MB, usage %)
  - PSRAM (free MB, usage %)
  - **🆕 SD card details** (free space, total capacity, usage % with progress bar)
- **Auto-refresh**: 3-second interval when drawer open
- **🆕 Storage warnings**: Visual alerts when SD card is >75% full

### 📡 Advanced WiFi Manager

#### Zero-Configuration Setup
- **Web-based interface**: No code editing required
- **Network scanner**: Visual list with signal strength indicators
- **One-click connection**: Select network → Enter password → Connect
- **Open WiFi support**: Connects to unsecured networks automatically
- **Credential persistence**: Saved to flash memory (NVP)
- **Auto-reconnect**: Attempts reconnection on dropout
- **Status monitoring**: Connection state, IP address, saved credentials
- **Reset option**: Clear saved WiFi with confirmation

#### Dual Mode Architecture
- **Station Mode (STA)**: Connects to existing WiFi infrastructure
- **Access Point Mode (AP)**: Broadcasts standalone network
  - SSID: `Trinetra` (customizable)
  - Password: `88888888` (8+ characters)
  - Static IP: `1.2.3.4` (memorable)
  - Gateway: Provides internet to connected clients
- **Simultaneous operation**: Both modes active at once
- **Fallback behavior**: AP always available even if STA fails
- **mDNS support**: Access via `http://trinetra.local`

### ⚡ Performance & Optimization

- **PSRAM utilization**: ~4MB allocated for frame buffers
- **Frame grabbing**: `CAMERA_GRAB_LATEST` mode
- **Memory efficient**: Minimal heap usage (~80KB free)
- **OTA support**: Wireless firmware updates (password-protected)
- **Watchdog protection**: Auto-reboot on crashes
- **Clean codebase**: Modular structure with detailed comments

---

## 🛠️ Hardware Requirements

### Essential Components

| Component | Specification | Notes |
|-----------|---------------|-------|
| **Microcontroller** | ESP32-CAM (AI-Thinker) | Other variants supported via `board_config.h` |
| **Camera** | OV2640 (2MP) | Included with ESP32-CAM modules |
| **Memory** | PSRAM (4MB) | Required for dual frame buffer |
| **Programmer** | USB-to-Serial adapter | FTDI, CP2102, or CH340G |
| **Power Supply** | 5V @ 500mA+ | Stable voltage critical for WiFi |

### Optional Accessories

- **microSD card** (FAT32, Class 10 recommended) for photo storage
- **External WiFi antenna** (with uFL connector) for extended range
- **3D printed case** for mounting and protection
- **USB power bank** for portable operation
- **🆕 Momentary push button** (for physical shutter trigger)

---

## 📦 Installation

### Prerequisites

- **Arduino IDE** 1.8.19+ or **PlatformIO**
- **ESP32 board support** 2.0.0+
- **Python** (for esptool, included with Arduino ESP32)

### Step 1: Arduino IDE Setup

#### Install ESP32 Core

1. Open **Arduino IDE**
2. Navigate to **File → Preferences**
3. Add to **Additional Board Manager URLs**:
   ```
   https://dl.espressif.com/dl/package_esp32_index.json
   ```
4. Open **Tools → Board → Boards Manager**
5. Search `esp32` → Install **esp32 by Espressif Systems** (v2.0.0+)

#### Configure Board Settings

Navigate to **Tools** menu:

| Setting | Value |
|---------|-------|
| **Board** | `AI Thinker ESP32-CAM` |
| **Partition Scheme** | `Huge APP (3MB No OTA/1MB SPIFFS)` |
| **PSRAM** | `Enabled` |
| **CPU Frequency** | `240MHz` |
| **Flash Frequency** | `80MHz` |
| **Upload Speed** | `115200` |

### Step 2: Download Project

**Option A: Git Clone**
```bash
git clone https://github.com/yourusername/trinetra.git
cd trinetra
```

**Option B: Direct Download**
1. Download ZIP from GitHub
2. Extract to `Documents/Arduino/trinetra/`

### Step 3: Hardware Wiring

#### Programming Mode

Connect USB-to-Serial adapter to ESP32-CAM:

| FTDI/Serial | ESP32-CAM | Notes |
|-------------|-----------|-------|
| 5V | 5V | Ensure stable 500mA+ supply |
| GND | GND | Common ground essential |
| RX | U0T (TX) | Cross connection required |
| TX | U0R (RX) | Cross connection required |

**Flash Mode**: Connect **GPIO 0 to GND** before powering on

**Run Mode**: Disconnect **GPIO 0 from GND** and press **RST** button

#### 🆕 Physical Shutter Button (Optional)

For hardware photo capture without web browser access:

| Component | ESP32-CAM Pin | Notes |
|-----------|---------------|-------|
| **Momentary Button** | GPIO 13 → GND | Internal pull-up enabled |

**Wiring**:
1. Connect one side of push button to **GPIO 13**
2. Connect other side to **GND**
3. No external resistor needed (internal pull-up used)

**Operation**:
- Press button to capture photo to SD card
- Flash LED blinks during capture (150ms)
- **Success**: Double-blink confirmation
- **Error**: Triple-blink (no SD card)
- Debounced automatically (300ms)

### Step 4: Upload Firmware

1. Open `trinetra.ino` in Arduino IDE
2. **Connect GPIO 0 to GND** (enter flash mode)
3. Power on ESP32-CAM (plug in USB adapter)
4. Select correct **Port** in **Tools → Port**
5. Click **Upload** (⬆️ arrow button)
6. Wait for compilation (~90 seconds) and upload (~30 seconds)
7. **Disconnect GPIO 0 from GND**
8. Press **RST** button

---

## 🚀 Quick Start

### First Boot (WiFi Configuration)

#### Step 1: Connect to Trinetra AP

1. Open WiFi settings on your phone/laptop
2. Look for network: **`Trinetra`**
3. Connect using password: **`88888888`**
4. Wait for captive portal popup (opens automatically)
   - If not auto-opened, navigate to `http://1.2.3.4`

#### Step 2: Configure Home WiFi (Optional)

1. In web interface, tap **WiFi** icon
2. Tap **Scan & Connect** button
3. Wait 2-3 seconds for network scan
4. **Select your WiFi network** from the list
5. **Enter password** if required
6. Tap **Connect** button
7. Note the IP address shown on success

#### Step 3: Access Methods

| Method | URL | Use Case |
|--------|-----|----------|
| **AP Direct** | `http://1.2.3.4` | Always works, no router needed |
| **mDNS** | `http://trinetra.local` | Convenient, works on same network |
| **Home WiFi IP** | `http://192.168.x.x` | Shown in Serial Monitor & WiFi tab |

### Using the Interface

#### Control Bar (Floating Dock)

| Button | Icon | Function | Shortcut |
|--------|------|----------|----------|
| **Play/Stop** | ▶️ / ⏹️ | Start/stop live stream | `Space` |
| **🆕 Record** | 🔴 / ⏹️ | Start/stop video recording | - |
| **Capture** | 📷 | Take photo & download | - |
| **Save SD** | 💾 | Capture to SD card | - |
| **LED** | 💡 | Toggle flash LED | - |
| **Resolution** | Dropdown | QQVGA → SXGA | - |
| **Fullscreen** | ⛶ | Immersive mode | `F` |

**Note**: Recording button appears only when stream is active

---

## 📡 API Reference

### Core Endpoints

| Endpoint | Method | Response | Description |
|----------|--------|----------|-------------|
| `/` | GET | HTML | Web interface |
| `/stream` | GET | MJPEG | Live video stream (port 81) |
| `/capture` | GET | JPEG | Capture single frame |
| `/save-photo` | GET | JSON | Save to SD card |
| `/control` | GET | Text | Set camera parameter |
| `/status` | GET | JSON | Camera settings |
| `/led` | GET | Text | LED control |
| `/system-stats` | GET | JSON | System monitoring |
| `/wifi-scan` | GET | JSON | Available networks |
| `/wifi-connect` | GET | JSON | Connect to WiFi |
| `/wifi-status` | GET | JSON | Connection status |
| `/wifi-reset` | GET | JSON | Clear credentials |
| **🆕 `/start-recording`** | GET | JSON | Start video recording |
| **🆕 `/stop-recording`** | GET | JSON | Stop recording & get stats |
| **🆕 `/recording-status`** | GET | JSON | Current recording state |
| **🆕 `/sd-info`** | GET | JSON | SD card space information |
| **🆕 `/list-files`** | GET | JSON | List all photos and videos |
| **🆕 `/download-file`** | GET | File | Download/view specific file |
| **🆕 `/delete-file`** | GET | JSON | Delete a file from SD card |

### Example API Calls

```bash
# Capture photo
curl "http://1.2.3.4/capture" --output photo.jpg

# Set resolution to VGA
curl "http://1.2.3.4/control?var=framesize&val=8"

# Get system stats
curl "http://1.2.3.4/system-stats"

# Toggle LED
curl "http://1.2.3.4/led?state=1"

# Start video recording
curl "http://1.2.3.4/start-recording"

# Stop recording and get file info
curl "http://1.2.3.4/stop-recording"

# Get SD card information
curl "http://1.2.3.4/sd-info"

# List all saved files
curl "http://1.2.3.4/list-files"

# Download a specific file
curl "http://1.2.3.4/download-file?name=trinetra_00001.jpg" --output photo.jpg

# Delete a file
curl "http://1.2.3.4/delete-file?name=video_00001.mjpeg"
```

---

## 🐛 Troubleshooting

### Camera Initialization

**❌ Error**: `Camera init failed`

**Solutions**:
- ✅ Enable PSRAM in Arduino IDE
- ✅ Select "Huge APP (3MB)" partition
- ✅ Reseat camera ribbon cable
- ✅ Use quality 5V power supply

### WiFi Issues

**❌ Can't connect to Trinetra AP**

**Solutions**:
- ✅ Password is `88888888` (8 characters)
- ✅ Wait 15-20 seconds after power-on
- ✅ Forget network and reconnect
- ✅ Check Serial Monitor for errors

### Stream Issues

**❌ Stream not loading**

**Solutions**:
- ✅ Use port 81: `http://1.2.3.4:81/stream`
- ✅ Reduce resolution to QVGA
- ✅ Move closer to WiFi AP
- ✅ Check camera lens cover removed

### 🆕 SD Card & Recording Issues

**❌ SD card not detected**

**Solutions**:
- ✅ Format as FAT32 (not exFAT or NTFS)
- ✅ Use 32GB or smaller card (better compatibility)
- ✅ Check card is fully inserted
- ✅ Try different microSD card (some brands incompatible)
- ✅ Check Serial Monitor for SD initialization errors

**❌ Recording won't start**

**Solutions**:
- ✅ Start streaming first (recording requires active stream)
- ✅ Ensure SD card has sufficient free space
- ✅ Check SD card isn't write-protected
- ✅ Verify SD card is mounted (check Monitor drawer)
- ✅ Format card and try again

**❌ Recording files won't play**

**Solutions**:
- ✅ Use VLC Media Player (best MJPEG support)
- ✅ Try converting to MP4: `ffmpeg -i video_00001.mjpeg -c:v libx264 output.mp4`
- ✅ Ensure recording wasn't interrupted while saving
- ✅ Check file size is > 0 bytes

### 🆕 Physical Button Issues

**❌ Button not working**

**Solutions**:
- ✅ Check wiring: Button between GPIO 13 and GND
- ✅ Verify SD card is inserted (button only saves to SD)
- ✅ Press button firmly (300ms debounce)
- ✅ Watch flash LED for blink pattern feedback
- ✅ Check Serial Monitor for `[BTN]` messages

**❌ Button triggers multiple captures**

**Solutions**:
- ✅ This is normal (debounce prevents rapid firing)
- ✅ Wait 300ms between presses
- ✅ Use better quality button (no bouncing contacts)
- ✅ Check wiring isn't loose or intermittent

---

## 🔐 Security

### Current Status

| Feature | Status | Risk |
|---------|--------|------|
| **Encryption** | ❌ HTTP only | 🔴 High |
| **Authentication** | ❌ None | 🔴 High |
| **AP Password** | ✅ WPA2 | 🟢 Low |
| **OTA Password** | ✅ Protected | 🟢 Low |

### Recommendations

✅ Change default AP password  
✅ Use on isolated network  
✅ Do not expose to internet  
✅ Add VPN for remote access  

---

## 📚 Documentation

### Project Structure

```
trinetra/
├── trinetra.ino          # Main sketch + button handler
├── app_httpd.cpp         # HTTP server + API endpoints
├── camera_index.h        # Web UI (v3.1)
├── board_config.h        # Board selection + button GPIO
├── camera_pins.h         # Pin definitions
└── README.md             # Documentation
```

---

## 🗺️ Roadmap

### Version 4.0 (Planned)

- [ ] HTTPS support
- [ ] HTTP Basic Authentication
- [ ] Motion detection
- [ ] Time-lapse mode
- [ ] Video recording to SD
- [ ] MQTT integration
- [ ] Mobile apps

---

## 🤝 Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create feature branch
3. Commit changes
4. Open Pull Request

---

## 📄 License

MIT License - Copyright (c) 2026 Trinetra Project

---

## 🙏 Acknowledgments

- **ESP32 Arduino Core** by Espressif Systems
- **Arduino IDE** community
- **OV2640 drivers** from ESP-IDF

---

## 👨‍💻 Developer

<div align="center">

**Developed by Sakshyam Bastakoti**

[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github)](https://github.com/sakshyambastakoti)
[![Email](https://img.shields.io/badge/Email-Contact-dc2626?style=for-the-badge&logo=gmail)](mailto:sakshyam@example.com)

*Embedded Systems Engineer | IoT Enthusiast | Open Source Contributor*

</div>

---

## 📬 Support

- 🐛 **Issues**: GitHub Issues
- 💡 **Features**: GitHub Discussions  
- 📧 **Email**: support@trinetra.local

---

## 📊 Changelog

### v3.2 — Physical Shutter Button (March 2026)

**📷 Hardware Photo Capture**
- Physical button support on GPIO 13
- Capture photos without web browser access
- Flash LED blinks during capture (visual indicator)
- Double-blink on successful save
- Triple-blink error indication (no SD card)
- 300ms debounce protection
- Interrupt-driven (zero CPU overhead)
- Shares filename counter with web captures
- Non-blocking operation (doesn't affect streaming)

**🔧 Technical Details**
- Uses internal pull-up resistor
- Interrupt Service Routine (IRAM_ATTR)
- Safe for concurrent web captures
- Works in parallel with recording
- No impact on camera performance

### v3.1 — Video Recording & SD Card Management (February 2026)

**🎥 Video Recording**
- Record video to SD card in MJPEG format
- Start/stop recording button in control bar
- Live recording indicator badge with timer
- Simultaneous streaming and recording
- Auto-increment file naming (`video_00001.mjpeg`)
- Frame counter during recording
- Recording statistics on stop (size, frames, duration)

**💾 SD Card Monitoring**
- Real-time storage information display
- Free space and total capacity (GB)
- Usage percentage with progress bar
- Color-coded warnings (green → yellow → red)
- Auto-refresh every 3 seconds
- SD card availability status
- Maximum space utilization alerts
- **Gallery browser** with thumbnail grid view
- View and download saved photos and videos
- Individual and bulk file deletion

**🔌 API Enhancements**
- `/start-recording` - Begin video capture
- `/stop-recording` - End recording & get stats
- `/recording-status` - Current recording state
- `/sd-info` - Storage space details
- `/list-files` - Browse all saved media
- `/download-file` - Retrieve specific file
- `/delete-file` - Remove file from SD card
- Enhanced `/system-stats` with SD & recording data

**🐛 Improvements**
- Automatic recording stop when stream ends
- Graceful error handling for SD card issues
- Better notification messages for recording events
- Recording state persistence across operations

### v3.0 — Immersive Stream-First UI (February 2026)

**🎨 Interface Redesign**
- Complete UI overhaul with stream-first layout
- Professional red theme (`#dc2626`) 
- Curved stream container (20px radius)
- Floating glassmorphic control dock

**✨ New Features**
- Gradient buttons with glow effects
- Color-coded feedback (green/red)
- Shutter flash animation
- Minimal notification pill
- Stream timer (MM:SS)
- Resolution switching without restart

**🎛️ Control Improvements**
- 7 professional buttons
- LED animated glow when active
- Real-time setting previews
- Keyboard shortcuts

**📱 Responsive Enhancements**
- Mobile bottom nav
- Desktop appbar
- Slide-in drawers
- Backdrop overlay

### v2.0 — Professional UI (January 2026)

- Slate/cyan theme
- Tabbed navigation
- SVG icons
- System monitoring
- WiFi Manager

### v1.0 — Initial Release (December 2025)

- MJPEG streaming
- Photo capture
- Dual WiFi mode
- Basic web interface

---

<div align="center">

### ⭐ Star this repository if you find it useful! ⭐

**Built with ❤️ for the maker community**

*Trinetra — Three Eyes Watching*

---

![Footer](https://img.shields.io/badge/ESP32-Powered-0f172a?style=for-the-badge)
![Footer](https://img.shields.io/badge/Open_Source-Forever-10b981?style=for-the-badge)
![Footer](https://img.shields.io/badge/Made_with-Arduino-dc2626?style=for-the-badge)

</div>
