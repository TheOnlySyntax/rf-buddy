# Firmware OTA Update (over Wi‑Fi)

Update the firmware over Wi‑Fi without a USB cable. The device has two app slots
(ota_0 / ota_1); the new firmware is written to the inactive slot and boots after
a restart. If the new image fails, the previous slot stays untouched.

**Open:** Home → **Wi‑Fi → File Transfer** → *Firmware update (OTA)* section.

## Steps

1. Open **Wi‑Fi → File Transfer**, connect to the device AP and open
   `http://192.168.4.1`.
2. In **Firmware update (OTA)** pick `firmware.bin`
   (not merged.bin — just the application).
3. Click **Flash OTA**. A percentage progress bar is shown.
4. When finished, the device reboots itself into the new firmware.

## OTA straight from GitHub (no PC)

**Wi‑Fi → FW from GitHub** downloads `firmware.bin` from the root of your GitHub
repo (the same repo as the online database, see `ghrepo`) and installs it directly:

1. Upload `firmware.bin` to the repo root (`https://github.com/<owner>/<repo>`).
2. Set the repo: `ghrepo <owner/repo> [branch]` and the home Wi‑Fi in Wi‑Fi Setup.
3. **Wi‑Fi → FW from GitHub** → confirm **OK** → the device downloads and flashes
   with a % progress bar on the display, then restarts.

This way you can ship updates just by pushing `firmware.bin` to the repo.

## Which file to upload

- For OTA use **`firmware.bin`** (application partition only), not `firmware-merged.bin`.
- `firmware-merged.bin` is for the first flash over USB
  (`esptool write_flash 0x0 firmware-merged.bin`) — it contains the bootloader +
  partition table + application.

## Flash layout (4 MB)

| Partition | Offset | Size |
|---|---|---|
| nvs | 0x9000 | 20 KB |
| otadata | 0xE000 | 8 KB |
| app0 (ota_0) | 0x10000 | 1856 KB |
| app1 (ota_1) | 0x1E0000 | 1856 KB |
| spiffs (LittleFS) | 0x3B0000 | 320 KB |

## Notes

- Switching to the two-slot layout **wipes saved `.sub` files once**
  (LittleFS partition change). After that OTA never deletes files.
- Do not power off the device during flashing.
