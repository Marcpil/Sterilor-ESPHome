# Hardware Guide

This document describes the recommended hardware for the **Sterilor XP ESPHome** project.

---
| Feature                 | Wi-Fi | Ethernet |
| ----------------------- | :---: | :------: |
| Easy installation       |   ✅   |     ✅    |
| Stable connection       |   ⚠️  |     ✅    |
| Best for technical room |   ⚠️  |     ✅    |
| OTA Updates             |   ✅   |     ✅    |
---

# ESP32

The project has been developed using an ESP32 running ESPHome.

Both Wi-Fi and Ethernet models are supported.

Recommended specifications:

- Bluetooth Low Energy (BLE)
- ESP32
- 4 MB Flash minimum

---

# Recommended boards

## ⭐ Waveshare ESP32-S3-ETH

Recommended for permanent installations.

Advantages:

- Native Ethernet
- USB-C programming
- Excellent Bluetooth range
- Reliable network connection
- Ideal for technical rooms

---

## ESP32 DevKit

Also compatible.

Advantages:

- Low cost
- Easy to find
- Simple USB programming

Limitations:

- Wi-Fi only
- Requires good Wi-Fi coverage

---

# Ethernet or Wi-Fi?

## Ethernet (recommended)

Advantages

- Stable network connection
- No Wi-Fi interference
- Ideal for technical rooms
- Better long-term reliability

Recommended whenever an Ethernet connection is available.

---

## Wi-Fi

Works perfectly if:

- Wi-Fi signal is good
- ESP32 is installed close to the pool equipment

---

# Bluetooth

The ESP32 communicates with:

- Sterilor XP Salt Chlorinator
- Sterilor XP pH Regulator

using Bluetooth Low Energy (BLE).

No Internet connection is required.

---

# Recommended installation

```
                 Bluetooth

   Sterilor SEL  ◄────────────┐
                               │
   Sterilor pH   ◄────────────┤
                               │
                         ESP32
                               │
                     Wi-Fi / Ethernet
                               │
                     Home Assistant
```
<p align="left">
  <img src="/images/schema.png" width="600">
</p>
---

# ESP32 location

For best Bluetooth performance:

- Install the ESP32 inside or close to the technical room.
- Keep less than 5 meters from Sterilor devices whenever possible.
- Avoid metal enclosures.
- Keep the antenna unobstructed.

---

# Power supply

Use a stable 5 V USB power supply.

Recommended:

- 5 V
- 2 A minimum

---

# Tested hardware

| Device | Status |
|----------|--------|
| Waveshare ESP32-S3-ETH | ✅ Tested |
| ESP32 DevKit | ✅ Compatible |

---

# Sterilor devices

Currently supported:

- ✅ Sterilor XP Salt Chlorinator
- ✅ Sterilor XP pH Regulator

Future versions may support additional Sterilor products.

---

# Why Ethernet?

The project was originally developed for a pool technical room.

Ethernet provides:

- Better reliability
- Lower maintenance
- No Wi-Fi coverage issues
- Stable communication with Home Assistant

For this reason, Ethernet is recommended whenever possible.

---

# Need help?

If you are unsure which ESP32 to purchase, please open a GitHub Issue.

We will be happy to help.
