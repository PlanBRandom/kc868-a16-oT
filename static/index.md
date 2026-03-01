# Crested Gecko Habitat Control Center

Full-featured ESPHome firmware for the **KC868-A16** (ESP32) controller board,
turning it into a comprehensive crested-gecko habitat management system.

## Features

| Category | Details |
|---|---|
| **Temperature** | 30× DS18B20 one-wire sensors; thermostat control via 8-ch SSR module |
| **Humidity** | SHT30/SHT31 I²C sensors; auto-mist when below target |
| **Lighting** | UVB lamp, ambient LED, secondary zone & night heat – day/night schedule |
| **Misting** | Primary + backup pump with adjustable duration & countdown timer |
| **Fan / Airflow** | Relay on/off + PWM speed control; auto-boost on high humidity |
| **Feeding tracker** | Physical button resets countdown; overdue alarm fires buzzer & red LED |
| **Alarms** | Red (critical), Yellow (warning), Green (status) indicator LEDs |
| **Substrate moisture** | Capacitive sensors on analog ADC with calibration |
| **UV index** | Analog UV sensors on ADC |
| **XBee DigiMesh** | S3B 900 MHz coordinator via UART for remote sensor mesh |
| **Home Assistant** | All sensors/switches exposed; events for fed/misted/alarm; adjustable setpoints |
| **Web dashboard** | Built-in ESPHome web server at `http://<device-ip>` |

## Hardware

- **Controller:** KC868-A16 (ESP32-based, 16-relay, 8 analog inputs)
- **Relay loads:** 8-channel Solid-State Relay (SSR) module
- **Temp sensors:** 30× DS18B20 on single 1-Wire bus (GPIO21, 4.7 kΩ pull-up)
- **Humidity:** SHT30/SHT31 on I²C bus (SDA=GPIO4, SCL=GPIO15)
- **Analog inputs:** UV sensors + capacitive moisture sensors (GPIO34, GPIO35, GPIO36, GPIO39)
- **Fan:** PWM speed control on GPIO26 (25 kHz)
- **Alarm LEDs:** Red=GPIO25, Yellow=GPIO18, Green=GPIO19
- **Buttons:** Feed=GPIO12, Manual Mist=GPIO13, Dismiss=GPIO14, Door=GPIO27
- **XBee UART:** TX=GPIO17, RX=GPIO16

## Installation

Use the button below to flash the firmware directly from your browser via USB.

<esp-web-install-button manifest="firmware/gecko-habitat.manifest.json"></esp-web-install-button>

<script type="module" src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js?module"></script>

## First-run steps

1. Flash the factory firmware and connect to the **"Gecko Habitat Setup"** Wi-Fi AP to provision your Wi-Fi credentials.
2. Adopt the device in the ESPHome dashboard.
3. Run `esphome logs kc868-a16-gecko-habitat.yaml` to discover DS18B20 sensor addresses, then update the placeholder addresses in the YAML.
4. Calibrate the capacitive moisture sensors (`dry_v` / `wet_v` lambdas in the YAML).
5. Adjust timezone, temperature setpoints and scheduling times to suit your setup.
