# Klipper Delta Calibration

This guide walks through basic delta calibration in Klipper.

## What this does

Delta calibration adjusts tower endstop positions, tower angles, delta radius, and arm-related geometry so the printer moves accurately across the bed.

## Important note

Delta calibration is only for delta printers. If your printer is not a delta machine, this guide does not apply.

## Before you start

- Make sure your printer already has reasonable starting delta values in `printer.cfg`
- If available, begin with the manufacturer or kit default geometry values
- Make sure the printer can home correctly
- Add a `[delta_calibrate]` section to your config if it is not already present

Klipper notes that the starting arm lengths, radius, and endstop positions should already be within a few millimeters.

## Probe choice matters

Klipper specifically warns that some automatic probes on delta printers are not accurate enough because small arm-length differences can tilt the effector and skew the probe result.

If probe bias is more than about `0.025 mm`, manual calibration is usually the better choice.

## Step 1: Allow a little extra Z travel if needed

Klipper notes that calibration may require probing slightly below the normal bed plane.

A typical temporary setting is:

```ini
[printer]
minimum_z_position: -5
```

You can remove or adjust that later if it is only needed for calibration.

## Step 2: Home the printer

Run:

```text
G28
```

## Step 3: Run basic delta calibration

For manual probing:

```text
DELTA_CALIBRATE METHOD=manual
```

For automatic probing:

```text
DELTA_CALIBRATE
```

Manual probing is often the safer choice on delta machines unless you know the probe is very accurate.

## Step 4: Save the result

After Klipper calculates the new parameters, run:

```text
SAVE_CONFIG
```

## Step 5: Test normal printing

After the basic calibration:

- Print a simple test object
- Check first-layer consistency
- Check dimensions and general motion accuracy

Klipper considers the basic calibration good enough for normal printing, and then you can decide whether you want the more advanced calibration workflow later.

## Good habits

- Recheck probe calibration after delta calibration if your probe has X or Y offset
- Use manual probing if automatic probe results seem inconsistent
- Do not skip starting geometry values in config
- Treat large errors as a sign to inspect mechanics, not just rerun software calibration

## Official reference

This guide is based on the official Klipper delta calibration documentation:

- [Klipper Delta Calibration](https://www.klipper3d.org/Delta_Calibrate.html)
