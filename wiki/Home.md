# SubGHz ESP32-C3 — Wiki

[← Project README and UI gallery](../README.md#ui-gallery)

Full manual for the firmware. Screens show the OLED UI with sample data.

## Getting started
- [Hardware & Wiring](Hardware-and-Wiring.md) — parts, pinout, amplified CC1101
- [Flashing](Flashing.md) — write the `.bin`, drivers, recovery
- [Main Menu & Navigation](Main-Menu-and-Navigation.md) — joystick, launcher, screens

## Receive
- [Read (Receiver)](Read.md) — auto-decode ~90 protocols, Send/Save
- [Read RAW](Read-RAW.md) — capture & replay raw waveforms
- [Frequency Analyzer / Band Scan](Frequency-Analyzer.md) — find active frequencies
- [Signal Hunter](Signal-Hunter.md) — auto-capture on RSSI trigger

## Transmit
- [Saved files](Saved.md) — info, decode RAW, Send (keyed & RAW), repeat
- [Brute Force](Brute-Force.md) — iterate fixed-code remotes
- [Jammer](Jammer.md) — continuous carrier
- [POCSAG Pager](POCSAG-Pager.md) — one inbox for received and sent pages

## TPMS
- [TPMS](TPMS.md) — live sensors, replay, and **full compose (spoof)**

## Tools
- [Sub-GHz Toolkit](Sub-GHz-Toolkit.md) — playlists, one-time scheduling, and activity
- [Weather Station](Weather-Station.md)
- [Tesla Tools](Tesla-Tools.md)
- [Sub-GHz Chat](Sub-GHz-Chat.md)

## Wi-Fi & BLE
- [Wi-Fi Recon](WiFi-Recon.md) — scan nearby access points
- [Wi-Fi File Transfer](WiFi-File-Transfer.md) — AP web portal: upload/download `.sub`
- [Firmware OTA Update](Firmware-OTA-Update.md) — flash new firmware over Wi-Fi
- [Online Database (GitHub)](Online-Database.md) — download `.sub` from your GitHub repo
- [BLE Tools](BLE-Tools.md) — scanner + advertising spam

## Reference
- [Serial CLI](Serial-CLI.md) — full command reference
- [Protocols](Protocols.md) — supported sub-GHz & TPMS protocols
- [Troubleshooting](Troubleshooting.md) — boot loops, COM drops, low memory
- [FAQ](FAQ.md)

---
⚠️ Use only on hardware you own or are authorised to test. Radio TX, jamming,
BLE/Wi-Fi spam and TPMS spoofing are regulated — know your local law.
