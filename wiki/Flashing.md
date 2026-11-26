# Flashing

The firmware is distributed as a **merged image** (`firmware-merged.bin`) that
already contains the bootloader, the custom 2 MB-app partition table and the
application. Flash it at offset **`0x0`**.

## Option A — esptool (CLI)
Install esptool (`pip install esptool`), then:
```bash
esptool.py --chip esp32c3 --port COM5 --baud 460800 write_flash 0x0 firmware-merged.bin
```
Replace `COM5` with your port (`/dev/ttyACM0` on Linux, `/dev/tty.usb*` on
macOS).

## Option B — browser (no install)
Use an ESP Web Tools / esptool-js based web flasher (Chrome/Edge):
1. Connect the board, click **Connect**, choose the serial port.
2. Flash `firmware-merged.bin` at address `0x0`.

## Entering download mode
Native-USB C3 boards usually flash without any button. If flashing fails:
1. Hold **BOOT**, tap **RESET**, release **BOOT**, then flash.
2. Some boards enter download mode automatically via esptool.

## After flashing
- Open a serial monitor at **115200 baud**. You should see:
  ```
  === Sub-GHz ESP32-C3 | type help ===
  [subghz] begin() CC1101 ... -> OK
  ```
- `CC1101 ... -> OK` confirms the radio is detected over SPI.

## Partition / size notes
The app needs a **2 MB** application slot (the default 1.25 MB is too small and
causes a boot loop — "image doesn't fit in partition"). The merged image bakes
in the correct partition table, so flashing at `0x0` is all you need. If you
ever flash only an app image, you must also flash the matching partition table.

## Recovery
- **Boot loop / blank screen right after flashing** → you flashed an app-only
  image against the wrong partition table. Re-flash the **merged** image at
  `0x0`. See [Troubleshooting](Troubleshooting.md).
- **Port disappears mid-flash** → unplug/replug USB and retry; see
  [Troubleshooting](Troubleshooting.md).
