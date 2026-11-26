# Firmware OTA Update (přes Wi‑Fi)

Aktualizace firmwaru přes Wi‑Fi bez USB kabelu. Zařízení má dva app sloty
(ota_0 / ota_1); nový firmware se zapíše do neaktivního slotu a po restartu
naběhne. Když se nový obraz nepovede, zůstává předchozí slot nedotčený.

**Otevření:** Home → **Wi‑Fi → File Transfer** → sekce *Firmware update (OTA)*.

## Postup

1. Otevři **Wi‑Fi → File Transfer**, připoj se k AP zařízení a otevři
   `http://192.168.4.1`.
2. V sekci **Firmware update (OTA)** vyber soubor `firmware.bin`
   (ne merged.bin — jen samotná aplikace).
3. Klikni **Flash OTA**. Ukáže se průběh v procentech.
4. Po dokončení se zařízení samo restartuje do nového firmwaru.

## OTA přímo z GitHubu (bez PC)

**Wi‑Fi → FW from GitHub** stáhne `firmware.bin` z kořene tvého GitHub repa
(stejné repo jako online databáze, viz `ghrepo`) a rovnou ho nainstaluje:

1. Nahraj `firmware.bin` do kořene repa (`https://github.com/<owner>/<repo>`).
2. Nastav repo: `ghrepo <owner/repo> [branch]` a domácí Wi‑Fi ve Wi‑Fi Setup.
3. **Wi‑Fi → FW from GitHub** → potvrď **OK** → zařízení stáhne a flashne
   s průběhem v % na displeji, pak se restartuje.

Tak můžeš vydávat updaty jen pushnutím `firmware.bin` do repa.

## Který soubor nahrát

- Pro OTA použij **`firmware.bin`** (jen app oddíl), ne `firmware-merged.bin`.
- `firmware-merged.bin` je určený pro první flash přes USB
  (`esptool write_flash 0x0 firmware-merged.bin`) — obsahuje bootloader +
  tabulku oddílů + aplikaci.

## Rozložení flash (4 MB)

| Oddíl | Offset | Velikost |
|---|---|---|
| nvs | 0x9000 | 20 KB |
| otadata | 0xE000 | 8 KB |
| app0 (ota_0) | 0x10000 | 1856 KB |
| app1 (ota_1) | 0x1E0000 | 1856 KB |
| spiffs (LittleFS) | 0x3B0000 | 320 KB |

## Poznámky

- Při přechodu na dvou‑slotové rozložení se **jednorázově smažou uložené
  `.sub`** (změna oddílu LittleFS). Dál už OTA soubory nemaže.
- Nevypínej zařízení během flashování.
