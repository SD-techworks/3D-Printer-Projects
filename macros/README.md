# Macros

A collection of printer and Klipper macros.

This section is for useful macro files that support printer setup, maintenance, or print workflow improvements.

## Compatibility warning

These macros are printer-specific. Do not copy a macro into another printer until you verify the printer model, bed size, homing behavior, purge location, and Klipper configuration.

The current start and end macros are written for the FLSUN S1. The end macro uses delta-style center and circular cooling movement based on the configured toolhead limits. The start macro uses an FLSUN S1 side purge position with negative X movement. Those coordinates can be wrong or unsafe on a different printer.

## Current files

- `FLSUN S1 Start Purge.cfg`
- `FLSUN S1 Spiral Cooling End Print.cfg`
- [Mainsail Config and Macros Basics](./Mainsail-Config-and-Macros.md)

## Macro descriptions

- `FLSUN S1 Start Purge.cfg`: Homes the printer, heats the bed first and waits for it to reach target temperature, then heats the hotend, enables the extruder, lifts Z, moves to the side purge position, and performs the initial purge before printing.
- Compatibility: FLSUN S1 only unless you review and adjust the purge coordinates, bed limits, temperatures, and slicer start-gcode parameters for your own printer.
- Start macro video demo: [YouTube Shorts](https://www.youtube.com/shorts/ZUa5L6KtgqE)
- `FLSUN S1 Spiral Cooling End Print.cfg`: Retracts filament, lifts Z, turns off the hotend, starts the part cooling fan, runs a circular cooling orbit over the bed, turns the fan off, returns to center, and homes the printer.
- Compatibility: FLSUN S1 / delta-style Klipper setup only unless you review and adjust the toolhead limits, cooling radius, homing behavior, and any custom bed-heater variables for your own printer.
- End macro video demo: [YouTube Shorts](https://youtube.com/shorts/EiTJ1vDjeCI?feature=share)

## Recommended macro notes

For each macro, include:

- What printer or firmware it targets
- Where the macro should be added
- Any required variables or dependencies
- Warnings about printer-specific behavior
