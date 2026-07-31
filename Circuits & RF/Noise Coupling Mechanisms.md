#circuits #electronics

**Noise gets into a circuit exactly four ways — stray capacitance, mutual inductance, a shared return impedance, or radiation — and each has a distinct fingerprint, so you can identify the route before touching anything.** Fixing the wrong mechanism (shielding an inductive problem, twisting a capacitive one) does nothing; this card is the diagnosis table.

# Reference

| Mechanism | Drive | Couples worst into | Telltale signature | Fix |
|---|---|---|---|---|
| **Capacitive** (stray C, E-field) | $dV/dt$ | **high-impedance** nodes | grows with victim impedance (probe with 10× lower R → drops); responds to a grounded shield, or even your hand | grounded electrostatic shield around victim; lower the node impedance; distance |
| **Inductive** (mutual M, B-field) | $dI/dt$ | **low-impedance loops** | scales with **loop area & orientation**, indifferent to victim Z; foil shield does nothing | shrink the loop, twist the pair, move/rotate away from the $dI/dt$ source |
| **Common impedance** | shared return path | anything sharing the wire | victim signal is a copy of **another circuit's current draw** (steps when a load switches) | separate return paths; star point; ground plane |
| **Radiated** (far-field) | cables ≈ antennas at $\ell \sim \lambda/4$ | the whole system via its cables | narrowband at broadcast/ISM bands; changes with **cable length and position**; ≳ tens of MHz | filter/ferrite at the enclosure entry; 360° shield termination |

**Diagnostic knobs — change one thing and watch:**
- Victim impedance ↓ and noise ↓ → capacitive.
- Move/reorient cables and it changes → inductive (or radiated, if RF).
- Correlates with another box's activity → common impedance.
- Tune across it on a spectrum analyzer and find a radio station → radiated.

Near-field coupling (capacitive/inductive) falls off fast with distance — physical separation is cheap and underrated.

> [!question]- Hum on a high-Z piezo line disappears when you grip the cable but not when you twist it with its return. Which mechanism, which fix?
> Grip helps (your body acts as a shield) while twisting doesn't → capacitive, not inductive. Fix: grounded shield around the line and/or lower the node impedance — loop-area tricks were never going to work.

# Connections

- [[Ground Loops]] — the lab's flagship combination of inductive + common-impedance coupling
- [[Near and Far Field]] — why capacitive/inductive pickup (near field) and radiated pickup (far field) are different physics with different fixes
- [[Grounding and Shielding Practice]] — the prevention playbook once you know the mechanism
- [[Faraday Induction]] — the physics under the inductive row
- [[Antennas]] — why every cable is an accidental λ/4 receiver
- [[Noise Spectra and Coupling to Systems]] — what the noise does after it enters: spectra and system response

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Chs. 2–3
