#circuits #electronics

**Drive a resistor, a capacitor, or an inductor with a sinusoidal voltage and wait for the switch-on transient to decay: the current is a sinusoid at the same frequency, with an amplitude and a phase shift set by the element and the frequency.** Impedance packs that ratio and phase shift into one complex number. Its real part, resistance, comes from energy dissipated; its imaginary part, reactance, comes from energy stored in an electric or magnetic field and handed back every cycle. With both in one number, the DC rules — series, parallel, voltage dividers — work unchanged for AC.

# Reference

**The element laws are the physics.** They hold for any waveform:

$$
v = iR, \qquad i = C\frac{dv}{dt}, \qquad v = L\frac{di}{dt}
$$

For a sinusoid written as $\mathrm{Re}[V e^{j\omega t}]$, every $d/dt$ becomes multiplication by $j\omega$ ([[Complex Numbers and Phasors]]), and each law turns into $V = ZI$:

$$
Z_R = R, \qquad Z_C = \frac{1}{j\omega C}, \qquad Z_L = j\omega L
$$

- $V, I$ — complex amplitudes (V, A): peak size and phase of the sinusoid
- $\omega$ — angular frequency (rad/s): $2\pi f$
- $j$ — the imaginary unit, $\sqrt{-1}$, written $j$ in engineering

$\lvert Z\rvert$ sets the current amplitude and $\arg Z$ the voltage–current phase: in a capacitor the current leads by 90°, in an inductor it lags by 90°. Series impedances add; parallel ones combine as $Z_1Z_2/(Z_1+Z_2)$.

**Resistance and reactance.** Any impedance, of one element or a whole network, splits into a real and an imaginary part:

$$
Z = R + jX, \qquad X_C = -\frac{1}{\omega C}, \qquad X_L = \omega L
$$

- $R$ — resistance (Ω): the part of $V$ in phase with $I$
- $X$ — reactance (Ω): the part of $V$ 90° out of phase with $I$
- $X_C$ — capacitor reactance (Ω): negative, shrinking with frequency
- $X_L$ — inductor reactance (Ω): positive, growing with frequency

The inverse, admittance $Y = 1/Z = G + jB$ (conductance $G$, susceptance $B$, in siemens), is the natural form for elements in parallel, where admittances add.

**Picture:** resistance is friction; reactance is a spring (capacitor) or a flywheel (inductor) — it pushes back on the current but returns each cycle the energy it took.

**What reactance means physically.** The power delivered to an impedance splits the same way:

$$
\tfrac12 V I^* = \tfrac12\lvert I\rvert^2 R + j\,\tfrac12\lvert I\rvert^2 X, \qquad X = \frac{4\omega\left(\langle W_m\rangle - \langle W_e\rangle\right)}{\lvert I\rvert^2}
$$

- $\tfrac12\lvert I\rvert^2 R$ — average power turned into heat (W)
- $\tfrac12\lvert I\rvert^2 X$ — reactive power (W, quoted as var): energy flowing in and back out each cycle
- $\langle W_m\rangle, \langle W_e\rangle$ — time-averaged magnetic and electric stored energy (J)
- $\lvert I\rvert$ — peak current amplitude (A)

So the sign of $X$ says which field, electric or magnetic, stores more energy: positive means magnetic (inductive), negative means electric (capacitive). Zero reactance — resonance — means the two store equal energy and trade it back and forth between themselves, and the source supplies only the losses. A reactance drops voltage without producing heat.

**What is physics and what is bookkeeping:**

