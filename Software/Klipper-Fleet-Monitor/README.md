# Klipper Fleet Monitor

Klipper Fleet Monitor is a read-only Windows app for watching multiple Klipper printers from one screen.

It is designed for simple fleet visibility without printer control buttons. Add each printer manually by Moonraker IP or URL, then view status, temperatures, progress, remaining time, and print pricing tools from a desktop dashboard.

## Download

- [Download Klipper Fleet Monitor for Windows](./Klipper%20Fleet%20Monitor%20Setup%200.1.0.exe)

## What It Does

- Shows all added Klipper printers on one dashboard
- Opens a detail view for each printer
- Shows current status, job name, progress, nozzle temp, bed temp, elapsed time, and remaining time
- Includes a print pricing calculator
- Shows a phone access link while the desktop app is running
- Stores printer settings locally on the computer

## What It Does Not Do

- No pause, cancel, restart, upload, macro, or control buttons
- No cloud service
- No automatic printer discovery

## Setup

1. Download the Windows installer.
2. Run the installer and open Klipper Fleet Monitor.
3. Click **Add Printer**.
4. Enter the printer name and Moonraker IP or URL.

Examples:

```text
192.168.1.50
http://192.168.1.50
```

5. Repeat for each Klipper printer.

## Phone Access

The phone does not run the Windows app. The Windows app runs on your computer and shows a local phone link, such as:

```text
http://192.168.1.25:8080
```

To use it on a phone:

1. Keep Klipper Fleet Monitor open on the computer.
2. Connect the phone to the same Wi-Fi/network.
3. Open the phone link in the phone browser.
4. Use the browser menu to add it to the home screen.

If the computer app is closed, the phone link will stop working.

## Requirements

- Windows PC on the same network as the printers
- Klipper printers using Moonraker
- Printer IP addresses or Moonraker URLs

## Notes

Some antivirus or Windows SmartScreen warnings may appear because this is an unsigned community app. Review the source project and only run downloads you trust.
