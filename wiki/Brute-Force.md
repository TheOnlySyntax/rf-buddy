# Brute Force

Iterates every code of a fixed-code remote (CAME, Nice FLO, Princeton, Holtek,
Chamberlain, Linear, Ansonic, SMC5326 …) on a chosen frequency. Only works
against **fixed-code** systems, never rolling-code.

## Use
1. Open **Brute Force** from Tools.
2. Pick a protocol + frequency entry from the list, **OK** to enter the RUN
   screen.
3. Bottom bar: **Cfg · Start/Stop · Rsn** — move with **Left/Right**, **OK**
   activates:
   - **Cfg** → set the **start code** (where to begin / where you stopped).
     Up/Down ±1, Left/Right ±256, OK confirm.
   - **Start/Stop** → run / pause the sweep from the current code.
   - **Rsn** → **resend the current single code** (the one you stopped on).
4. **Back (hold)** on the RUN screen returns to the protocol list.

## Display
Shows the protocol + bit length and progress `current/total`.

## Notes
- The sweep sends codes with a small gap between them; large key spaces take a
  while — use **Cfg** to resume rather than restart.
- For a single known code use the serial `tx` command instead.
