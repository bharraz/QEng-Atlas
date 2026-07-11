#circuits #electronics

**Two ground connections between chassis = a conducting loop: changing magnetic flux through it, or other equipment's current flowing along its shared segment, drives a current that your signal cable turns into voltage.** The signature: 50/60 Hz hum plus harmonics that appears the moment you plug in a second ground-referenced cable.

# Reference

**Two mechanisms, same loop:**
- **Induction:** $V = d\Phi/dt = \omega BA$. A 1 m² loop in the ~µT stray field of a transformer at 60 Hz picks up ~0.5 mV — enormous against a µV signal. Buzz (harmonic-rich) rather than pure hum means the source is rectifier/SMPS current spikes, not a sinusoidal field.
- **Shared return impedance:** the two "grounds" are joined through building wiring carrying everyone else's return current; the drop $I\,Z_\text{gnd}$ appears in series with your signal. This one tracks other equipment switching on and off.

**Symptom checklist:**
- Comb of 50/60 Hz + harmonics on the spectrum analyzer
- Appears/vanishes as specific cables connect — including the scope probe (its ground clip is mains earth!)
- Level changes when cables are re-routed (loop area) or when the HVAC/pump kicks in (shared current)

**Fixes, in order of preference:**
1. **Break the loop where the signal crosses:** differential/instrumentation input, isolation transformer, optocoupler/fiber — signal passes, ground current can't.
2. **Single-point ground:** one path to earth per signal cluster, no second path to close a loop.
3. **Shrink the loop:** signal and return in the same cable (coax/twisted pair), all cables routed along the same path.
4. Never defeat a safety earth to "fix" hum — lift the shield or signal ground instead.

> [!question]- Connecting a scope to a quiet photodiode signal adds 60 Hz hum. The scope is fine. What happened?
> The probe shield tied the circuit to earth at the scope while the supply earths it elsewhere — a loop through mains earth now encloses stray flux and carries shared return current. Break it (differential probe, single ground point); don't float the scope.

# Connections

- [[Faraday Induction]] — mechanism 1 is exactly $-d\Phi/dt$ with your cables as the winding
- [[Grounding and Shielding Practice]] — the systematic prevention doctrine
- [[Noise Coupling Mechanisms]] — ground loops mix the inductive and common-impedance rows
- [[Common-Mode and Differential-Mode Signals]] — loop voltage arrives common-mode; that's why differential inputs (fix #1) work
- [[Instrumentation Amplifier]] — the standard loop-breaking input stage

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 3
