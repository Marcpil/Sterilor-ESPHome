# Installation Guide

This guide explains how to install the **Sterilor XP ESPHome** integration in Home Assistant. Estimated installation time: 10–15 minutes

---

# Prerequisites

Before starting, make sure you have:

- Home Assistant
- ESPHome add-on installed
- An ESP32 (Wi-Fi or Ethernet)
- A Sterilor XP Salt chlorinator
- (Optional) A Sterilor XP pH regulator
- Bluetooth available on the ESP32

---

# 1. Download the project

Download the latest release from GitHub.

```
Sterilor_ESPHome_V1.0.1.yaml
```

---

# 2. Create a new ESPHome device

Open **ESPHome**

Click

**New Device**

Create a new ESP32 device.

---

# 3. Replace the generated YAML

Replace the generated configuration with:

```
Sterilor_ESPHome_V1.0.1.yaml
```

---

# 4. Configure your Wi-Fi

Edit the Wi-Fi section.

```yaml
wifi:
  ssid: "YOUR_WIFI"
  password: "YOUR_PASSWORD"
```

---

# 5. Find the BLE MAC addresses

You need the Bluetooth MAC addresses of your Sterilor devices.

Using the nRF Connect application you should discover something similar to:

```
Sterilor_Sel_xxxx
```

and

```
Ph-On_xxxx
```

Copy both MAC addresses.

---

# 6. Update the YAML

Replace the default MAC addresses.

Example:

```yaml
ble_client:

  - mac_address: AA:BB:CC:DD:EE:FF
    id: sterilor_sel

  - mac_address: 11:22:33:44:55:66
    id: sterilor_ph
```

---

# 7. Compile

Compile the project.

The firmware should compile without errors.

---

# 8. Flash the ESP32

Upload the firmware.

Once rebooted, the ESP32 should connect automatically to:

- Wi-Fi
- Home Assistant
- Sterilor devices

---

# 9. Add to Home Assistant

ESPHome should automatically discover the new device.

Click

**Add Integration**

---

# 10. Verify the entities

You should now see entities similar to:

- Pool pH
- Salt production
- Production setpoint
- Cell connectivity
- pH regulator connectivity

---

# 11. Import the dashboard

Copy

```
dashboard/dashboard_mushroom.yaml
```

into your Lovelace dashboard.

The dashboard will display:

- Water temperature
- Filtration
- Salt production
- Pool pH
- Device connectivity
- Filtration controls
- Production setpoint

---

# Troubleshooting

## No Bluetooth connection

Check:

- BLE MAC addresses
- Distance between ESP32 and Sterilor
- Bluetooth enabled on ESP32

---

## No entities appear

Verify:

- ESPHome device is online
- Home Assistant integration is loaded

---

## Production cannot be changed

Check that:

- BLE connection is active
- Sterilor is powered on

---

# Updating

When a new firmware version is released:

1. Download the new YAML
2. Recompile
3. Upload the firmware

Your Home Assistant entities will remain unchanged.

---

# Need help?

Please open an Issue on GitHub including:

- ESPHome version
- Home Assistant version
- ESP32 model
- Sterilor model
- Logs
