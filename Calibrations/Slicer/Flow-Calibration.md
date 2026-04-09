# Flow Calibration

This guide walks through flow calibration as a slicer-side tuning step.

## What this does

Flow calibration adjusts how much material the slicer asks the printer to extrude. The goal is cleaner top surfaces, better dimensions, and less over-extrusion or under-extrusion.

## Important note

This is not the same thing as Klipper extruder `rotation_distance` calibration.

- `rotation_distance` makes sure the extruder physically feeds the correct amount
- Flow calibration fine-tunes print output for a specific filament, slicer profile, and print setup

Do the Klipper extruder calibration first, then do flow calibration.

## Suggested workflow

This guide follows OrcaSlicer's official calibration flow because it provides a documented, repeatable process.

## Before you start

- Finish extruder calibration first
- Use the exact filament you want to tune
- Use the nozzle, temperature, and layer settings you plan to print with
- Create a new normal project after finishing calibration so you are not still in calibration mode

## Step 1: Open slicer calibration tools

In OrcaSlicer, open the Calibration section and choose the flow calibration process.

The OrcaSlicer calibration guide recommends doing temperature first, then flow-related tuning, followed by later tests like pressure advance and retraction.

## Step 2: Run the first flow test

Start with the first flow calibration pass in OrcaSlicer.

Inspect the result and look for:

- Overfilled top surfaces
- Gaps or weak coverage
- Uneven line appearance
- A patch that looks the most balanced and consistent

## Step 3: Apply the first result

Choose the best-looking patch according to the OrcaSlicer guide and apply that corrected flow value.

## Step 4: Run the second pass if needed

If your slicer version or calibration method uses a second pass, run it to narrow the value further.

This helps refine the result around the best candidate from the first pass.

## Step 5: Save the flow ratio to the filament profile

Once you identify the best result, save the updated flow ratio in your slicer's filament profile.

## Good habits

- Tune per filament type and brand
- Different colors of the same material can behave differently
- Retest after major nozzle or temperature changes
- Do not use flow calibration as a substitute for fixing real under-extrusion problems

## Official references

This guide is based on OrcaSlicer's official calibration documentation:

- [OrcaSlicer Calibration Guide](https://github.com/SoftFever/OrcaSlicer/wiki/Calibration)
- [OrcaSlicer Flow Rate Calibration](https://github.com/SoftFever/OrcaSlicer/wiki/flow-rate-calib)
