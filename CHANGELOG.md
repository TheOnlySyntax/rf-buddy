# Changelog

## Wi-Fi update

### Added
- **Wi-Fi File Transfer** (Home → Wi-Fi → File Transfer): zařízení spustí vlastní
  Wi-Fi AP + web portál na `http://192.168.4.1` — seznam / stažení / nahrání /
  mazání `.sub` souborů z telefonu nebo PC.
- **Firmware OTA Update** přes web portál: nahraj `firmware.bin`, zapíše se do
  druhého app slotu a zařízení se restartuje do nového firmwaru.
- **OTA přímo z GitHubu** (Home → Wi-Fi → FW from GitHub): stáhne `firmware.bin`
  z kořene repa (`ghrepo`) a sám flashne, s průběhem v % na displeji.
- **Online Database (GitHub)** (Home → Wi-Fi → Download DB): stažení `.sub` z
  veřejného GitHub repa přes HTTPS podle `index.txt`. Repo se nastaví serialem
  `ghrepo <owner/repo> [branch]`.
- Wi-Fi dlaždice na Home nově otevírá submenu: **Scanner / File Transfer /
  Download DB / Wi-Fi Setup**.
- Serial příkazy: `webportal on|off`, `ghrepo`, `open wifiap`, `open ghdb`.
- Sdílené jádro `wifi_net` (BLE off + uvolnění 48KB CC1101 bufferu) pro všechny
  Wi-Fi funkce.

### Fixed
- **Wi-Fi scan „No networks" / zamrznutí na nule.** Scan neměl souvislou RAM,
  protože 48KB CC1101 capture buffer (`cap_`) ji zabíral. Wi-Fi recon i
  `wifiscan` nově buffer uvolní (stejně jako to dělá BLE) → scan funguje.

### Changed
- **Rozložení flash → dva OTA app sloty** (nutné pro OTA):
  `app0`/`app1` = 1856 KB každý, LittleFS = 320 KB.
  ⚠️ Přechod jednorázově smaže uložené `.sub` (změna oddílu LittleFS).
- Firmware `firmware.bin` ≈ 1,55 MB (slot 1,75 MB).

### Flashing
- První flash přes USB: `esptool write_flash 0x0 firmware-merged.bin`.
- Další updaty: OTA přes Wi-Fi (nahraj `firmware.bin` ve File Transfer).
