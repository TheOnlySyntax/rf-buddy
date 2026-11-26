# Main Menu & Navigation

## Joystick
| Action | Effect |
|---|---|
| Up / Down / Left / Right | move / change value |
| Push (short) | **OK** / select |
| Push (hold) | **Back** |
| Long OK | context action (e.g. toggle hopping in Read) |

## Home launcher
On boot you land on the **Home** launcher — a 2×2 grid:

| Tile | Opens |
|---|---|
| **Wi-Fi** | [Wi-Fi Recon](WiFi-Recon.md) (AP scan) |
| **BLE** | [BLE Tools](BLE-Tools.md) (scanner + spam submenu) |
| **Sub-GHz** | the Sub-GHz menu (below) |
| **Settings** | device settings (Wi-Fi, brightness, radio, diagnostics, about) |

The top-right corner shows Wi-Fi signal bars when connected.

## Sub-GHz menu
A 2×2 grid of core receivers plus a footer:

| Item | Opens |
|---|---|
| **READ** | [Read](Read.md) — auto-decode receiver |
| **RAW** | [Read RAW](Read-RAW.md) |
| **SAVED** | [Saved files](Saved.md) |
| **SCAN** | [Frequency Analyzer](Frequency-Analyzer.md) |
| **Settings** | radio / display / diagnostics |
| **Tools** | the Tools submenu (below) |

## Tools submenu
Sub-GHz Toolkit · TPMS · Add Manually · Advanced Add · Jammer · Brute Force ·
POCSAG Pager · Sub-GHz Chat · Weather Station · Signal Hunter · Tesla Tools.

## Tips
- The header usually shows the current **frequency** and **preset/modulation**.
- Every screen can also be opened and driven over USB — see
  [Serial CLI](Serial-CLI.md) (`open <app>` + `key …`).
