# KC868-A16 OI-6950 Modbus Bridge

ESPHome firmware for the **KinCony KC868-A16** that bridges up to 30 **OI-6950** gas
monitors to Home Assistant via RS485 Modbus RTU.

## What it does

- **Polls 16 gas channels** from an OI-6950 every 5 s over RS485 (Modbus RTU, 9600 8N1)
- **Reports to Home Assistant** via the native API (encrypted) and MQTT auto-discovery
- **Activates relay outputs Y01–Y16** automatically when the paired gas channel meets or
  exceeds the configurable alarm threshold (default 10 ppm)
- **Bluetooth proxy** – forwards BLE advertisements to Home Assistant over Ethernet/WiFi
- **Fleet-ready** – `name_add_mac_suffix: true` gives every unit a unique name so 30
  devices can share a single firmware image

## Hardware

| Component | Details |
|-----------|---------|
| Controller | KinCony KC868-A16 (ESP32-WROOM, LAN8720 Ethernet) |
| Gas monitor | OI-6950 (Modbus RTU slave, 9600 baud, address 1 by default) |
| RS485 pins | TX = GPIO13, RX = GPIO16 (on-board transceiver, no DE pin needed) |
| Relay outputs | 16 × MOSFET via PCF8574 (I²C 0x24/0x25) |
| Digital inputs | 16 × optocoupler via PCF8574 (I²C 0x22/0x21) |

## Register map

| Registers | Description | Source |
|-----------|-------------|--------|
| `0x21 + (ch-1)×2` | Channel ch gas reading (FP32, ppm) | PlanBRandom/teleproject |
| `6052–6053` | Supply voltage (FP32, V) | PlanBRandom/anjoytell |
| `6012` | Fault LED status | PlanBRandom/anjoytell |

## Quick start

1. Copy `secrets.yaml.example` to `secrets.yaml` and fill in your credentials.
2. Flash with [ESPHome](https://esphome.io/) or use the installer page (see GitHub Pages).
3. Set the OI-6950 Modbus address to match `modbus_address` (default `0x01`).
4. Wire RS485 A/B between the KC868-A16 terminal and the OI-6950.

## Related repositories

- [PlanBRandom/teleproject](https://github.com/PlanBRandom/teleproject) – radio receiver &
  Modbus bridge for OI-7530/7010 (register addresses used here)
- [PlanBRandom/anjoytell](https://github.com/PlanBRandom/anjoytell) – OI-6950/7010/9850
  Modbus register documentation and OI-6950 shipping roadmap

