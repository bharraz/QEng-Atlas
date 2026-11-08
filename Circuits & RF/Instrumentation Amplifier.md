#circuits #electronics

**Many sensors produce a small voltage difference between two wires that both sit at a large shared voltage relative to the measuring circuit — a small [[Common-Mode and Differential-Mode Signals|differential-mode (DM)]] signal riding a large common mode (CM) — and an instrumentation amplifier (in-amp) amplifies only the difference while presenting near-infinite impedance to both wires, so it neither loads the sensor nor unbalances the two lines.** Inside, two buffer op-amps give both inputs that near-infinite impedance and amplify the difference; a third subtracts.

# Reference

**Why not one op-amp:** a single op-amp difference amplifier has input resistors that load the source, and its CM rejection depends on those resistors matching; any source resistance in series with them spoils the match. The in-amp puts a buffer in front of each input instead.

**Three-op-amp topology:** each input drives a non-inverting op-amp stage (whose input draws almost no current); the two stages share one gain resistor $R_g$ between them, and a third op-amp subtracts their outputs:

$$
G = 1 + \frac{2R}{R_g}
$$

- $G$ — differential gain (for a unity-gain subtractor)
- $R$ — the two equal input-stage feedback resistors (Ω): internal to integrated in-amps
- $R_g$ — the single gain resistor, usually the one you choose

Gain set by **one resistor**; the input stage amplifies DM but passes CM at unity, so the subtractor's resistor-matching burden is relieved by $G$ — the common-mode rejection ratio (CMRR) improves with gain.

**Picture:** two buffers that listen to each wire without drawing current, then a subtractor: the common voltage passes the buffers at unity, while the difference is amplified before subtraction.

**Specs that matter:** CMRR 100–120 dB at DC, **falling ~20 dB/dec above ~1–10 kHz** (fine for mains harmonics, useless against RF common-mode); input impedance ~GΩ on both pins; AD620/INA128-class parts (common integrated in-amps) are the default.

**Where it's the right tool:** thermocouples, strain bridges, current-shunt readout — any **small differential signal riding a large common-mode** (ground offsets between racks, motor drives, biopotentials).

**Pitfalls:**
- **Bias-current return path:** the inputs draw small DC input bias currents that must flow somewhere. A floating source (thermocouple, transformer) leaves the input bias currents nowhere to go, so the inputs drift to the supply rails. ~1 MΩ from an input to reference ground gives them a path.
- **Input CM range:** how large a common mode the inputs tolerate depends on gain and on $V_\text{ref}$, the voltage on the reference pin that the output is measured from. Datasheets draw the allowed region of CM input versus output voltage, and its shape gives it the name "diamond plot" — check it when the common-mode is large.
- **RF rectification:** out-of-band RF common mode is rectified by the nonlinear input stage and demodulates to a DC offset. The remedy is an RC or CM-choke filter at the inputs, built with *matched* resistors on the two lines, because any imbalance converts CM to DM.

> [!question]- A thermocouple reads fine on a bench meter but slams to the rail through an in-amp. Both are "high impedance." What's missing?
> A DC return path for the in-amp's input bias currents — the floating couple provides none, so the inputs charge to the rails. ~1 MΩ to reference ground fixes it.

# Connections

- [[Common-Mode and Differential-Mode Signals]] — the rejection arithmetic this amplifier exploits
- [[Op-Amp Golden Rules and Real Limits]] — the bias-current and CM-range specs behind these pitfalls
- [[Differential Signaling]] — the transmission-side discipline that pairs with it
- [[Ground Loops]] — differential input = the #1 loop-breaking fix

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §5.15