| Item | Status | What it means |
|---|---|---|
| element laws and Kirchhoff's laws | physics | hold for any waveform, transients included |
| amplitude ratio and phase shift between $V$ and $I$ at one frequency | physics | measurable on a scope; the content $Z$ encodes |
| dissipated against stored energy | physics | heat against energy exchanged each cycle; carried by $R$ and $X$ |
| $j$ and $e^{j\omega t}$ | bookkeeping | the real signal is the real part; turns calculus into algebra |
| a single $Z(\omega)$ for an element | bookkeeping, valid in sinusoidal steady state of linear, time-invariant circuits | fails during transients, for diodes and saturating cores, and in switched circuits ([[RC and RL Time Response]]) |
| series $R + jX$ against a parallel equivalent | a modelling choice | a series pair $R_s, X_s$ equals a parallel pair $R_p = R_s(1+Q^2)$, $X_p = X_s(1+1/Q^2)$ at one frequency, with $Q = \lvert X_s\rvert/R_s$ |
| the sign of the imaginary unit | convention | physics texts using $e^{-i\omega t}$ write $Z_L = -i\omega L$ and $Z_C = i/\omega C$ |

For transients, replace $j\omega$ with the Laplace variable $s$: $Z_C = 1/sC$ and $Z_L = sL$ then describe switch-on as well as steady state ([[Transfer Functions and Bode Plots]]).

**Why reactance has its own name:**
- **Resonance** is where the total reactance is zero: in a series LC, $X_L + X_C = 0$ at $\omega_0 = 1/\sqrt{LC}$ ([[LC Resonators]]).
- **Matching** cancels a load's reactance with an opposite one, leaving only a resistance to transform ([[Impedance Matching]]).
- **Quality factor** $Q = \lvert X\rvert/R$ of a component is energy stored over energy lost per radian of oscillation.
- **Instruments report it:** LCR meters, impedance analyzers, and network analyzers give $R$ and $X$ (or $C$ and ESR) at a stated frequency ([[Smith Chart]]).

**Generalized voltage divider:**
$$
\frac{V_\text{out}}{V_\text{in}} = \frac{Z_2}{Z_1+Z_2}
$$

- $Z_1$ — impedance between input and output (Ω)
- $Z_2$ — impedance from output to ground (Ω)

Every passive filter is this equation with different impedances ([[RC and RL Filters]]).

**Scale:** $\lvert Z_C\rvert = 1/\omega C$ — 100 nF is 16 Ω at 100 kHz and 1.6 Ω at 1 MHz. $\lvert Z_L\rvert = \omega L$ — 1 µH is 6.3 Ω at 1 MHz. Crossovers like these decide which parasitic dominates a node ([[Time Constants and Reactance Rules of Thumb]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| phase of the current (across a small sense resistor) against the voltage on a scope | sign of $X$: current leading means capacitive, lagging means inductive |
| $\lvert Z\rvert$ against frequency on log–log axes | slope −1 is capacitive, +1 inductive, flat resistive; a dip marks a self-resonance |
| LCR-meter reading of $C$ and ESR at a stated frequency | the series model at that frequency only; the values change with frequency |
| reflection measured on a network analyzer, plotted on a Smith chart | upper half inductive, lower half capacitive |

> [!question]- A 1 kΩ resistor in series with 100 nF, driven at 10 kHz — roughly what is the current's phase, and where does the power go?
> $\lvert X_C\rvert = 1/(2\pi\cdot10^4\cdot10^{-7}) \approx 160\ \Omega \ll 1\ \text{k}\Omega$: the branch is mostly resistive, and the current is nearly in phase, leading by $\arctan(160/1000)\approx 9°$. All of the average power is dissipated in the resistor; the capacitor charges and discharges every cycle and dissipates none.

# Connections

- [[Complex Numbers and Phasors]] — why $e^{j\omega t}$ turns differential equations into this algebra
- [[RC and RL Time Response]] — the same circuits solved in time, before steady state
- [[RC and RL Filters]] — the divider above, evaluated against frequency
- [[Transfer Functions and Bode Plots]] — impedance dividers plotted and read
- [[LC Resonators]] — two reactances cancelling
- [[Impedance Matching]] — cancelling reactance, then transforming resistance
- [[Smith Chart]] — resistance and reactance read off one plot
- [[Time Constants and Reactance Rules of Thumb]] — reactance magnitudes to carry
- [[Capacitance and Inductance]] — where element values (and the pF/cm, nH/mm parasitics) come from

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §1.7; D. M. Pozar, *Microwave Engineering* 4th ed., §4.1 (impedance of a one-port from power and stored energy)
