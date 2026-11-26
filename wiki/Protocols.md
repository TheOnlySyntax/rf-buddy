# Protocols

## Sub-GHz (Read / decode, ~90)
The receiver auto-detects a large set of OOK and FSK remote/sensor protocols,
ported from the Flipper firmware and rtl_433. Highlights:

- **Gates/remotes:** CAME, CAME TWEE, CAME Atomo, Nice FLO/FloR-S, Ansonic,
  Princeton, Holtek / HT12x, Chamberlain (Cham_Code 7/8/9-bit), Linear,
  SMC5326, Hormann HSM, Roger, Hollarm, Nord ICE, Treadmill, KeyFinder …
- **Rolling code:** KeeLoq (+ manufacturers, AN-Motors, HCS101), Security+ 1.0
  & 2.0, BFT Mitto, Nice FloR-S, Faac SLH …
- **Sensors/other:** weather stations (Nexus-TH, Acurite 592TXR, GT-WT,
  inFactory), Schrader GG4, and more.

Decoded fields (where available): Bit length, Key (+ reversed "Yek"),
TE, manufacturer, and per-protocol breakdowns (serial, button, counter, DIP…).

> Fixed-code protocols can be replayed/brute-forced; rolling-code protocols
> cannot be opened by replay.

## TPMS (~38 decoders + compose encoders)
Schrader (plain, EG53MA4, SMD3MA4, MRXBC5A4, motorcycle), Renault (+0435R),
Citroen, Ford, Toyota, GM, Abarth 124, Honda, Kia, Hyundai VDO, Elantra 2012,
Nissan, BMW, BMW G3, Jansite (+ Solar, TY588, TY468), Porsche, Truck,
Mercedes-Benz, Sefis M3, PMV-107J, AVE, Airpuxem, Bmw, EGQ Q85, Gear/Hive,
Tyreguard 400, Smartire, EEZ RV, SP372, Steelmate, TRW, iMars T240 …

Every listed TPMS protocol has both a **decoder** (RX) and a **compose
encoder** (spoof TX). Use `tpmslist` over serial for the exact names the
`tpmstx` command expects.

## POCSAG
Standard POCSAG paging: 512 / 1200 / 2400 baud, FSK, BCH-protected address and
message codewords, 7-bit text.

## Modulations
OOK (AM650 / AM270) and 2-FSK (various deviations incl. the FM95 ≈ 9.5 kHz
pager preset). The active preset is shown in each screen's header.
