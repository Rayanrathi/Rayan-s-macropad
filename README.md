# Rayan's Macropad

A custom 4-key macropad with a rotary encoder and OLED display, built as part of Hack Club's PCB design program.

---

## Renders & Screenshots

### PCB 3D Render
![PCB 3D Render](images/pcb_3d.jpeg)

### Schematic
![Schematic](images/schematic.jpeg)

### PCB Layout
![PCB Layout](images/pcb_layout.jpeg)

### Case — Bottom
![Case Bottom](images/case_bottom.jpeg)

### Case — Lid
![Case Lid](images/case_lid.jpeg)

---

## Features

- 4x tactile push switches (SW1–SW4)
- EC11 rotary encoder with push button (SW6)
- 0.91" 128×32 OLED display
- Seeeduino XIAO SAMD21 microcontroller
- QMK firmware with layer support and WPM counter
- Custom 3D printed sandwich-mount case

---

## Bill of Materials

| Part | Quantity | Notes |
|------|----------|-------|
| Seeeduino XIAO SAMD21 | 1 | Main MCU |
| Tactile push switch | 4 | SW1–SW4 |
| EC11 Rotary Encoder | 1 | SW6, with push button |
| 0.91" SSD1306 OLED (128×32) | 1 | I2C, 4-pin, J1 connector |
| M2.9 screws | 4 | Sandwich mount lid to base |
| Custom PCB | 1 | 97mm × 49.5mm, see /PCB |
| 3D printed case (top + bottom) | 1 set | See /CAD |

---

## Pin Assignments

| Component | XIAO Pin |
|-----------|----------|
| SW1 | A0 (PA02) |
| SW2 | A1 (PA4) |
| SW3 | A2 (PA10) |
| SW4 | A3 (PA11) |
| OLED SDA | A4 (PA8) |
| OLED SCL | A5 (PA9) |
| Encoder A | A8 (PA5) |
| Encoder B | A9 (PA7) |

All switches are wired directly (no matrix) — one side to GND, other side to pin.

---

## PCB

Designed in KiCad. Board size: 97mm × 49.5mm.
To order, use `production/gerbers.zip` with JLCPCB or PCBWay.

---

## Case

Designed in OpenSCAD. Sandwich-mount style.
- Base: 3mm floor + 10mm walls = 13mm total height
- Lid: 3mm thick with switch holes, OLED window, encoder shaft hole

Export STLs from `case_bottom.scad` and `case_lid.scad` → F6 → Export as STL.

---

## Firmware

Built with QMK. See `/Firmware/` folder.

**Default keymap:**

| Key | Base | FN |
|-----|------|----|
| SW1 | 1 | F1 |
| SW2 | 2 | F2 |
| SW3 | 3 | F3 |
| SW4 | 4 | F4 |
| Knob CW | Vol Up | Next Track |
| Knob CCW | Vol Down | Prev Track |

OLED shows: keyboard name, current layer, encoder hint, WPM counter.

**To flash:**
```bash
qmk compile -kb rayan_macropad -km default
```
Double-tap RST on XIAO → open QMK Toolbox → load `.bin` → Flash.

---

## Build Guide

1. Solder XIAO onto PCB
2. Solder SW1–SW4 switches
3. Solder EC11 rotary encoder (SW6)
4. Connect OLED to J1 connector
5. 3D print top and bottom case
6. Place PCB into bottom case
7. Screw lid on with 4x M2.9 screws
8. Flash QMK firmware

---

## File Structure

```
your-macropad/
├── README.md
├── images/
│   ├── pcb_3d.jpeg
│   ├── schematic.jpeg
│   ├── pcb_layout.jpeg
│   ├── case_bottom.jpeg
│   └── case_lid.jpeg
├── CAD/
│   └── assembled-model.STEP
├── PCB/
│   ├── your-project.kicad_pro
│   ├── your-project.kicad_sch
│   └── your-project.kicad_pcb
├── Firmware/
│   └── rayan_macropad/
└── production/
    ├── gerbers.zip
    ├── Top.STEP
    ├── Bottom.STEP
    └── firmware.uf2
```

---

*Made with ❤️ as part of [Hack Club](https://hackclub.com)*
