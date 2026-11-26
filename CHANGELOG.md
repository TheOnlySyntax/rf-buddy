# Changelog

## Wi-Fi update

### Added
- **Wi-Fi File Transfer** (Home → Wi-Fi → File Transfer): the device starts its own
  Wi-Fi AP + web portal at `http://192.168.4.1` — list / download / upload /
  delete `.sub` files from a phone or PC.
- **Firmware OTA Update** via the web portal: upload `firmware.bin`, it is written
  to the second app slot and the device reboots into the new firmware.
- **OTA straight from GitHub** (Home → Wi-Fi → FW from GitHub): downloads
  `firmware.bin` from the repo root (`ghrepo`) and flashes it itself, with a
  percentage progress bar on the display.
- **Online Database (GitHub)** (Home → Wi-Fi → Download DB): download `.sub` files
  from a public GitHub repo over HTTPS using `index.txt`. Configure the repo over
  serial with `ghrepo <owner/repo> [branch]`.
- The Wi-Fi tile on Home now opens a submenu: **Scanner / File Transfer /
  Download DB / Wi-Fi Setup**.
- Serial commands: `webportal on|off`, `ghrepo`, `open wifiap`, `open ghdb`.
- Shared `wifi_net` core (BLE off + release of the 48 KB CC1101 buffer) for all
  Wi-Fi features.

### Fixed
- **Wi-Fi scan "No networks" / stuck at zero.** The scan had no contiguous RAM
  because the 48 KB CC1101 capture buffer (`cap_`) was holding it. Wi-Fi recon and
  `wifiscan` now release the buffer (the same way BLE does) → scan works.

### Changed
- **Flash layout → two OTA app slots** (required for OTA):
  `app0`/`app1` = 1856 KB each, LittleFS = 320 KB.
  ⚠️ Switching to it wipes saved `.sub` files once (LittleFS partition change).
- Firmware `firmware.bin` ≈ 1.8 MB (slot 1856 KB).

### Flashing
- First flash over USB: `esptool write_flash 0x0 firmware-merged.bin`.
- Further updates: OTA over Wi-Fi (upload `firmware.bin` in File Transfer).
