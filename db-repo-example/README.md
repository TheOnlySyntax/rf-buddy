# SubGHz online database (example repo)

This directory is a **GitHub repository template** that the SubGHz ESP32‑C3
device downloads `.sub` files from over Wi‑Fi (Home → **Wi‑Fi → Download DB**).

## Setup

1. Create a **public** GitHub repository (e.g. `yourname/subghz-db`).
2. Upload the contents of this directory into it:
   - `index.txt` — file list (one `.sub` per line).
   - `files/` — the `.sub` files themselves.
3. Point the device at the repo over the serial line (COM5, 115200):
   ```
   ghrepo yourname/subghz-db main
   ```
   (`main` is the branch; if you omit it, `main` is used.)
4. On the device open **Wi‑Fi → Download DB**. It connects to the saved home
   Wi‑Fi (set it in **Wi‑Fi → Wi‑Fi Setup**), downloads `index.txt`, shows the
   list, and saves the selected file to `/subghz`.

## `index.txt` format

- One file per line, path **relative to the repo root**.
- Lines starting with `#` and blank lines are ignored.
- The device downloads from:
  `https://raw.githubusercontent.com/<owner>/<repo>/<branch>/<path>`

Example:
```
# garage doors
files/garage/came_12bit.sub
files/garage/nice_flo.sub
# cars
files/cars/tpms_toyota.sub
```

## Note

- Only download and transmit signals for devices you **own / are authorized** to test.
- `.sub` files are tiny; the device storage (LittleFS ~320 KB) holds hundreds of them.
