#labwork #reference

**Atoms, ions, spins, and defects in a lab sit in the Earth's field, the 50 or 60 Hz fields of nearby wiring, and the stray fields of pumps and steel, while the experiment needs a magnetic field of known direction, size, and stability at the sample.** Coils create the field you want — a bias that defines the quantization axis, a gradient for a trap — and shielding and active compensation remove the field you do not want. Because a free electron spin shifts by about 2.8 MHz per gauss, field noise at the milligauss level is already kilohertz of qubit frequency noise.

# Reference

**Scale:**

| Source | Typical size |
|---|---|
| Earth's field | 25–65 µT (0.25–0.65 G), direction set by location |
| mains-frequency fields near wiring and equipment | 0.01–1 µT at 50 or 60 Hz and harmonics |
| ion pump magnets, magnetic optical mounts, steel tables | µT to mT nearby, with strong gradients |
| bias fields for atomic and ion qubits | 0.1–1 mT (1–10 G) typical |
| MOT gradients | 0.1–0.5 T/m (10–50 G/cm) |

Zeeman sensitivity sets how much of this matters: about 1.4 MHz/G per unit of $g_F m_F$ for atomic states, 2.8 MHz/G for a free electron spin, and only a quadratic shift for clock-type $m = 0 \to m = 0$ transitions ([[Zeeman Effect (Atlas)]], [[Hyperfine Structure]]).

**Coil geometries.** On the axis of a single circular loop of radius $R$ carrying current $I$, the field at the centre is $\mu_0 I/2R$. Pairs of loops do better ([[Magnetostatics]]):

$$
B_\text{H} = \left(\frac45\right)^{3/2}\frac{\mu_0 N I}{R} \approx 0.716\,\frac{\mu_0 N I}{R}, \qquad \frac{dB_z}{dz}\bigg|_\text{aH} = \frac{3\mu_0 N I R^2 a}{(R^2 + a^2)^{5/2}}
$$

- $B_\text{H}$ — central field of a Helmholtz pair (T): coils spaced by $R$, currents parallel
- $dB_z/dz$ — central gradient of an anti-Helmholtz pair (T/m): currents opposed
- $N$ — turns per coil
- $I$ — current (A)
- $R$ — coil radius (m)
- $a$ — half the spacing between the coils (m)

The Helmholtz spacing cancels the second derivative of the field at the centre, so the field departs from uniformity only at fourth order in the distance from it. For the gradient pair, a spacing of $\sqrt3 R$ gives the most uniform gradient. Because $\nabla\cdot\vec B = 0$, the radial gradient of an anti-Helmholtz pair is half the axial one, with opposite sign. Scale: $R = 10$ cm, $N = 50$, $I = 1$ A gives 4.5 G at the centre of a Helmholtz pair.

**Picture:** coils are the faucets that put field where you want it; shields and compensation are the drains that carry away the field you did not ask for.

| Geometry | Field it makes | Typical use |
|---|---|---|
| Helmholtz pair | uniform field | bias field, quantization axis |
| three orthogonal Helmholtz pairs | uniform field in any direction | cancelling Earth's field, setting the bias direction |
| anti-Helmholtz pair | quadrupole: zero at the centre, linear gradient | MOTs, magnetic traps ([[Magneto-Optical Traps]]) |
| long solenoid | uniform field $\mu_0 n I$ inside | Zeeman slowers (tapered), magnetometer calibration |
| permanent magnets | static field with no current noise | quiet bias fields for ion and defect experiments |

**Driving coils.**
- **Use a current source, not a voltage source.** Coil resistance rises as the coil heats, so a fixed voltage gives a drifting field. Current noise maps directly to field noise, so the sense resistor's temperature coefficient sets the long-term stability.
- **Inductance sets the switching speed.** A coil of inductance $L$ driven through resistance $R$ responds with time constant $L/R$. Interrupting its current produces a voltage spike $L\,dI/dt$, so a switched coil needs a diode, resistor, or snubber to give the current a path ([[RC and RL Time Response]]).
- **Eddy currents outlast the coil.** After switch-off, currents induced in the vacuum chamber, mounts, and table hold the field for milliseconds; slotted metal and non-conductive mounts shorten this ([[Faraday Induction]]).
- **Heat.** Dissipation $I^2R$ warms the coil and its surroundings; large coils need water cooling, and thermal expansion moves the field centre.
- **Permanent magnets** remove current noise but drift with temperature: about $-0.1\%$/K of field for NdFeB and $-0.03\%$/K for SmCo.

