# B-Lamp — Bill of Materials

The B-Lamp is a 3D printed LED lamp designed for desk or shelf use. All electronic components are off-the-shelf and the structural parts can be printed on any FDM printer.

---

## 3D Printed Parts

| Part | Qty | Print Notes |
|------|-----|-------------|
| Lamp base | 1 | 20% infill, PETG or PLA |
| Lamp shade | 1 | 10% infill, translucent PLA recommended |
| PCB mount bracket | 1 | 30% infill, any material |
| Diffuser ring | 1 | 10% infill, translucent PLA |
| Cable clip | 2 | 20% infill, any material |

> **STL files** are provided in the `/stl` folder of the project repository.

---

## Electronics

| Component | Specification | Qty | Notes |
|-----------|---------------|-----|-------|
| LED strip | WS2812B 60 LED/m, 5 V | 0.5 m | Cut to length; ~30 LEDs total |
| Microcontroller | Seeed XIAO RP2040 | 1 | Or any 3.3 V board with USB-C |
| USB-C power supply | 5 V / 2 A | 1 | At least 10 W |
| USB-C breakout board | — | 1 | For clean power entry |
| Capacitor | 1000 µF, 6.3 V electrolytic | 1 | Across LED strip power rails |
| Resistor | 330 Ω, 1/4 W | 1 | On the data line to the LED strip |
| Tactile push button | 6 mm through-hole | 1 | Mode / brightness control |

---

## Wiring & Fasteners

| Item | Qty | Notes |
|------|-----|-------|
| 22 AWG silicone wire, red | 30 cm | Power positive |
| 22 AWG silicone wire, black | 30 cm | Power ground |
| 22 AWG silicone wire, yellow | 15 cm | Data line |
| M3 × 8 mm socket-head screw | 4 | Attaches shade to base |
| M3 hex nut | 4 | Captured in base pockets |
| M2 × 6 mm self-tapping screw | 4 | Mounts PCB bracket |

---

## Tools Required

- FDM 3D printer with a 0.4 mm nozzle
- Soldering iron and solder
- Wire stripper / cutter
- Small Phillips and hex screwdrivers (M3)
- Multimeter (recommended)
