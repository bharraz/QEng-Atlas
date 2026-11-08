#circuits #electronics

**A capacitor is two conductors separated by an insulator, and the insulator — a ceramic, a plastic film, or a thin oxide grown on etched aluminium or tantalum — decides almost everything except the value printed on it: how the capacitance changes with voltage and temperature, how much current leaks through, how much series resistance and inductance come with it, and how it fails.** Choosing a capacitor means choosing a dielectric.

# Reference

**A real capacitor** is the capacitance in series with a resistance and an inductance:

$$
Z(f) = \mathrm{ESR} + j\left(2\pi f\,\mathrm{ESL} - \frac{1}{2\pi f C}\right)
$$

- $C$ — capacitance (F)
- $\mathrm{ESR}$ — equivalent series resistance (Ω): dielectric and electrode loss; heats under ripple current
- $\mathrm{ESL}$ — equivalent series inductance (H): package and leads, ~0.5–2 nH surface-mount, more if leaded
- $f$ — frequency (Hz)

Below the self-resonant frequency $1/2\pi\sqrt{\mathrm{ESL}\cdot C}$ it behaves as a capacitor; at resonance its impedance bottoms out at the ESR; above it, it is an inductor ([[Decoupling and Bypassing]]). A leakage resistance in parallel lets a small DC current through.

**Picture:** an ideal capacitor wrapped in its parasitics, with series resistance and inductance from the leads and plates and a leakage resistor across it, all set by the dielectric between the plates.

**Dielectrics:**

| Type | Values | Strengths | Drawbacks | Use for |
|---|---|---|---|---|
| C0G / NP0 ceramic (class 1) | pF to ~100 nF | capacitance nearly independent of voltage and temperature (±30 ppm/°C), low loss, not piezoelectric | small values only | filters and timing that must stay put, resonators, RF |
| X7R / X5R ceramic (class 2) | nF to ~100 µF | small, cheap, very low ESR and ESL | capacitance falls under DC bias — often to half or less of the rated value at rated voltage, worse in small packages; ±15% over temperature; piezoelectric; cracks if the board flexes, often failing short | decoupling and bulk bypass, where the exact value does not matter |
| Y5V / Z5U ceramic | as X7R | high capacitance per volume | loses most of its capacitance over the temperature range | avoid where the value matters |
| film (polypropylene, polyester) | nF to tens of µF | stable, low loss, little dielectric absorption (polypropylene), no bias derating, survives small breakdowns by clearing the spot | large | precision filters, integrators, sample-and-hold, high voltage |
| aluminium electrolytic | µF to F | very large capacitance per volume, cheap | polarized (reverse voltage destroys it); high ESR; µA leakage; dries out with heat and age (lifetime roughly halves per 10 °C); useless above ~100 kHz | bulk storage on supply lines |
| tantalum (MnO₂) | µF to hundreds of µF | small, stable | fails short — sometimes burning — under surges or reverse voltage; run at about half its rated voltage | compact bulk capacitance; polymer types have lower ESR and milder failures |
| mica | pF to nF | very stable, high Q | large, expensive | RF and reference circuits |

**Other non-idealities:**

- **Dielectric absorption.** After a capacitor is discharged, part of the charge was held in slow polarization of the dielectric and returns, so the voltage creeps back. This corrupts integrators and sample-and-hold circuits, and a high-voltage capacitor stored open can recharge itself to a dangerous voltage, which is why it is stored shorted.
- **Leakage.** In a filter with a large series resistor, leakage current × resistance appears as a DC offset ([[Filtering Power and Signal Lines]]).
- **Microphonics.** Class-2 ceramics are piezoelectric: vibration generates voltage on sensitive nodes, and ripple current can make them audibly sing.
- **Ratings.** Voltage, ripple current, temperature, and, for electrolytics, polarity are limits, not suggestions.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| LCR meter at the operating frequency and DC bias | the actual capacitance and ESR in the circuit; the printed value is measured at 1 kHz and zero bias |
| impedance against frequency (impedance analyzer or VNA) | self-resonance, ESL, and the ESR floor |
| tapping the board while watching a sensitive node | microphonic ceramics |
| leakage current at rated voltage, or ESR rising over the years | an electrolytic drying out |

> [!question]- A 10 µF, 6.3 V X5R capacitor in a small package filters a 5 V bias line, and the measured corner frequency is several times higher than designed. Why?
> DC-bias derating: at 5 V a small-package class-2 ceramic may keep only a fraction of its rated capacitance, so the RC corner $1/2\pi RC$ moves up by the same factor. Use a larger package or a higher voltage rating, or a film capacitor, whose value does not depend on bias.

# Connections

- [[Decoupling and Bypassing]] — capacitors at supply pins, self-resonance, and anti-resonance
- [[Filtering Power and Signal Lines]] — choosing filters for noisy lines
- [[RC and RL Filters]] — the corner frequency the capacitance sets
- [[LC Resonators]] — where capacitor loss sets the $Q$
- [[Complex Impedance]] — the $1/j\omega C$ behind every row above
- [[Time Constants and Reactance Rules of Thumb]] — reactance numbers to carry
- [[Handling Lab Hardware]] — stored charge in high-voltage supplies

---
Source: P. Horowitz & W. Hill, *The Art of Electronics*, 3rd ed. (Cambridge, 2015), Ch. 1; H. W. Ott, *Electromagnetic Compatibility Engineering* (Wiley, 2009), Ch. 5
