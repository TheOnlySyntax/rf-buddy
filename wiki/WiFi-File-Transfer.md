# Wi‑Fi File Transfer

Transfer `.sub` files between the device and a phone/PC over the device's own
Wi‑Fi access point — no cable, no router.

**Open:** Home → **Wi‑Fi → File Transfer**.

## How it works

1. The device starts its own Wi‑Fi AP and shows on the display:
   - **AP** — network name (e.g. `SubGHz-1A2B`),
   - **Pass** — password (stable, derived from the chip ID),
   - **http://192.168.4.1** — the portal address.
2. Connect your phone/PC to that Wi‑Fi network.
3. Open `http://192.168.4.1` in a browser.
4. In the portal you can:
   - see the list of saved `.sub` files and **download** them,
   - **upload** new `.sub` files to the device (saved to `/subghz`),
   - **delete** files,
   - upload **firmware (OTA)** — see [Firmware OTA Update](Firmware-OTA-Update).

## Notes

- AP mode runs instead of a connection to the home Wi‑Fi (STA). For the online
  database (which needs internet) use **Download DB** — that runs in STA mode.
- The portal and BLE share RAM; if memory is low, close BLE first.
- Serial equivalent: `webportal on` / `webportal off`.
