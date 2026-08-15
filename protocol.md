# Sterilor XP BLE Protocol

This document describes the Bluetooth Low Energy (BLE) protocol currently understood by the project.

> **Important**
>
> This protocol has been reverse engineered from real Sterilor XP devices.
>
> It is **not** based on official documentation.

---

# Project history

The Sterilor XP salt chlorinator and pH regulator communicate through Bluetooth Low Energy.

At the beginning of this project, no public documentation describing the protocol was available.

The protocol was progressively discovered by:

- Bluetooth HCI captures
- nRF Connect
- ESPHome BLE notifications
- Python scripts
- Real-world validation

The objective was to understand the protocol well enough to build a complete native ESPHome implementation.

---

# Devices

The project currently supports two BLE devices.

| Device | Function |
|---------|----------|
| Sterilor XP Sel | Salt chlorinator |
| Sterilor XP pH | pH regulator |

---

# Communication

The ESP32 acts as a BLE Central.

Both Sterilor devices act as BLE Peripherals.

```
ESP32
   │
   ├──────── BLE ───────► Sterilor XP Sel
   │
   └──────── BLE ───────► Sterilor XP pH
```

Communication is performed using BLE notifications and BLE writes.

---

# Packet structure

Most notification packets follow the format:

| Byte | Description |
|------|-------------|
| 0 | Frame type |
| 1 | Reserved |
| 2 | Register |
| 3..n | Payload |

The register number determines the payload format.

---

# Known registers

## Register 0x14

Used by the salt chlorinator.

Provides:

- Current production (%)
- Device status

Payload:

```
01 00 14 xx xx xx xx xx xx
```

Currently decoded:

| Byte | Meaning |
|------|---------|
| 4 | Production (%) |
| 8 | Device status |

---

## Register 0x0B

Provides the measured pool pH.

Payload:

```
01 00 0B xx xx
```

Current decoding:

```
raw = ((byte3 & 0x7F) << 8) | byte4

pH = raw / 1000
```

---

# Writing commands

The project currently supports writing:

- Salt production setpoint

The ESP32 sends BLE write commands directly to the Sterilor salt chlorinator.

---

# Connection monitoring

The firmware continuously monitors the BLE connection status.

Two binary sensors are exposed:

- Salt Cell connected
- pH Regulator connected

This allows Home Assistant to detect communication failures.

---

# Current capabilities

Implemented:

- Read production
- Read pH
- Write production setpoint
- Connection monitoring

Not yet implemented:

- pH setpoint writing
- Advanced diagnostics
- Additional registers

---

# Reverse engineering methodology

The protocol was discovered using several complementary tools.

## Android

- Bluetooth HCI snoop log
- nRF Connect

## Linux

- Python
- Bleak
- Wireshark
- tshark

## ESPHome

- BLE Client
- Notification decoding
- Real-time validation

Each decoded register was validated on a real Sterilor installation.

---

# Future work

Future versions may include:

- Additional BLE registers
- pH setpoint writing
- Diagnostic registers
- Firmware compatibility improvements

---

# Disclaimer

This document reflects the current understanding of the protocol.

Some registers may remain undocumented or partially understood.

Contributions and discoveries are welcome.
