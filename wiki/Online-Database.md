# Online Database (GitHub)

Stahování `.sub` souborů z veřejného GitHub repozitáře přímo do zařízení
přes Wi‑Fi (HTTPS). Repo si vytváříš sám — je to tvoje databáze signálů.

**Otevření:** Home → **Wi‑Fi → Download DB**.

## Nastavení repozitáře

1. Vytvoř **veřejný** GitHub repozitář (např. `tvojejmeno/subghz-db`) podle
   šablony v `db-repo-example/` (obsahuje `index.txt` a `files/`).
2. Nastav repo v zařízení přes sériovou linku (COM5, 115200):
   ```
   ghrepo tvojejmeno/subghz-db main
   ```
   Bez argumentů `ghrepo` vypíše aktuální nastavení.
3. Nastav domácí Wi‑Fi ve **Wi‑Fi → Wi‑Fi Setup** (potřeba internet).

## Použití

1. Home → **Wi‑Fi → Download DB**.
2. Zařízení se připojí k uložené Wi‑Fi, stáhne `index.txt` a zobrazí seznam.
3. Vyber soubor a stiskni **OK** — stáhne se do `/subghz` a je hned v **Saved**.

## Formát `index.txt`

Jeden `.sub` na řádek, cesta relativní ke kořenu repa; `#` = komentář.
Zařízení stahuje z
`https://raw.githubusercontent.com/<owner>/<repo>/<branch>/<cesta>`.

```
# príklad
files/garage/came_12bit.sub
files/cars/tpms_toyota.sub
```

## Poznámky

- HTTPS certifikát se neověřuje (`setInsecure`) — šetří RAM na C3.
- Online databáze (STA) a File Transfer (AP) běží každá zvlášť.
- Stahuj/vysílej jen signály z vlastních / autorizovaných zařízení.
