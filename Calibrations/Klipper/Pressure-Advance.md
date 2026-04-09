# Klipper Pressure Advance Tuning

This guide walks through tuning `pressure_advance` in Klipper.

## What this does

Pressure advance helps reduce corner blobs and extra ooze by adjusting extrusion during acceleration and deceleration.

## Before you start

- Make sure the printer is already printing well
- Calibrate extruder `rotation_distance` first
- Use the nozzle and filament you actually plan to print with
- Be aware that different filaments can need different values

## Print setup

Klipper recommends printing the large hollow square test model from its documentation.

When slicing the test:

- Use high speed, around 100 mm/s
- Use zero infill
- Use a coarse layer height, around 75% of nozzle diameter
- Disable dynamic acceleration control if your slicer supports it
- Disable scarf joint seams if your slicer supports them

## Step 1: Set temporary motion limits

Run this in the console before the test print:

```text
SET_VELOCITY_LIMIT SQUARE_CORNER_VELOCITY=1 ACCEL=500
```

This exaggerates the extrusion behavior at corners so the effect is easier to see.

## Step 2: Start the tuning tower

For a direct drive extruder, run:

```text
TUNING_TOWER COMMAND=SET_PRESSURE_ADVANCE PARAMETER=ADVANCE START=0 FACTOR=.005
```

For a long Bowden setup, run:

```text
TUNING_TOWER COMMAND=SET_PRESSURE_ADVANCE PARAMETER=ADVANCE START=0 FACTOR=.020
```

Then start the test print.

## Step 3: Inspect the print

As the print gets taller, Klipper changes the pressure advance value on each layer.

What to look for:

- Lower layers may show blobs at the corners
- Higher layers may start to show rounded corners or weak extrusion before corners
- The best layer is the one where corners look clean without starting to degrade

You can stop the print early once the corners clearly get worse.

## Step 4: Measure the best height

Use digital calipers to measure the height of the layer region with the best corner quality.

When in doubt, choose the lower value.

## Step 5: Calculate pressure advance

Use this formula:

```text
pressure_advance = start + measured_height * factor
```

Example for a Bowden setup:

```text
start = 0
measured_height = 12.90
factor = .020

pressure_advance = 0 + 12.90 * .020
pressure_advance = 0.258
```

## Step 6: Save the value

Add the final number to your `[extruder]` section in `printer.cfg`.

Example:

```ini
[extruder]
pressure_advance: 0.258
```

Then run:

```text
RESTART
```

## Important notes

- Pressure advance depends on the extruder, nozzle, and filament
- Different filament brands and even different colors can need different values
- If there is no clear benefit, it is okay to leave pressure advance disabled
- If the value is very high and the extruder starts skipping, reduce acceleration or use a lower value

## Official reference

This guide is based on the official Klipper pressure advance guide:

- [Klipper Pressure Advance](https://www.klipper3d.org/Pressure_Advance.html)
