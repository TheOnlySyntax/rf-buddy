# Releases (firmware .bin)

Closed-source firmware — only binaries are published here.

## Soubory

- **`firmware-merged.bin`** — kompletní obraz pro **první flash přes USB**
  (obsahuje bootloader + tabulku oddílů + boot_app0 + aplikaci).
  ```
  esptool --chip esp32c3 write-flash 0x0 firmware-merged.bin
  ```
  (COM port podle potřeby: `--port COM5`.)

- **`firmware.bin`** — jen aplikační oddíl, pro **OTA update přes Wi‑Fi**
  (Home → Wi‑Fi → File Transfer → Firmware update, nebo FW from GitHub).

## Pozor

- Přechod na toto rozložení (dva OTA sloty) **jednorázově smaže uložené `.sub`**.
- Nevypínej zařízení během flashování.
