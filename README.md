# ZMK Unified Base - Nice Nano OLED

A minimal ZMK keyboard firmware configuration with OLED (SSD1306) display support for the Nice Nano microcontroller.

## Features

- ✅ SSD1306 OLED Display (128x64) via I2C
- ✅ Nice Nano (nRF52840) with BLE & USB
- ✅ Basic QWERTY Keymap
- ✅ GitHub Actions CI/CD Workflow

## Hardware

- **Microcontroller**: Nice Nano (nRF52840)
- **Display**: SSD1306 128x64 OLED
- **Connection**: I2C (SDA on GPIO3, SCL on GPIO2)
- **Display Address**: 0x3c

## Project Structure

```
├── boards/
│   └── nice_nano.overlay      # OLED & I2C hardware config
├── config/
│   ├── nice_nano.conf         # ZMK feature flags
│   └── nice_nano.keymap       # Keyboard layout
├── .github/
│   └── workflows/
│       └── build.yml          # Automated CI/CD build
├── build.yaml                 # Build target config
├── west.yml                   # Workspace manifest
└── README.md                  # This file
```

## Building

### GitHub Actions (Automated)
Push to `main` or `copilot/*` branches, or open a PR. The workflow will automatically build and upload firmware artifacts.

### Local Build (if you have ZMK environment)
```bash
west build -s zmk/app -b nice_nano_33 config
```

## Configuration

### OLED Settings
- **Resolution**: 128x64 pixels
- **Interface**: I2C @ address 0x3c
- **Status Display**: Built-in (auto-enabled)
- **Colors**: Inverted

### I2C Pins (Nice Nano)
- **SDA**: GPIO3
- **SCL**: GPIO2
- **Pull-ups**: 10kΩ recommended

## Customization

Edit `config/nice_nano.keymap` to change the keyboard layout.

## Troubleshooting

**OLED not displaying:**
- Verify I2C wiring (SDA/SCL pins)
- Check SSD1306 is at address 0x3c
- Ensure power/ground connections
- Check `boards/nice_nano.overlay` I2C configuration

**Build fails on GitHub Actions:**
- Check workflow logs for error details
- Verify `config/nice_nano.conf` has valid CONFIG_* flags
- Ensure west.yml is properly formatted

