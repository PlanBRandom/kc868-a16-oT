# KC868-A16 OI-6950 Modbus Bridge

This firmware turns a **KinCony KC868-A16** (ESP32 + LAN8720 Ethernet + RS485) into
a Modbus RTU bridge for up to 30 **OI-6950** gas monitors.

- Polls all 16 gas channels from the OI-6950 every 5 seconds via RS485
- Reports readings to Home Assistant through the native API and MQTT auto-discovery
- Activates the matching relay/MOSFET output (Y01–Y16) when a gas channel exceeds the alarm threshold
- Forwards Bluetooth LE advertisements as a Bluetooth proxy
- Supports fleet deployment: `name_add_mac_suffix` gives every unit a unique device name

Register addresses follow the OI-7530/7010 pattern documented in
[PlanBRandom/teleproject](https://github.com/PlanBRandom/teleproject) and
[PlanBRandom/anjoytell](https://github.com/PlanBRandom/anjoytell).

## Hardware Connections

| KC868-A16 Pin | RS485 Signal | OI-6950 Terminal |
|---------------|-------------|-----------------|
| RS485 A+      | A (non-inv) | RS485 A          |
| RS485 B−      | B (inv)     | RS485 B          |
| GND           | GND         | GND              |

## Installation

Use the button below to install the pre-built firmware directly to your device via USB from the browser.

<esp-web-install-button manifest="firmware/kc868-a16-oi6950.manifest.json"></esp-web-install-button>

<script type="module" src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js?module"></script>