**Shielding.**
- **High-permeability shields** (mu-metal and similar alloys) divert static and low-frequency flux around the enclosed volume. For a long cylinder in a transverse field, the shielding factor is roughly $S \approx \mu_r t/D$ (relative permeability × wall thickness / diameter). Nested layers with gaps between them multiply their factors.
- **Their weaknesses.** High-permeability alloys saturate in fields of order 0.5–0.8 T, and lose permeability when bent, machined, or knocked, which then requires re-annealing. After assembly, or after being exposed to a strong field, they are degaussed with a slowly decaying AC current.
- **Openings.** Field leaks through holes, but decays exponentially along a tube-shaped opening over a length of order its radius, so access ports are made as short tubes rather than bare holes.
- **AC fields** above roughly 100 Hz are also screened by eddy currents in thick copper or aluminium ([[Electromagnetic Shielding]], [[Skin Depth]]).
- **Superconducting shields** expel field once cold, but any field present while they cool through $T_c$ is trapped as flux ([[Superconductivity]]).

**Active compensation.** A fluxgate or atomic magnetometer near the sample drives the three-axis coils in feedback, cancelling slow drifts and mains-frequency fields. The sensor measures the field at the sensor, not at the atoms, so gradients set the limit. Two simpler alternatives:
- **Line triggering.** Start each experimental shot at a fixed phase of the mains cycle, which makes the 50/60 Hz field the same in every shot.
- **Feedforward.** Drive the coils with a measured mains-synchronous waveform to cancel the AC field.

**Nulling the field, in order:**
1. **Measure a field-sensitive splitting** — a Zeeman-split microwave or Raman line, or a Ramsey frequency — while scanning the current in one compensation axis.
2. **Find the minimum of the splitting along that axis.** The minimum is where that axis's component cancels.
3. **Repeat for the other two axes, then iterate,** because the axes are never exactly orthogonal and the minimum of $\lvert B\rvert$ along one axis depends on the others.
4. **Apply the bias along the intended axis,** large enough that residual transverse fields only tilt it slightly.

**Failure modes:**

| Failure | Mechanism | Symptom |
|---|---|---|
| drifting bias | coil heating, sense-resistor temperature coefficient, building temperature | slow drift of qubit frequency, correlated with lab temperature |
| mains-frequency field | wiring, transformers, ground-loop currents in the coil driver | Ramsey phase that depends on when in the mains cycle the shot starts |
| magnetized hardware | steel screws, cold-worked 304 stainless, ion pump magnets | gradients; field that changes when parts are moved |
| eddy-current tails | conductive chamber and mounts | field still changing milliseconds after a switch |
| vibrating coils | coil or mount mechanical resonances | field noise at acoustic frequencies |
| magnetized or damaged shield | knocks, saturation, no degaussing after assembly | residual field inside higher than expected; offsets that change after handling |
| nearby equipment | elevators, compressors, other labs' magnets | slow or irregular field steps |

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Zeeman splitting against coil current, for each axis | field per ampere and the residual field to cancel |
| Ramsey phase against mains-cycle start phase | amplitude and phase of the 50/60 Hz field at the sample |
| Ramsey decay compared with spin-echo decay | slow field drift (removed by echo) against fast noise (not removed) ([[Spin Echo and Dynamical Decoupling]]) |
| splitting measured at several delays after a coil is switched | the eddy-current decay time |
| splitting at different positions of the sample | the field gradient |

> [!question]- Your qubit's Ramsey fringe contrast depends on when in the 60 Hz mains cycle the experiment starts. What is happening, and what are the fixes?
> A 60 Hz magnetic field at the sample shifts the qubit frequency through the Zeeman effect. The phase accumulated during a Ramsey sequence then depends on the part of the mains cycle it spans, so shots started at random times average to reduced contrast. The fixes: trigger every shot at the same mains phase, which makes the shift repeatable; feed forward a cancelling mains-synchronous current; add magnetic shielding; use a field-insensitive clock transition; or use spin echo, which cancels the part of the shift that is nearly constant during the sequence.

# Connections

- [[Magnetostatics]] — fields of wires, loops, and solenoids
- [[Electromagnetic Shielding]] — reflection, absorption, and leakage for general EM shielding
- [[Zeeman Effect (Atlas)]] — how a field shifts the levels being protected
- [[Hyperfine Structure]] — the clock transitions that are first-order field-insensitive
- [[RC and RL Time Response]] — coil switching and inductive kickback
- [[Faraday Induction]] — eddy currents in nearby metal
- [[Spin Echo and Dynamical Decoupling]] — removing the slow part of field noise
- [[Ground Loops]] — mains-frequency currents injected into coil drivers
- [[Handling Lab Hardware]] — handling shields and other sensitive hardware

---
Source: T. J. Sumner, J. M. Pendlebury & K. F. Smith, "Conventional magnetic shielding," *J. Phys. D* 20, 1095 (1987); Ott, *Electromagnetic Compatibility Engineering*, Ch. 6; Foot, *Atomic Physics*, Ch. 9–10 (traps and coils)
