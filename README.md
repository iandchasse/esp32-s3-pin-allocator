# ESP32-S3-WROOM-1 (N8R8) GPIO Pin Allocator

A single-file, static web app to visually allocate GPIO pins for an
**ESP32-S3-WROOM-1, R8 variant (8MB Octal PSRAM)** during PCB layout.

Open `index.html` in a browser or deploy it to any static host — no build step, no backend.

## Features
- 40-pin module rendered by physical edge (left 1–14, bottom 15–26, right 27–40)
  in perimeter order so it mirrors the real footprint.
- Click a pin to assign a function; per-pin capabilities (ADC1, native FSPI role,
  strapping) shown in the side panel.
- Color-coded by pin class and current assignment; badges for ADC1 / FSPI / strapping.
- Highlight modes: ADC1 pins, native FSPI pins, strapping pins, free "safe" pins.
- Validation:
  - ADC allowed only on ADC1 pins (ADC2 blocked — WiFi active).
  - GPIO35/36/37 locked as Octal-PSRAM reserved.
  - Strapping pins (GPIO0/3/45/46) warn against driving at boot.
  - USB fixed to GPIO19 (D-) / GPIO20 (D+).
  - GPIO43/44 warn (shared with UART0 default console).
  - Duplicate unique-signal detection (e.g. two I2C SDA).
  - Running allocation status / per-signal checklist.
- Export / import allocation as JSON; copy summary as a Markdown table.

Pin data is transcribed from the authoritative table for this exact module variant.
