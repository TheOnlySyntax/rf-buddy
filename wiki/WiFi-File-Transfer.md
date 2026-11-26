# Wi‑Fi File Transfer

Přenos `.sub` souborů mezi zařízením a telefonem/PC přes vlastní Wi‑Fi
access point zařízení — bez kabelu, bez routeru.

**Otevření:** Home → **Wi‑Fi → File Transfer**.

## Jak to funguje

1. Zařízení spustí vlastní Wi‑Fi AP a na displeji ukáže:
   - **AP** — jméno sítě (např. `SubGHz-1A2B`),
   - **Pass** — heslo (stabilní, odvozené z chip ID),
   - **http://192.168.4.1** — adresa portálu.
2. Připoj telefon/PC k té Wi‑Fi síti.
3. Otevři v prohlížeči `http://192.168.4.1`.
4. V portálu můžeš:
   - vidět seznam uložených `.sub` a **stáhnout** je,
   - **nahrát** nové `.sub` do zařízení (uloží se do `/subghz`),
   - **smazat** soubory,
   - nahrát **firmware (OTA)** — viz [Firmware OTA Update](Firmware-OTA-Update).

## Poznámky

- AP režim běží místo připojení k domácí Wi‑Fi (STA). Pro online databázi
  (která potřebuje internet) použij **Download DB** — ta běží v STA režimu.
- Portál a BLE se dělí o RAM; když je málo paměti, zavři nejdřív BLE.
- Serial ekvivalent: `webportal on` / `webportal off`.
