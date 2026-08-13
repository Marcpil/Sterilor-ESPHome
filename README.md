![ESPHome](https://img.shields.io/badge/ESPHome-2026+-blue.svg)

![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Compatible-41BDF5.svg)

![License](https://img.shields.io/badge/License-MIT-green.svg)

## Requirements

- Home Assistant
- ESPHome
- ESP32
- Bluetooth Low Energy

## Contents

- Overview
- Features
- Hardware
- Dashboard
- Installation
- BLE protocol
- Roadmap
- License

# 🏊 Sterilor XP ESPHome

> Native ESPHome integration for Sterilor XP salt chlorinator and pH regulator using Bluetooth Low Energy (BLE).

![Dashboard](images/dashboard.png)

---

## ✨ Features

- ✅ Read pool water pH
- ✅ Read salt chlorinator production (%)
- ✅ Change production setpoint
- ✅ Monitor BLE connection status
- ✅ Native ESPHome integration
- ✅ Ready-to-use Mushroom dashboard
- ✅ Local communication only (no cloud)

## Supported hardware

- Sterilor XP Salt Chlorinator
- Sterilor XP pH Regulator
- ESP32 (Wi-Fi or Ethernet)
- Home Assistant
- ESPHome

## Dashboard

A complete Mushroom dashboard is included.

It provides:

- Pool water temperature
- Filtration status
- Water pH
- Chlorinator production
- Cell connection status
- pH regulator connection status
- Filtration controls
- Production setpoint adjustment

![Dashboard](images/dashboard.png)

## Repository structure

```
Sterilor-ESPHome/

├── esphome/
│   └── Sterilor_ESPHome_V1.0.1.yaml
│
├── dashboard/
│   └── dashboard_mushroom.yaml
│
├── docs/
│   └── installation.md
│
├── images/
│
├── protocol.md
│
└── README.md
```

## Installation

1. Install ESPHome.
2. Copy the provided YAML file.
3. Update the BLE MAC addresses of your Sterilor devices.
4. Compile and flash the ESP32.
5. Add the ESPHome device to Home Assistant.
6. Import the Mushroom dashboard.

Detailed installation instructions are available in:

```
docs/installation.md
```

## BLE protocol

The BLE protocol has been reverse engineered from real Sterilor devices.

Known features include:

- Production reading
- Production setpoint writing
- pH reading
- Device status monitoring

Technical details are available in:

```
protocol.md
```

## Roadmap

### Version 1.1

- pH setpoint writing
- RSSI monitoring
- Improved diagnostics

### Future

- Automatic BLE discovery
- Firmware compatibility improvements
- Additional Sterilor models

## Disclaimer

This project is **not affiliated with or endorsed by Sterilor**.

Sterilor is a trademark of its respective owner.

## License

MIT License.

## Acknowledgements

This project was developed through a collaborative effort combining:

- Bluetooth Low Energy reverse engineering
- ESPHome development
- Home Assistant integration
- Extensive real-world testing

The goal is to provide the Home Assistant community with a reliable and easy-to-use integration for Sterilor XP devices.
