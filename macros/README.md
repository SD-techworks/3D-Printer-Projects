# Macros

A collection of printer and Klipper macros.

This section is for useful macro files that support printer setup, maintenance, or print workflow improvements.

## Current files

- `FLSUN S1 Start Purge.cfg`
- `FLSUN S1 Spiral Cooling End Print.cfg`
- [Mainsail Config and Macros Basics](./Mainsail-Config-and-Macros.md)

## Macro descriptions

- `FLSUN S1 Start Purge.cfg`: Homes the printer, heats the bed first and waits for it to reach target temperature, then heats the hotend, enables the extruder, lifts Z, moves to the side purge position, and performs the initial purge before printing.
- Start macro video demo: [YouTube Shorts](https://www.youtube.com/shorts/ZUa5L6KtgqE)
- `FLSUN S1 Spiral Cooling End Print.cfg`: Retracts filament, lifts Z, turns off the hotend, starts the part cooling fan, runs a circular cooling orbit over the bed, turns the fan off, returns to center, and homes the printer.
- End macro video demo: [YouTube Shorts](https://youtube.com/shorts/EiTJ1vDjeCI?feature=share)

## Recommended macro notes

For each macro, include:

- What printer or firmware it targets
- Where the macro should be added
- Any required variables or dependencies
- Warnings about printer-specific behavior
