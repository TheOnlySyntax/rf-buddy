# Hardware & Wiring

## Bill of materials
- **ESP32-C3** dev board (native USB, 4 MB flash) — e.g. ESP32-C3-DevKitM-1 /
  Super Mini.
- **CC1101** sub-GHz module (optionally an *amplified* CC1101 with PA/LNA).
- **SSD1306** 128×64 OLED, I²C.
- **Analog joystick** (2-axis potentiometer + push switch), e.g. KY-023.
- Antenna tuned for your band (433 / 315 / 868 MHz).

## Pinout (default `config.h`)

| Signal | GPIO | Notes |
|---|---|---|
| OLED SDA | 8 | I²C data |
| OLED SCL | 9 | I²C clock (addr `0x3C`) |
| CC1101 SCK | 4 | SPI clock |
| CC1101 MOSI | 6 | SPI MOSI |
| CC1101 MISO | 5 | SPI MISO (also CC1101 "ready") |
| CC1101 CS | 7 | chip select |
| CC1101 GDO0 | 20 | async data in/out |
| CC1101 PA (T/R) | 2 | **amplified module only** — HIGH on TX, LOW on RX/idle |
| Joystick VRx | 0 | left / right (ADC) |
| Joystick VRy | 1 | up / down (ADC) |
| Joystick SW | 10 | push = OK; hold = Back |

## Amplified CC1101 (PA/LNA control)
If your CC1101 board has a power amplifier + LNA with a T/R (transmit/receive)
switch, wire its enable to **GPIO2**. The firmware drives it automatically,
everywhere:
- **TX** → GPIO2 **HIGH** (3.3 V) → PA path enabled.
- **RX / idle** → GPIO2 **LOW** (0 V) → LNA/receive path.

If you use a plain (non-amplified) CC1101, GPIO2 is simply unused — leave it
disconnected.

## Joystick calibration
The centre of each axis is auto-calibrated at boot (hold the stick centred
while powering on). Axis polarity is fixed in `config.h`; if directions feel
swapped, that is where they are defined.

## Notes
- The ESP32-C3 uses **native USB** (Serial/JTAG), so it appears as a COM port
  directly — no external USB-UART chip.
- CC1101 `MISO` doubles as the "chip ready" line and must be connected.
- Keep the antenna attached before transmitting to avoid stressing the PA.
