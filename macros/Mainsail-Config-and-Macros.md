# Mainsail Basics: Editing Config and Finding Macros

This guide explains the basics of editing your Klipper config in Mainsail and where to find macros.

## Editing config files in Mainsail

In Mainsail, your printer config files are usually edited through the file manager and built-in editor.

### How to open the config files

1. Open Mainsail in your browser.
2. In the left sidebar, open the file area for your printer.
3. Look for your main Klipper config file, usually `printer.cfg`.
4. Click the file to open it in the editor.

If your setup uses included files, you may also see files such as:

- `mainsail.cfg`
- `macros.cfg`
- `hardware.cfg`
- `steppers.cfg`
- `fans.cfg`

Your printer may use one big config file or several smaller ones.

## How to make changes safely

Basic safe workflow:

1. Open the file you want to edit.
2. Make a small change.
3. Click `Save` or `Save & Restart`.
4. Watch the console for errors.

If Mainsail shows an error after saving:

- read the error message carefully
- reopen the file
- fix the mistake
- save again

## Save vs Save & Restart

Mainsail supports normal saving and also `Save & Restart` behavior for Klipper config files.

In Mainsail editor settings, the restart method can be set to:

- `RESTART`
- `FIRMWARE_RESTART`

For most normal config edits, people usually use `Save & Restart` so Klipper reloads the config right away.

## Where macros are usually stored

Macros are usually found in one of these places:

- directly inside `printer.cfg`
- inside a separate file like `macros.cfg`
- inside `mainsail.cfg`
- inside another included config file

If your `printer.cfg` has lines like this:

```ini
[include macros.cfg]
[include mainsail.cfg]
```

that means the macros may be stored in those files instead of the main config.

## How to identify a macro

Macros in Klipper usually look like this:

```ini
[gcode_macro LOAD_FILAMENT]
gcode:
  M83
  G1 E50 F300
```

The important part is the section header:

```ini
[gcode_macro MACRO_NAME]
```

That tells you it is a macro.

## Where to find macros in the Mainsail interface

Mainsail can show macros on the dashboard as macro buttons.

Depending on your settings, macros may appear:

- in a single macro panel
- grouped into custom macro sections
- hidden from the dashboard if you chose to hide them

If you do not see a macro on the dashboard, that does not always mean it is missing from config.

## Why some macros do not show up

According to the Mainsail docs, some macros are hidden automatically, including:

- macros whose names start with an underscore
- macros that use `rename_existing`

This is normal behavior in Mainsail.

Example:

```ini
[gcode_macro _MY_HIDDEN_HELPER]
gcode:
  M117 Hidden helper
```

That macro can still exist in config, but it may not appear as a button in Mainsail.

## How to search for macros

If you are not sure where a macro lives:

1. Open `printer.cfg`
2. Check the `[include ...]` lines near the top
3. Open the included files one by one
4. Look for sections that begin with `[gcode_macro ...]`

That is the easiest way to track down macros in a split config setup.

## Good beginner tips

- Make one change at a time
- Save often
- Keep macros in a separate file if your config starts getting crowded
- Use clear macro names
- Test macros from the console after editing them

## Running a macro manually

You can run a macro from:

- the Mainsail dashboard macro button
- the Mainsail console

If your macro is named:

```ini
[gcode_macro LOAD_FILAMENT]
```

you can run it in the console by typing:

```text
LOAD_FILAMENT
```

## Official references

This guide is based on the official Mainsail documentation:

- [Mainsail Editor](https://docs.mainsail.xyz/overview/settings/editor)
- [Mainsail Macros](https://docs.mainsail.xyz/overview/settings/macros)
- [Hide macros in Mainsail](https://docs.mainsail.xyz/overview/features/hide-macros-outputs-or-fans)
- [Mainsail Console](https://docs.mainsail.xyz/overview/features/console)
