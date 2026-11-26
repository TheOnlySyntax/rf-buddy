# FAQ

**Is this a Flipper Zero?**
No. It's independent firmware for an ESP32-C3 + CC1101 build that borrows the
Flipper/Momentum UI style. Not affiliated with Flipper Devices.

**Is the source available?**
No — this repository provides prebuilt firmware (`.bin`) and documentation only.

**Which frequencies are supported?**
300–928 MHz via the CC1101 (common bands 315 / 433.92 / 868 MHz). Actual legal
use depends on your region.

**Can it open my car / garage?**
Fixed-code remotes can be replayed or brute-forced. Modern rolling-code systems
(KeeLoq, Security+ 2.0, most cars) cannot be opened by replay — that's the point
of rolling codes.

**Does TPMS compose really spoof a sensor?**
It builds a valid frame for the chosen protocol with your ID/pressure/temp, and
a receiver (or this device) decodes it back to those values. Some protocols
have field limits. Test only on your own vehicle.

**Why does BLE turn my Wi-Fi off?**
The ESP32-C3 shares memory/radio between Wi-Fi and BLE. BLE tools disable Wi-Fi
temporarily to give the Bluetooth controller enough RAM, and restore it on exit.

**Can I control it from a PC?**
Yes — a full [serial CLI](Serial-CLI.md) exposes navigation, RX/TX, files,
POCSAG, TPMS compose, jammer and Wi-Fi scan over USB at 115200 baud.

**Is any of this legal?**
Receiving is usually fine; transmitting, jamming, spoofing and BLE/Wi-Fi spam
are regulated and often illegal outside a controlled, authorised setting. You
are responsible for compliance.
