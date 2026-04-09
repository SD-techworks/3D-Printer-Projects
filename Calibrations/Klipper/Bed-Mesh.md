# Klipper Bed Mesh Calibration

This guide walks through creating a bed mesh in Klipper so the printer can compensate for small bed surface irregularities.

## What this does

Bed mesh helps improve first-layer consistency across the bed by adjusting Z height based on measured surface points.

## Important note

Bed mesh is not a fix for mechanical problems. The Klipper docs are clear that it can help compensate for surface irregularities, but it cannot fully correct bad probe accuracy, skew, or other hardware issues.

## Before you start

- Make sure your probe Z offset is calibrated first
- If you use a Z endstop instead of a probe, make sure Z endstop calibration is already done
- Heat the bed to a normal printing temperature before probing if you want the mesh to reflect real print conditions
- Make sure the bed mesh section already exists in `printer.cfg`

## Basic bed_mesh config example

For a rectangular bed, a common starting point looks like this:

```ini
[bed_mesh]
speed: 120
horizontal_move_z: 5
mesh_min: 35, 6
mesh_max: 240, 198
probe_count: 5, 3
```

Your actual values should match your printer's usable bed area and probe reach.

## Step 1: Home the printer

Run:

```text
G28
```

## Step 2: Run bed mesh calibration

If you have a probe, a simple starting command is:

```text
BED_MESH_CALIBRATE
```

If you want to force manual probing:

```text
BED_MESH_CALIBRATE METHOD=manual
```

Klipper also supports `automatic`, `scan`, and `rapid_scan` methods when your setup supports them.

## Step 3: Review the result

When the command finishes, the mesh is active immediately.

Check for:

- Unexpectedly large height variation
- Strange points that suggest probe error
- A mesh area that does not cover the print area you actually use

## Step 4: Save the mesh

To save the current mesh profile into config, run:

```text
SAVE_CONFIG
```

Klipper can store the mesh in a named profile or in the default profile.

## Helpful commands

- Create mesh: `BED_MESH_CALIBRATE`
- Save or load mesh profiles: `BED_MESH_PROFILE SAVE=<name>` or `BED_MESH_PROFILE LOAD=<name>`
- Clear current mesh: `BED_MESH_CLEAR`

## Good habits

- Recreate the mesh after major hotend, probe, or bed changes
- Heat the bed before probing for more realistic results
- Keep the probe clean and repeatable
- If results look inconsistent, fix the mechanical issue before relying on the mesh

## Official reference

This guide is based on the official Klipper bed mesh documentation:

- [Klipper Bed Mesh](https://www.klipper3d.org/Bed_Mesh.html)
