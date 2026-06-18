# Rayan's Macropad
 
A custom 4-key macropad with a rotary encoder and OLED display, built as part of Hack Club's PCB design program.
 
---
 
## Features
 
- 4x tactile push switches (SW1–SW4)
- EC11 rotary encoder with push button (SW6)
- 0.91" 128×32 OLED display
- Seeeduino XIAO SAMD21 microcontroller
- QMK firmware with layer support and WPM counter
- Custom 3D printed sandwich-mount case
---
 
## Parts List
 
| Part | Quantity | Notes |
|------|----------|-------|
| Seeeduino XIAO SAMD21 | 1 | Main MCU |
| Tactile push switch | 4 | SW1–SW4 |
| EC11 Rotary Encoder | 1 | SW6, with push button |
| 0.91" SSD1306 OLED (128×32) | 1 | I2C, 4-pin |
| M2.9 screws | 4 | For sandwich mount |
| Custom PCB | 1 | See /PCB |
| 3D printed case (top + bottom) | 1 set | See /CAD |
 
---
 
## PCB
 
Designed in KiCad. The PCB is 97mm × 49.5mm.
 
**Pin assignments:**
 
| Component | XIAO Pin |
|-----------|----------|
| SW1 | A0 |
| SW2 | A1 |
| SW3 | A2 |
| SW4 | A3 |
| OLED SDA | A4 |
| OLED SCL | A5 |
| Encoder A | A8 |
| Encoder B | A9 |
 
All switches are wired directly (no matrix) with one side to GND and the other to the pin. The OLED is connected via I2C.
 
To order the PCB, use the gerbers in `/production/gerbers.zip` — works with JLCPCB or PCBWay.
 
---
 
## Case
 
Designed in OpenSCAD. Sandwich-mount style with a 3mm base, 10mm walls, and a 3mm lid.
 
**Lid cutouts:**
- 4x 13×13mm switch holes (SW1–SW4)
- 30×11.5mm OLED window
- ⌀7mm encoder shaft hole
- 4x M2.9 corner screw holes
Export `keyboard_case_97x49.5.scad` as two separate STLs:
- Set `EXPORT = "bottom"` → F6 → Export STL
- Set `EXPORT = "lid"` → F6 → Export STL
---
 
## Firmware
 
Built with QMK firmware. Located in `/Firmware/`.
 
**Default keymap:**
 
| Key | Base layer | FN layer |
|-----|-----------|----------|
| SW1 | 1 | F1 |
| SW2 | 2 | F2 |
| SW3 | 3 | F3 |
| SW4 | 4 | F4 |
| Knob CW | Volume Up | Next Track |
| Knob CCW | Volume Down | Prev Track |
 
**OLED displays:**
- Keyboard name
- Current layer
- Encoder function
- WPM counter
**To compile and flash:**
 
```bash
# Copy Firmware/ folder into qmk_firmware/keyboards/rayan_macropad
qmk compile -kb rayan_macropad -km default
```
 
Then double-tap the RST button on the XIAO → open QMK Toolbox → load the `.bin` file → Flash.
 
---
 
## Build Guide
 
1. Solder the XIAO onto the PCB
2. Solder SW1–SW4 switches
3. Solder the EC11 rotary encoder (SW6)
4. Solder the OLED display to the J1 connector
5. 3D print the top and bottom case pieces
6. Place PCB into the bottom case
7. Screw the lid on with 4x M2.9 screws
8. Flash QMK firmware via QMK Toolbox
---
 
## File Structure
 
```
your-macropad/
├── README.md
├── CAD/
│   └── assembled-model.STEP
├── PCB/
│   ├── your-project.kicad_pro
│   ├── your-project.kicad_sch
│   └── your-project.kicad_pcb
├── Firmware/
│   └── rayan_macropad/ (QMK source folder)
└── production/
    ├── gerbers.zip
    ├── Top.STEP
    ├── Bottom.STEP
    └── firmware.uf2
```
 
---
 
*Made with ❤️ as part of [Hack Club](https://hackclub.com)*
