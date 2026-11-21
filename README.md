🇬🇧 **English** · 🇩🇪 [Deutsch](README.de.md)

# gutmann-sombra-pcb

Hardware for connecting a Gutmann Sombra range hood to home automation: an
ESP8266 board (ESP-12E) that sits in the cable between the hood electronics
and the front panel. It reads which front-panel LEDs are lit and can
simulate key presses. The original front panel keeps working as before.

- KiCad 10 PCB, 80 × 55 mm, through-hole except the ESP-12E module
- Powered from the hood's service connector (~4.8 V) via a buck-boost
  converter
- Level shifters for the 5 V key matrix of the hood
- Fabrication files included

## Firmware

| Repository | Status |
|---|---|
| [gutmann-sombra-esphome](https://github.com/jowi24/gutmann-sombra-esphome) | **Recommended.** ESPHome external component, native Home Assistant API |
| [gutmann-sombra-mqtt](https://github.com/jowi24/gutmann-sombra-mqtt) | Arduino/PlatformIO, MQTT with Home Assistant discovery. No longer maintained |

Both run on the same board and can be swapped over the air.

## Documentation

| Document | Contents |
|---|---|
| [How the circuit works](docs/CIRCUIT.md) | Beginner-friendly explanation: the hood's key matrix, level shifters, power supply, firmware timing, troubleshooting |
| [Hardware design notes](kicad/DESIGN.md) | Part values, sourcing, layout decisions, bring-up findings |
| [Fabrication files](kicad/fab/FAB.md) | Gerber/drill files and PCB order parameters |
| [Schematic](kicad/schematic.pdf) · [Layout](kicad/board-layout.pdf) | PDF exports |

All documents are also available in German (`*.de.md`).

## Status

PCB rev. 0.3. The fabricated rev. 0.2 boards work after a small
modification at U3 (diodes + pull-downs, see [DESIGN.md](kicad/DESIGN.md)).

## Project layout

```
kicad/                schematic, PCB, custom footprint and 3D model
kicad/fab/            fabrication files
docs/                 description of the circuit
fritzing/             2017 perfboard version (reference only)
```

## First flash

New boards are flashed serially via J2 (3.3 V USB-serial adapter) with
jumper J5 set to FLASH; afterwards set J5 back to RUN and press reset. See
[CIRCUIT.md](docs/CIRCUIT.md), section 10. All later updates go over Wi-Fi.

## Background

Blog post about the original perfboard version:
[Do-It-Yourself IoT Modul für die Dunstabzugshaube](https://joachim-wilke.de/blog/2017/12/27/do-it-yourself-iot-modul-fur-die-dunstabzugshaube/)

## License

Copyright (c) 2017–2026 Joachim Wilke. Hardware and documentation are
licensed under [CC BY-NC-SA 4.0](LICENSE) and are free for
**non-commercial** use only. Commercial use (e.g. selling boards, kits or
products based on this project) requires the author's permission.
