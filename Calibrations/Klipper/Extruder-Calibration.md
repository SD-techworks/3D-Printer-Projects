# Klipper Extruder Calibration

This guide walks through calibrating your extruder in Klipper by tuning the `rotation_distance` value.

## What this does

Extruder calibration makes sure the printer feeds the amount of filament you actually ask for. If this value is off, prints can be over-extruded or under-extruded.

## Before you start

- Load filament into the printer
- Heat the hotend to a normal printing temperature for your filament
- Make sure the printer is ready to extrude
- Have a marker and digital calipers ready
- Start with a reasonable existing `rotation_distance` value in your `[extruder]` section

## Step 1: Mark the filament

Place a mark on the filament around 70 mm above the extruder intake. Then measure the exact distance from the top of the extruder entry to the mark and write that number down.

Call that number:

```text
initial_mark_distance
```

## Step 2: Extrude 50 mm

In the Klipper console, run:

```text
G91
G1 E50 F60
```

This tells the printer to extrude 50 mm slowly enough to measure accurately.

Wait for the move to finish completely before measuring again.

## Step 3: Measure the new distance

Measure the distance from the extruder entry to the mark again.

Call that number:

```text
final_mark_distance
```

## Step 4: Calculate actual extrusion

Use this formula:

```text
actual_extrude_distance = initial_mark_distance - final_mark_distance
```

Example:

```text
initial_mark_distance = 70
final_mark_distance = 22
actual_extrude_distance = 48
```

## Step 5: Calculate the new rotation_distance

Use this formula from the Klipper docs:

```text
new_rotation_distance = old_rotation_distance * actual_extrude_distance / requested_extrude_distance
```

For this guide, the requested extrude distance is:

```text
requested_extrude_distance = 50
```

Example:

```text
old_rotation_distance = 22.6789511
actual_extrude_distance = 48
requested_extrude_distance = 50

new_rotation_distance = 22.6789511 * 48 / 50
new_rotation_distance = 21.771793
```

## Step 6: Update printer.cfg

Open your Klipper config and replace the current `rotation_distance` in the `[extruder]` section with the new value.

Example:

```ini
[extruder]
rotation_distance: 21.771793
```

Then run:

```text
RESTART
```

## Step 7: Repeat once more

Run the same test again to confirm the result is now close to 50 mm. A small amount of error is normal, but you want it to be very close.

## Good habits

- Always calibrate with the hotend heated
- Extrude slowly during testing
- Double-check your measurement with calipers
- Recheck after changing extruders, gears, or filament path hardware

## Official reference

This guide is based on the official Klipper rotation distance guide:

- [Klipper Rotation Distance](https://www.klipper3d.org/Rotation_Distance.html)
