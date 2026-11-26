# Serial CLI

Full USB control. Port appears as a COM device (native USB), **115200 baud**,
line-based (`\n`). Responses start with `>>`; multi-line blocks end with `<<`.
Type `help` or `?` for the list, `help <cmd>` for one.

## General / status
| Command | Description |
|---|---|
| `help [cmd]` / `?` | list commands / one command's help |
| `status` | version, screen, depth, freq, preset, rx/tx, samples |
| `ping` | firmware version + scene depth |
| `power` | display brightness & dim status |
| `shot` | dump OLED framebuffer as hex (`>>OLED w h` … `<<OLED`) |

## Navigation (drives any app)
| Command | Description |
|---|---|
| `open <app>` | switch screen / open any app |
| `key U\|D\|L\|R\|O\|K\|B` | joystick: Up/Down/Left/Right, O=OK, **K=OK long**, **B=Back** |

`open` targets: `home menu read raw saved analyzer settings power tpms toolkit
hunter pocsag jammer brute chat weather tesla wifi ble`.

## Receive / decode
| Command | Description |
|---|---|
| `rx start` / `rx stop` | start/stop decoded RX (Read) |
| `freq [Hz]` | get/set RX frequency |
| `fsk [0\|1]` | modulation 0=OOK, 1=2-FSK |
| `rssi` | signal strength (dBm) |
| `lastdec` / `clrdec` | last decoded result / clear |
| `dumpraw` · `rawslice <off>` · `rawstats` | inspect the RAW capture buffer |
| `scan [start\|stop]` | frequency analyzer control/read |

## RAW record
| Command | Description |
|---|---|
| `raw start` / `raw stop` | record RAW |
| `raw save <name>` | save recording as `.sub` |

## Files (LittleFS `/subghz`)
| Command | Description |
|---|---|
| `list` | list `.sub` files |
| `check <name>` | validate `.sub` header/fields |
| `rawinfo <name>` | RAW file info |
| `export <offset> <name>` | download bytes (hex) |
| `delete <name>` · `rename <old> <new>` | manage files |

## Sub-GHz TX
| Command | Description |
|---|---|
| `tx "<proto>" <freqHz> <bit> <keyHex> [te= key2= seed= manuf=]` | encode & transmit |
| `txbuild "<proto>" <freqHz> <bit> <keyHex> [..]` | build waveform, no TX |
| `txslice <offset>` | read up to 32 samples from last build |

Example: `tx "CAME" 433920000 12 000000000000064B`

## POCSAG
| Command | Description |
|---|---|
| `pocsagtx <freqHz> <devHex> <baud> <addr> <func> <text>` | transmit POCSAG |
| `pocsagbuild <512\|1200> <addr> <func> <text>` | build only |

Example: `pocsagtx 439987500 24 1200 1234567 3 HELLO`

## TPMS compose (spoof)
| Command | Description |
|---|---|
| `tpmslist` | list all TPMS protocols |
| `tpmstx "<proto>" <idHex> <kPa> <tempC> [315\|433]` | compose & transmit |
| `tpmsbuild "<proto>" <idHex> <kPa> <tempC>` | build only (read via `txslice`) |

Example: `tpmstx "toyota" 1A2B3C4D 240 21 433`

## Jammer / Wi-Fi
| Command | Description |
|---|---|
| `jammer on [freqHz]` / `jammer off` | continuous-carrier jammer |
| `wifiscan` | scan & list APs: `channel RSSI auth SSID` |

## Driving interactive apps (open + key)
Apps without a one-shot command are driven with `open <app>` then `key …`:
- **Jammer:** `open jammer` → `key O` select → `key O` start/stop (or `jammer on`).
- **Brute Force:** `open brute` → `key U/D` pick → `key O` enter → `key O` Start.
- **Chat:** `open chat` → set key/freq → `key O`.
- **Weather / Tesla:** `open weather` / `open tesla` → set values → `key O`.
- **Signal Hunter:** `open hunter` → `key O` pause/start, `key U/D` threshold.
- **BLE:** `open ble` → `key U/D` pick mode → `key O`.
- **TPMS UI:** `open tpms` → `key D` to Compose → `key O` … (or `tpmstx`).

## Notes
- The CC1101 is a **single resource**; a running RX/TX/Toolkit/Chat blocks other
  TX with `>>ERR radio busy`.
- Use `tx`/`tpmstx`/`pocsagtx`/`jammer`/replay only on authorised hardware.
