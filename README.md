# FRMM — Shift Light Controller

**Real-time RPM shift light controller for the Logitech G923 racing wheel.**  
Works with Forza Horizon 5 and Forza Horizon 6 via UDP telemetry.

[![Demo on YouTube](https://img.shields.io/badge/Demo-YouTube-red.svg)](https://youtu.be/J_oqmbScInI)
[![Microsoft Store](https://img.shields.io/badge/Download-Microsoft%20Store-blue.svg)](https://apps.microsoft.com/detail/9MTJ39ZLGMHD)

---

## Features

- **Instant LED response** — Direct HID++ 2.0 communication (~2 ms latency), bypassing G HUB's processing ceiling
- **Adaptive RPM calibration** — Learns each car's actual shift point automatically; no manual setup per car
- **Progressive LED fill** — 10 LEDs light up gradually as RPM rises; all 10 blink at shift point
- **Live dashboard** — Real-time display of speed, throttle, brake, boost, tire temperatures, and gear
- **Configurable thresholds** — Adjust LED start %, shift point %, and blink speed from the UI
- **Dual-mode LED sync** — HID direct write + G HUB WebSocket sync to prevent G HUB from overriding LED state
- **Three themes** — Dark, Light, and Forza Horizon 6 style
- **Bilingual** — English and Spanish interface
- **Tachometer display** — Animated RPM gauge with configurable styles
- **Lightweight** — Single portable `.exe`, no installation required

---

## Requirements

- Windows 10/11 (64-bit)
- Logitech G923 Xbox racing wheel
- **Logitech G HUB** must be running (initializes the wheel's LED feature at boot)
- Forza Horizon 5 or Forza Horizon 6
- UDP telemetry enabled in-game (see Setup below)

---

## Setup

### 1. Enable UDP telemetry in Forza Horizon

1. Open **Settings → HUD and Gameplay**
2. Enable **Data Out**
3. Set **Data Out IP Address** to your PC's local IP (or `127.0.0.1` if running on the same machine)
4. Set **Data Out Port** to `12350` (default, configurable in the app)

### 2. Run FRMM

1. Make sure **Logitech G HUB** is running
2. Launch **FRMM Shift Light Controller**
3. Verify the port matches your Forza telemetry settings
4. Click **Start**
5. Drive — LEDs will respond immediately to RPM

---

## How it works

FRMM receives UDP packets from Forza Horizon containing live engine data (RPM, speed, throttle, brake, gear, tire temps). It maps the current RPM to one of 10 LED levels and sends a HID++ 2.0 command directly to the G923's LED controller interface, achieving ~2 ms end-to-end latency.

The adaptive calibration tracks the peak RPM seen during a session and uses that (plus 5% headroom) as the effective maximum, so the full LED range is always used regardless of the car's engine ceiling.

---

## Configuration

| Setting | Description | Default |
|---------|-------------|---------|
| Port | UDP port Forza sends telemetry to | 12350 |
| LED Start % | RPM % at which LEDs begin lighting up | 50% |
| Shift Point % | RPM % at which all LEDs blink | 87% |
| Blink Speed | LED blink frequency at shift point (Hz) | 15 Hz |

---

## Support & Feature Requests

Found a bug or have an idea for a new feature? Feel free to:

- **Open an issue** on this repository — [github.com/Ricardom-m/frmm-shift-light-controller/issues](https://github.com/Ricardom-m/frmm-shift-light-controller/issues)
- **Send an email** to: ricardom_m@outlook.es

All suggestions are welcome — whether it's support for other wheels, new dashboard data, different LED patterns, or anything else.

## Donate

If you find FRMM useful, you can support development via PayPal:

[![Donate](https://img.shields.io/badge/Donate-PayPal-blue.svg)](https://paypal.me/RichardPM20)

---

## License

Personal use. Not affiliated with Logitech or Microsoft/Turn 10/Playground Games.
