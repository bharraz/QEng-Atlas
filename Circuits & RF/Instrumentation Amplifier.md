#circuits #electronics

**Two buffer op-amps give both inputs near-infinite impedance and amplify only the difference; a third subtracts — a differential amplifier you can connect to real sensors without loading or unbalancing them.**

# Reference

Three-op-amp topology, input pair sharing one gain resistor $R_g$:

$$
G = 1 + \frac{2R}{R_g}
$$

Gain set by **one resistor**; the input stage amplifies DM but passes CM at unity, so the subtractor's resistor-matching burden is relieved by $G$ — CMRR improves with gain.

**Specs that matter:** CMRR 100–120 dB at DC, **falling ~20 dB/dec above ~1–10 kHz** (fine for mains harmonics, useless against RF common-mode); input impedance ~GΩ on both pins; AD620/INA128-class parts are the default.

**Where it's the right tool:** thermocouples, strain bridges, current-shunt readout — any **small differential signal riding a large common-mode** (ground offsets between racks, motor drives, biopotentials).

**Gotchas:**
- **Bias-current return path:** a floating source (thermocouple, transformer) leaves the input bias currents nowhere to go — inputs drift to the rails. Add ~1 MΩ from an input to reference ground.
- Input CM range depends on gain and $V_\text{ref}$ (the "diamond plot") — check it when the common-mode is large.
- RF rectification: out-of-band CM demodulates to a DC offset — RC/CM-choke filter at the inputs, with *matched* resistors (imbalance = CM→DM conversion).

> [!question]- A thermocouple reads fine on a bench meter but slams to the rail through an in-amp. Both are "high impedance." What's missing?
> A DC return path for the in-amp's input bias currents — the floating couple provides none, so the inputs charge to the rails. ~1 MΩ to reference ground fixes it.

# Connections

- [[Common-Mode and Differential-Mode Signals]] — the rejection arithmetic this amplifier exploits
- [[Op-Amp Golden Rules and Real Limits]] — the bias-current and CM-range specs behind the gotchas
- [[Differential Signaling]] — the transmission-side discipline that pairs with it
- [[Ground Loops]] — differential input = the #1 loop-breaking fix

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §5.15
