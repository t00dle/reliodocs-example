# B-Lamp — Build Guide

The B-Lamp is a compact 3D printed LED lamp powered by a WS2812B LED strip and a small microcontroller. This guide walks through printing the parts, wiring the electronics, and assembling the final lamp.

---

## Prerequisites

- All parts from the [Bill of Materials](bom.md) on hand
- Slicer software (e.g. PrusaSlicer, Cura, or Bambu Studio)
- Basic soldering experience
- Estimated build time: **2–3 hours**

---

## Step 1 — Print the Parts

1. Download the STL files from the `/stl` folder in the project repository.
2. Slice each part with the settings listed in the BOM print notes.
3. Recommended settings for structural parts:
   - Layer height: 0.2 mm
   - Perimeters: 3
   - Supports: none required (all parts designed to print support-free)
4. Recommended settings for the shade and diffuser ring:
   - Layer height: 0.15 mm for smoother surface
   - Infill: 10% gyroid
   - Material: **translucent PLA** for best light diffusion
5. Allow parts to cool fully before removing from the build plate.

---

## Step 2 — Prepare the LED Strip

1. Cut the WS2812B strip to **30 LEDs** (0.5 m at 60 LED/m density). Always cut on the designated cut lines between pads.
2. Tin the three solder pads at the input end of the strip: **5V**, **GND**, and **DIN**.
3. Solder the 330 Ω resistor in series on the **DIN** wire before connecting to the microcontroller data pin. This protects the first LED from signal reflections.
4. Solder the 1000 µF capacitor across the **5V** and **GND** pads at the power-input end of the strip. Observe correct polarity (positive leg to 5V).

---

## Step 3 — Wire the Electronics

```
USB-C breakout ──5V──┬──────────────────── LED strip 5V
                     │
                    [1000 µF cap]
                     │
USB-C breakout ──GND─┴──────────────────── LED strip GND
                     │
              XIAO RP2040 GND ─────────── (shared ground)

XIAO RP2040 D0 ──[330 Ω]──────────────── LED strip DIN

XIAO RP2040 D1 ─────────────────────────── button pin 1
GND ─────────────────────────────────────── button pin 2
```

1. Connect the USB-C breakout board **VBUS** pin to the LED strip **5V** pad and also to the **VIN** or **5V** pin on the XIAO RP2040.
2. Join all **GND** connections: breakout board, LED strip, and XIAO RP2040.
3. Run the data wire from XIAO pin **D0** through the 330 Ω resistor to the LED strip **DIN** pad.
4. Connect the tactile push button between XIAO pin **D1** and **GND**.
5. Double-check polarity on the capacitor before powering on.

---

## Step 4 — Flash the Firmware

1. Plug the XIAO RP2040 into your computer while holding the **BOOT** button to enter UF2 bootloader mode. A USB drive named `RPI-RP2` should appear.
2. Copy the provided `.uf2` firmware file from the `/firmware` folder onto the drive. The board will reboot automatically.
3. Once flashed, the LED strip should illuminate with the default warm-white scene.
4. Short-press the button to cycle through preset scenes; long-press (> 1 s) to toggle the lamp on/off.

---

## Step 5 — Mount the Electronics

1. Place the **PCB mount bracket** flat inside the lamp base, aligning the four M2 screw holes.
2. Secure the XIAO RP2040 and USB-C breakout board to the bracket using **M2 × 6 mm self-tapping screws**.
3. Coil the excess wire neatly and use the **cable clips** to secure them to the interior walls of the base.
4. Feed the USB-C cable through the opening in the base.

---

## Step 6 — Attach the LED Strip

1. Peel the backing from the LED strip's adhesive side.
2. Route the strip along the inside rim of the **lamp shade**, pressing firmly so the adhesive seats fully.
3. Ensure the strip's **DIN** end aligns with where the wire exits toward the base.
4. Gently flex the shade into its final curve — the strip should follow without kinking.

---

## Step 7 — Final Assembly

1. Place the **diffuser ring** into the top opening of the shade. It should press-fit snugly.
2. Align the shade with the base so the four M3 screw bosses line up with the holes in the base top plate.
3. Insert **M3 hex nuts** into the captured pockets on the underside of the base.
4. Thread **M3 × 8 mm screws** through the shade into the nuts and tighten until snug — do not overtighten.
5. Plug in the USB-C cable and verify the lamp powers on.

---

## Troubleshooting

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No LEDs light up | Power not reaching strip | Check 5V and GND connections at strip input |
| First LED wrong colour / flickering | Missing or incorrect resistor | Verify 330 Ω on DIN line |
| LEDs flash then go dark | Power supply under-rated | Use a supply rated ≥ 2 A at 5 V |
| Lamp won't respond to button | Button wiring or firmware issue | Check D1 connection; reflash firmware |
| Shade does not seat flat | Warp in 3D print | Lightly sand the mating surface |

---

*Happy building! If you run into issues, open an issue in the project repository.*
