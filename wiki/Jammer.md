# Jammer

Transmits a continuous carrier / noise on a chosen frequency to block nearby
sub-GHz receivers. **Highly regulated — authorised testing only.**

## Use
1. Open **Jammer** from Tools.
2. Bottom bar: **Edit · Start/Stop · Mode** — move the cursor with
   **Left/Right** and press **OK** to activate the highlighted button.
   - **Edit** → set frequency.
   - **Start/Stop** → begin/stop jamming.
   - **Mode** → cycle modulation preset.

## Modes
- `OOK 650 kHz`, `OOK 270 kHz`, `2FSK 238 kHz`, `2FSK 476 kHz`.

## Serial
- `jammer on [freqHz]` — start (default 433.92 MHz).
- `jammer off` — stop.

## Notes
- Jamming denies service to everyone on that band, including safety and vehicle
  systems. Illegal in most places outside a shielded lab. You are responsible.
