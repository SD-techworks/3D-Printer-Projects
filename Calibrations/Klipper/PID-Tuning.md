# Klipper PID Tuning

This guide walks through tuning PID values for the hotend and heated bed in Klipper.

## What this does

PID tuning helps your printer hold a more stable temperature. Better temperature control can improve print consistency and reduce temperature swings.

## Before you start

- Make sure the printer is configured and heating correctly
- Do not leave the printer unattended during tuning
- Use a realistic target temperature for the heater you are tuning

## Hotend PID tuning

In the Klipper console, run:

```text
PID_CALIBRATE HEATER=extruder TARGET=170
```

Klipper uses `170` as a common example in its docs, but you can choose a target closer to your real print temperature if that makes more sense for your filament and hotend.

Wait for the test to finish.

Then run:

```text
SAVE_CONFIG
```

This writes the new PID values into your config automatically.

## Heated bed PID tuning

If your bed supports PID control, a common example is:

```text
PID_CALIBRATE HEATER=heater_bed TARGET=60
```

After the test finishes, run:

```text
SAVE_CONFIG
```

## Where the values go

Klipper will save the tuned values into your config after `SAVE_CONFIG`.

They typically appear in the relevant heater section with values like:

```ini
[extruder]
control: pid
pid_Kp: ...
pid_Ki: ...
pid_Kd: ...
```

and:

```ini
[heater_bed]
control: pid
pid_Kp: ...
pid_Ki: ...
pid_Kd: ...
```

## Good habits

- Tune the hotend near the temperatures you actually print at
- Retune after major hotend changes
- Retune the bed after changing bed heaters or control hardware
- Let the process finish fully before saving config

## Important note

Some heaters controlled by a mechanical switch may not be suitable for PID bed control. The official Klipper docs call this out specifically for some bed setups.

## Official reference

This guide is based on the official Klipper configuration checks guide:

- [Klipper Configuration Checks](https://www.klipper3d.org/Config_checks.html)
