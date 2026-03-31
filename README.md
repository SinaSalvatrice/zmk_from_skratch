# ZMK Unified Base - Nice Nano OLED Shield

A minimal ZMK keyboard firmware configuration with OLED (SSD1306) display support for the Nice Nano.

## Features

- ✅ SSD1306 OLED Display (128x64)
- ✅ I2C Communication
- ✅ Basic QWERTY Keymap
- ✅ GitHub Actions Build Workflow

## Hardware

- **Microcontroller**: Nice Nano (nRF52840)
- **Display**: SSD1306 128x64 OLED
- **Communication**: I2C (SDA/SCL on GPIO3/GPIO2)

## Configuration

### Directory Structure

```
├── boards/           # Board overlays
├── config/           # ZMK configuration files
├── dts/             # Device tree bindings
├── .github/
│   └── workflows/   # CI/CD workflows
├── build.yaml       # Build configuration
├── Kconfig          # Kconfig options
└── README.md        # This file
```

### Files

- `boards/nice_nano.overlay` - Hardware I2C and OLED configuration
- `config/nice_nano.conf` - ZMK feature configuration
- `config/nice_nano.keymap` - Keyboard keymap definition
- `nice_nano_oled.shield.overlay` - Shield overlay for OLED
- `.github/workflows/build.yml` - Automated build workflow

## Building

### Local Build

```bash
west build -s app -b nice_nano_33 -- -DSHIELD=nice_nano_oled
```

### Remote Build (GitHub Actions)

Push to main branch or create a pull request. The workflow will automatically build the firmware.

## OLED Display

- **Resolution**: 128x64 pixels
- **Interface**: I2C @ 0x3c
- **Features**: Status screen built-in
- **Pins**: SDA (GPIO3), SCL (GPIO2)

## Customization

Edit `config/nice_nano.keymap` to customize your keyboard layout.

## Troubleshooting

If OLED doesn't display:
1. Verify I2C pins are correct (SDA/SCL)
2. Check power and ground connections
3. Ensure SSD1306 is at I2C address 0x3c
4. Rebuild and reflash firmware
