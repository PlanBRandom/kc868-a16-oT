# KC868-A16 Gecko Enclosure Monitor

ESPHome firmware for the **Kincony KC868-A16** controller.

## Features

- **16 gecko enclosures** – named and grouped into two vivarium rows (Juveniles / Adults)
- **Relay control** – 16 relay outputs (heating lamps, UVB, misters) via PCF8575 I2C expander
- **Digital inputs** – 16 door / trigger inputs via PCF8575 I2C expander
- **Bluetooth Proxy** – extends Home Assistant Bluetooth reach into the vivarium room
- **NFC / QR-code tags** – unique identification URL per enclosure; print as QR code or write to an NTAG213 NFC sticker
- **OI-7530 gas monitoring** – all 32 channels of the Otis Instruments OI-7530 read via RS485 Modbus RTU

## Customising gecko names

Edit the `substitutions` block in `project-template-esp32.yaml` to rename each enclosure:

```yaml
substitutions:
  enc_01: "Row A - Spike"
  enc_02: "Row A - Luna"
  # …
```

## Installation

Use the button below to install the pre-built firmware directly to your KC868-A16 via USB from the browser.

<esp-web-install-button manifest="firmware/kc868-a16-gecko.manifest.json"></esp-web-install-button>

<script type="module" src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js?module"></script>
