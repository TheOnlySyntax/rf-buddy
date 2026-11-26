# Online Database (GitHub)

Download `.sub` files from a public GitHub repository straight to the device
over Wi‑Fi (HTTPS). You create the repo yourself — it is your signal database.

**Open:** Home → **Wi‑Fi → Download DB**.

## Repository setup

1. Create a **public** GitHub repository (e.g. `yourname/subghz-db`) following the
   template in `db-repo-example/` (contains `index.txt` and `files/`).
2. Point the device at the repo over the serial line (COM5, 115200):
   ```
   ghrepo yourname/subghz-db main
   ```
   With no arguments `ghrepo` prints the current setting.
3. Set the home Wi‑Fi in **Wi‑Fi → Wi‑Fi Setup** (internet required).

## Usage

1. Home → **Wi‑Fi → Download DB**.
2. The device connects to the saved Wi‑Fi, downloads `index.txt` and shows the list.
3. Pick a file and press **OK** — it is saved to `/subghz` and appears in **Saved**.

## `index.txt` format

One `.sub` per line, path relative to the repo root; `#` = comment.
The device downloads from
`https://raw.githubusercontent.com/<owner>/<repo>/<branch>/<path>`.

```
# example
files/garage/came_12bit.sub
files/cars/tpms_toyota.sub
```

## Notes

- The HTTPS certificate is not verified (`setInsecure`) — it saves RAM on the C3.
- The online database (STA) and File Transfer (AP) each run separately.
- Only download / transmit signals for devices you own or are authorized to test.
