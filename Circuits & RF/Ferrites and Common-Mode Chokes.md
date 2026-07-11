#circuits #electronics

**A ferrite around a cable is a lossy RF resistor that only the common-mode current sees: differential currents' flux cancels through the core, while CM current magnetizes it and gets dissipated.** That's why you can clamp one onto a finished cable without touching the signal.

# Reference

**Ferrite bead:** below ~1 MHz mostly inductive; through ~10–1000 MHz the core is **lossy**, so the impedance is resistive — it absorbs RF rather than reflecting or resonating. Datasheet spec is Z at 100 MHz, typically 50–600 Ω. One bead in a 50 Ω system: ~6–15 dB — helpful, not surgical. Multiple turns through the core: Z scales ~$n^2$ until parasitic capacitance spoils it.

**Common-mode choke:** both conductors wound together on one core.
- DM current (signal, power): equal and opposite → flux cancels → $Z_\text{dm}\approx 0$, and load current can't saturate the core
- CM current (noise): fluxes add → full inductance plus core loss → $Z_\text{cm}$ large

**What a clamp-on ferrite can fix:** RF common-mode on cables — cable-as-antenna pickup and emission, USB/SMPS hash riding into the experiment. Place it **at the cable's entry** to the shielded box; mid-cable just relocates the antenna.

**What it can't fix:** differential-mode noise (invisible to it), and 50/60 Hz hum — ferrite impedance at mains frequency is essentially zero. Hum is a grounding problem, not a ferrite problem.

> [!question]- A clamp-on ferrite killed the 100 MHz hash on a cable but didn't touch the 60 Hz hum. Why is that exactly as expected?
> Ferrite impedance is significant only at RF — milliohms at 60 Hz, hundreds of lossy ohms at 100 MHz — and it only acts on common-mode. Hum needs the ground loop broken, not choked.

# Connections

- [[Common-Mode and Differential-Mode Signals]] — the choke is a pure-CM impedance; the cleanest application of the decomposition
- [[Noise Coupling Mechanisms]] — the standard fix for the radiated/cable-antenna row
- [[Ground Loops]] — at RF a CM choke effectively opens the loop; at mains frequency it cannot
- [[Impedance Matching]] — why a series impedance helps: it spoils the accidental antenna's match

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 5
