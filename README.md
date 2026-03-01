# Crested Gecko Habitat Control Center

ESPHome firmware for the **KC868-A16** (ESP32) board configured as a full-featured crested-gecko habitat management system.

## What's included

- **30× DS18B20** one-wire temperature sensors with thermostat control
- **SHT30/SHT31** humidity sensors with auto-misting on low humidity
- **Day/Night lighting schedule** (UVB, ambient LED, night heat)
- **Misting system** – primary + backup pump with countdown timers and auto-mist
- **8-channel SSR module** for all high-voltage/high-current loads
- **Fan PWM speed control** with auto-boost on high humidity
- **Physical buttons** – Feed logged, Manual mist, Alarm dismiss
- **Alarm LEDs** (Red/Yellow/Green) + buzzer relay
- **Capacitive substrate moisture** sensors (analog ADC)
- **Analog UV index** sensors
- **XBee S3B 900 MHz DigiMesh** coordinator via UART for a remote sensor mesh
- Full **Home Assistant** integration: sensors, switches, adjustable setpoints, events

## Files

| File | Purpose |
|---|---|
| `kc868-a16-gecko-habitat.yaml` | Main ESPHome configuration |
| `kc868-a16-gecko-habitat.factory.yaml` | Factory firmware (for initial USB flash + Wi-Fi provisioning) |

## Quick start

1. Copy `secrets.yaml.example` → `secrets.yaml` and fill in your credentials.
2. Flash the factory firmware via USB:  
   `esphome run kc868-a16-gecko-habitat.factory.yaml`
3. Connect to the **"Gecko Habitat Setup"** Wi-Fi access point to provision Wi-Fi.
4. Adopt the device in ESPHome and follow the first-run steps in `static/index.md`.

## Hardware wiring summary

See the pin-reference comment block at the top of `kc868-a16-gecko-habitat.yaml`.
