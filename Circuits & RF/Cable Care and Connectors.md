#circuits #electronics

**Half of all "mystery noise" and "flaky signals" is cables and connectors: the wrong coax for the job, connectors used past their rating, or an intermittent you haven't wiggled out yet.**

# Reference

**Coax quick table (50 Ω unless noted):**

| Cable | Use | Notes |
|---|---|---|
| RG-58 | everyday BNC runs | lossy: ~0.2 dB/m @ 100 MHz, ~0.7 dB/m @ 1 GHz; single braid leaks at RF |
| RG-223 / double-braid | pickup-sensitive analog | second shield buys ~20+ dB isolation |
| RG-316 | short jumpers in dense racks | thin and lossier; fine at 30 cm |
| Semi-rigid / hardline | phase-critical, microwave | phase-stable; bend once, correctly |
| RG-59/RG-6 (**75 Ω!**) | video/CCD | mates mechanically with 50 Ω BNC, mismatches electrically |

**Connectors:** BNC to ~1 GHz — the bayonet contact isn't a precise 50 Ω past that, and it gets microphonic; SMA to 18 GHz — **torque wrench, 0.9 N·m / 8 in·lb, turn the nut, never the body**; N-type for power and outdoors. Finger-tight SMA = reflections that drift with temperature.

**Handling:** bend radius ≥ ~10× diameter — a sharp kink permanently changes $Z_0$ and shielding. Strain-relieve at connectors; flexing changes electrical length, so **cable motion is phase noise** in interferometers and RF references. Cables on the floor die young.

**Intermittents:** the wiggle test is a legitimate instrument — watch the signal while flexing along the length and at every connector. Usual suspects: center-pin fatigue at the strain point, cold solder in a field-installed BNC. An intermittent that "fixed itself" didn't.

> [!question]- A 425 MHz signal arrives 10 dB weaker than budgeted after 20 m of RG-58. Bad cable?
> No — that's spec: RG-58 loses ~0.4–0.5 dB/m there, so 20 m ≈ 9–10 dB. Long UHF runs need low-loss cable (LMR-400 class, ~0.1 dB/m) or gain at the source end.

# Connections

- [[Transmission Lines]] — why cable geometry sets impedance and loss
- [[Characteristic Impedance and Reflection]] — what a mismatched or damaged connector does to the line
- [[Grounding and Shielding Practice]] — braid quality and pigtails, the shielding half of cabling
- [[Skin Depth]] — why cable loss climbs as √f

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Appendix H
