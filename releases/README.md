# Releases (firmware .bin)

Closed-source firmware — only binaries are published, under the repository's
**Releases** tab (not committed into the repo tree).

## Files

- **`firmware-merged.bin`** — complete image for the **first flash over USB**
  (contains bootloader + partition table + boot_app0 + application).
  ```
  esptool --chip esp32c3 write-flash 0x0 firmware-merged.bin
  ```
  (COM port as needed: `--port COM5`.)

- **`firmware.bin`** — application partition only, for **OTA update over Wi‑Fi**
  (Home → Wi‑Fi → File Transfer → Firmware update, or FW from GitHub).

## Caution

- Switching to this layout (two OTA slots) **wipes saved `.sub` files once**.
- Do not power off the device during flashing.
