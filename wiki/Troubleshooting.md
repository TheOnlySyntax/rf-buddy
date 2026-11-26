# Troubleshooting

## Boot loop / display stays dark right after flashing
Symptom (on serial):
```
esp_image: Image length ... doesn't fit in partition length ...
No bootable app partitions
```
Cause: an app-only image flashed against the wrong (too-small) partition table.
**Fix:** flash the **merged** image (`firmware-merged.bin`) at `0x0`; it carries
the correct 2 MB-app partition table. See [Flashing](Flashing.md).

## COM port disappears / "Could not open COMx, port is busy"
The native-USB C3 port can drop during a crash, a transmit, or a stalled flash.
**Fix:** unplug and replug the USB cable (or tap RESET), wait for the port to
re-enumerate, then retry.

## `CC1101 ... -> version=0x14 OK` but nothing receives
- Check antenna and that you're on the right **frequency** and **modulation**
  for the target (OOK vs 2-FSK).
- Weak/distant signals need a good antenna; an amplified CC1101 (LNA) helps.
- Close range can saturate the receiver — back off ~1 m.

## CC1101 not detected (`partnumber`/`version` wrong or 0)
SPI wiring problem. Verify SCK=4, MOSI=6, MISO=5, CS=7 and that **MISO** (also
the "ready" line) is connected. Check 3.3 V power and ground.

## BLE shows "Low memory"
The Bluetooth controller couldn't get enough RAM. The firmware already turns
Wi-Fi off and frees the capture buffer on entry; if it still fails, reboot the
device and open BLE first (before heavy Wi-Fi use).

## Wi-Fi scan returns 0 / fails after using BLE
BLE and Wi-Fi share one radio. After a BLE session, leave BLE (which restores
Wi-Fi) before scanning; if needed, reboot.

## TX says "radio busy" / "radio in use"
The CC1101 is single-user. Stop any running RX, Toolkit schedule, Chat or TX
before starting a new transmission.

## Transmitted a TPMS/remote frame but the target didn't react
- Rolling-code targets reject replays by design.
- Wrong region frequency (315 vs 433) or modulation.
- Some composed TPMS fields saturate outside a protocol's real range.
