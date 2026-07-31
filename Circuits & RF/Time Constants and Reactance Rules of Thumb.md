#circuits #electronics

**Every capacitor and inductor in a circuit — intended or parasitic — pairs with a resistance to make a time constant, and with the signal frequency to make a reactance. Knowing $\tau$ and $|X|$ by inspection tells you what a circuit will do before you simulate it, and tells you what went wrong when it misbehaves.**

# Reference

$$\tau_{RC} = RC, \qquad \tau_{RL} = L/R, \qquad f_{-3\mathrm{dB}} = \frac{1}{2\pi\tau}, \qquad t_{\text{rise}}\,(10\text{–}90\%) = 2.2\,\tau$$

$\tau$ = time constant (s), the $1/e$ settling time of the step response; $R$ = the resistance the reactive element actually sees looking outward — *not* a component value on the schematic, but source resistance plus load in parallel, which is why the same capacitor behaves differently in two places; $C$ (F), $L$ (H) = the total including parasitics.

Reactance magnitudes at frequency $f$:

$$|X_C| = \frac{1}{2\pi f C}, \qquad |X_L| = 2\pi f L$$

$X_C$ falls with frequency (a cap is an open at DC, a short at high $f$), $X_L$ rises (an inductor is a short at DC, an open at high $f$). A reactive element only matters where its reactance is *comparable to the surrounding resistance* — that crossing is the corner frequency, and it is the whole reason $f = 1/2\pi RC$ appears everywhere.

## Numbers worth memorizing

$$RC:\; 1\,\mathrm{k\Omega} \times 1\,\mathrm{nF} = 1\,\mu\mathrm{s} \;\Rightarrow\; 159\,\mathrm{kHz}, \qquad L/R:\; 1\,\mu\mathrm{H} / 50\,\Omega = 20\,\mathrm{ns}$$

Scale by inspection — both are products, so a decade in either factor is a decade in $\tau$.

| Element | Typical value | Reactance = 50 Ω at | Reactance = 1 MΩ at |
|---|---|---|---|
| Coax, 1 m | 100 pF | 32 MHz | 1.6 kHz |
| Scope probe (10×) | 10 pF | 320 MHz | 16 kHz |
| Bond wire / lead, 1 mm | 1 nH | 8 GHz | — |
| Ceramic bypass cap | 100 nF | 32 kHz | 1.6 Hz |
| Piezo / photodiode | 1 nF | 3.2 MHz | 160 Hz |

Also: $1/2\pi \approx 0.159$, so "$RC$ in µs" → "corner in kHz" is division by 6.28; a decade of frequency is a factor 10 in reactance; free space and PCB traces run ~1 nH/mm and ~1 pF/cm.

## Why it matters for design

- **Filter placement**: the corner must sit between the signal you keep and the noise you reject, and the resistance in $\tau$ must be the *actual* driven-plus-load impedance, or the filter lands at the wrong frequency.
- **Bypassing**: a bypass cap works where $|X_C| \ll$ supply impedance; its own series inductance (ESL, ~1 nH) makes it *self-resonant* at $f = 1/2\pi\sqrt{LC}$ and inductive above — a 100 nF 0805 resonates near 20 MHz, which is why parallel small caps exist ([[Decoupling and Bypassing]]).
- **Speed budget**: cascading $n$ single-pole stages gives $t_r \approx \sqrt{\sum t_{r,i}^2}$ — the slowest stage dominates in quadrature, so fixing anything but the worst pole buys little.
- **Loading**: a 10 pF probe on a 100 kΩ node makes a 1 µs pole — the instrument creates the corner it then measures.

## Why it matters for debugging

Read the symptom back to a $\tau$:

- **Exponential settling with visible tail** → an $RC$ somewhere; measure the tail's $\tau$, divide by the resistance you know, and the capacitance names the culprit (usually cable or input capacitance).
- **Overshoot/ringing at a definite frequency** → an $LC$: $f_0 = 1/2\pi\sqrt{LC}$ with $Q = \frac{1}{R}\sqrt{L/C}$ — lead inductance with bypass capacitance, or feedback capacitance with source capacitance ([[Transimpedance Amplifier]]).
- **Rolloff at the wrong frequency** → the resistance in $\tau$ isn't what you assumed (source impedance, or a load in parallel).
- **A "slow" signal that speeds up when you shorten a cable** → cable capacitance was in the $\tau$ all along.
- **Steps ringing with period fixed by cable length, not by any $RC$** → not a time constant at all but a transmission-line reflection ([[Characteristic Impedance and Reflection]]) — the tell is that the period tracks length, and the fix is termination, not a filter.

> [!question]- A photodiode signal looks clean on a 1 MΩ scope input but disappears when you switch to 50 Ω. What is the circuit telling you?
> The source is current-like with high output impedance, and the two inputs form different $\tau$'s with the cable capacitance ($\sim$100 pF/m). At 1 MΩ, $\tau = 100\ \mu$s — the node integrates the current into a large, slow voltage. At 50 Ω, $\tau = 5$ ns, so the same current produces $IR$ = a tiny fast voltage. Nothing broke; you traded amplitude for bandwidth by changing $R$ in both $V = IR$ and $\tau = RC$. If you want both, use a [[Transimpedance Amplifier|transimpedance amplifier]], which holds the node at virtual ground so $C$ never charges.

# Connections

- [[RC and RL Filters]] — the full transfer functions these rules approximate
- [[Complex Impedance]] — where $X_C$, $X_L$ come from; the phasor formalism
- [[LC Resonators]] — $f_0$ and $Q$ when both reactances are present
- [[Decoupling and Bypassing]] — self-resonance and why cap choice is a reactance argument
- [[Bandwidth]] — rise time × bandwidth ≈ 0.35, the same pole in time-domain clothing
- [[Characteristic Impedance and Reflection]] — the regime where lumped $\tau$ reasoning fails
- [[Transimpedance Amplifier]] — the standard escape from source-capacitance loading

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Ch. 1 & App. H; Ott, *Electromagnetic Compatibility Engineering*, Ch. 11
