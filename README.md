# Analog Tilt Sensor

A tilt sensor built entirely from analog circuitry (no microcontroller)
using an ADXL335 accelerometer, LM324N op amps, and PN2222 transistors.
Built as a final project for 311, an advanced circuits course, at CSULB
in [Fall/Spring] 2025.

## How it works
- **Sensing:** The ADXL335, a 3-axis analog accelerometer, outputs a voltage
  on each of the X, Y, and Z axes that changes with orientation.
- **Filtering:** Three active low-pass filters, one per axis, are built from
  op amps on the first LM324N to remove noise and vibration.
- **Detection:** Three op amp comparators on the second LM324N compare each
  axis's filtered voltage against a reference voltage set by a potentiometer.
- **Output:** Each comparator drives a PN2222 NPN transistor, which switches
  one LED per axis (X, Y, Z), so the lit LED shows which side is tilted.
- **Sensitivity:** Turning the potentiometer changes the reference voltage,
  which sets how far the sensor must tilt before an LED turns on.

## Parts list
| Part | Qty |
|------|-----|
| ADXL335 3-axis accelerometer | 1 |
| LM324N quad op amp | 2 (6 of 8 op amps used: 3 filters, 3 comparators) |
| PN2222 NPN transistor | 3 |
| LED | 3 |
| Potentiometer | 1 |
| Resistors and capacitors (filter and biasing) | as used |

## Schematic
![Schematic](schematics/schematic.png)

## Finished Circuit
<img width="240" height="320" alt="image" src="https://github.com/user-attachments/assets/63d03ca0-8f2d-4ae9-8388-920704a2fc56" />

<img width="240" height="320" alt="image" src="https://github.com/user-attachments/assets/029942de-8994-4c67-af4d-d4133c74631c" />

<img width="240" height="320" alt="image" src="https://github.com/user-attachments/assets/52c36dd8-b475-4a0b-b473-7186b47ca131" />





## What I learned
Designing the active low-pass filters showed me how the cutoff frequency
trades noise rejection against response speed. Using op amps as comparators
against a potentiometer reference taught me how threshold settings affect
false triggers versus missed detections. With no microcontroller, every
behavior had to come from the circuit itself, so I debugged by measuring
voltages at each stage to find where a signal went wrong.
