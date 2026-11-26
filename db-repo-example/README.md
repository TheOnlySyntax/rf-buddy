# SubGHz online database (example repo)

Tenhle adresář je **šablona GitHub repozitáře**, ze kterého si zařízení
SubGHz ESP32‑C3 stahuje `.sub` soubory přes WiFi (Home → **Wi‑Fi → Download DB**).

## Jak to zprovoznit

1. Vytvoř si **veřejný** GitHub repozitář (např. `tvojejmeno/subghz-db`).
2. Nahraj do něj obsah tohoto adresáře:
   - `index.txt` — seznam souborů (jeden `.sub` na řádek).
   - `files/` — samotné `.sub` soubory.
3. V zařízení nastav repo přes sériovou linku (COM5, 115200):
   ```
   ghrepo tvojejmeno/subghz-db main
   ```
   (`main` je větev; když ji vynecháš, použije se `main`.)
4. Na zařízení otevři **Wi‑Fi → Download DB**. Zařízení se připojí k uložené
   domácí WiFi (nastav ji ve **Wi‑Fi → Wi‑Fi Setup**), stáhne `index.txt`,
   zobrazí seznam a vybraný soubor uloží do `/subghz`.

## Formát `index.txt`

- Jeden soubor na řádek, cesta **relativní ke kořenu repa**.
- Řádky začínající `#` a prázdné řádky se ignorují.
- Zařízení stahuje z:
  `https://raw.githubusercontent.com/<owner>/<repo>/<branch>/<cesta>`

Příklad:
```
# garážová vrata
files/garage/came_12bit.sub
files/garage/nice_flo.sub
# auta
files/cars/tpms_toyota.sub
```

## Poznámka

- Stahuj a vysílej jen signály z **vlastních / autorizovaných** zařízení.
- `.sub` soubory jsou drobné; úložiště zařízení (LittleFS ~320 KB) jich pojme stovky.
