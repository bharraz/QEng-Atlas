#solid-state #quantum
**A nitrogen-vacancy center is an atom-like defect in diamond whose electronic spin can be initialized and read out optically and manipulated with microwaves — at room temperature.** It is a solid-state spin qubit and a nanoscale magnetometer, and it applies the AMO toolkit (optical pumping, Zeeman, Ramsey, echo) to a point defect in a crystal.

# Reference

The NV center is a substitutional nitrogen next to a missing carbon, with $C_{3v}$ symmetry along one of the four $\langle 111 \rangle$ diamond axes (see [[Point Groups and Character Tables]]). The negatively charged NV$^-$ has a **spin-triplet ($S=1$) ground state** ($^3A_2$ in the point-group labels).

**Ground-state spin Hamiltonian** (the working equation of everything NV):

$$H/h = D S_z^2 + E\,(S_x^2 - S_y^2) + \frac{\gamma_e}{2\pi}\, \mathbf{B}\cdot\mathbf{S} + A_\parallel S_z I_z + A_\perp (S_x I_x + S_y I_y)$$

Dividing by $h$ puts every term in Hz, the units all NV work is quoted in. $\mathbf{S}$ = electron spin-1 operator and $\mathbf{I}$ = host-nuclear spin operator (both dimensionless, in units of $\hbar$); $z$ = the NV symmetry axis. Term by term: $D S_z^2$ splits $m_s = \pm1$ from $m_s = 0$ *without* any field (it is the spin's own dipolar field, hence $S_z^2$ — even in $m_s$, so it cannot distinguish $+1$ from $-1$); $E(S_x^2 - S_y^2)$ is the only transverse term, and being a difference of $x$ and $y$ it vanishes under threefold symmetry; the Zeeman term is linear in $m_s$ and so *does* split $\pm1$; the hyperfine terms couple electron to nucleus. Parameters:

- $D \approx 2.870$ GHz — zero-field splitting between $m_s = 0$ and $m_s = \pm1$; temperature-dependent, $dD/dT \approx -74$ kHz/K (the thermometry channel), and shifted by axial strain/electric field.
- $E$ — transverse strain/electric-field parameter; splits $m_s = \pm 1$ at zero field (kHz–MHz depending on sample). Zero in ideal $C_{3v}$; any $E \neq 0$ *is* broken symmetry.
- $\gamma_e/2\pi = 28.0$ GHz/T $= 2.80$ MHz/G — electron gyromagnetic ratio; small axial fields shift $m_s = \pm1$ by $\mp\gamma_e B_z$, so the ODMR dip splitting is $2\gamma_e B_z / 2\pi$.
- Hyperfine to the host $^{14}$N ($I=1$): $A_\parallel \approx -2.16$ MHz — the visible triplet substructure on each ODMR line; nearby $^{13}$C ($I = \tfrac12$, 1.1% abundance) add couplings from ~kHz to 130 MHz (first shell).

Level ordering to keep straight: $m_s = 0$ is the *ground* sublevel; magnetometry works between $0 \leftrightarrow \pm 1$ at $D \pm \gamma_e B_z/2\pi$.

**Optical spin readout and initialization:** green (532 nm) excitation drives a spin-conserving optical transition, but the excited $m_s=\pm1$ states preferentially decay through a dark metastable singlet back to $m_s=0$. Two things follow: $m_s=0$ fluoresces brighter than $m_s=\pm1$ (**optical readout**), and repeated cycling pumps population into $m_s=0$ (**optical initialization**).

**ODMR (optically detected magnetic resonance):** sweep a microwave tone while watching the fluorescence; a dip appears at the spin resonance ($\sim$20–30% contrast for a single NV). An external field Zeeman-shifts $m_s=\pm1$ (see [[Zeeman Effect (Atlas)]]), so the dip positions read out the local magnetic field — the basis of NV **magnetometry**.

**Sensitivity — the estimate to remember.** A Ramsey (DC) or echo (AC) measurement converts field to phase, $\phi = \gamma_e B \tau$; shot-noise-limited sensitivity is

$$\eta \approx \frac{1}{\gamma_e\, C \sqrt{N\, \tau}} \quad (\text{units } \mathrm{T}/\sqrt{\mathrm{Hz}}),$$

$\eta$ = sensitivity, the field resolvable in one second of averaging (smaller is better; a $\sqrt{\text{Hz}}$ quantity because errors average down as $1/\sqrt{t}$); $\gamma_e$ = gyromagnetic ratio (rad s⁻¹T⁻¹) converting field into precession rate; $\tau$ = interrogation time per shot (s), capped by coherence ($T_2^*$ for DC, $T_2$ for AC); $N$ = number of NVs contributing; $C$ = readout contrast/collection factor (dimensionless, 0.01–0.3). The $\sqrt{\tau}$ rather than $\tau$ is the trade: phase accumulates linearly in $\tau$ but fewer shots fit in a fixed averaging window, so sensitivity improves only as the square root — and $C$ enters linearly, which is why readout fidelity is worth as much as coherence. Orders of magnitude: single NV, $T_2 \sim 100\,\mu$s, ideal readout → nT/√Hz; ensembles reach pT/√Hz. The same logic with $dD/dT$ gives thermometry (~mK/√Hz) and with the $E$-term, electrometry.

**Coherence budget:** $T_1 \sim$ ms (room temp, phonon-limited, $\propto T^{-5}$ at low temp); $T_2^* \sim \mu$s (quasi-static $^{13}$C bath and strain); $T_2 \sim 0.1\text{–}1$ ms with echo/DD, up to ~s at low temperature in isotopically purified $^{12}$C diamond. The gap between $T_2^*$ and $T_2$ is why NV sensing is largely pulse-sequence engineering (see [[Spin Echo and Dynamical Decoupling]] and [[Reference Atlas/Math/Magnus Expansion]]); DD filter frequencies double as AC-field lock-in detection. Nearby $^{13}$C and the $^{14}$N nuclear spins act as a small quantum register with second-scale coherence.

> [!question]- How do you read a single electron spin optically when a microwave-energy spin flip is far too weak to detect directly?
> You never detect the spin flip itself. You exploit spin-dependent fluorescence: $m_s=0$ cycles brightly on the optical transition while $m_s=\pm1$ shelves into a dark singlet, so counting visible photons over many optical cycles reports the spin state. The optical transition amplifies a GHz-scale spin difference into a stream of eV-scale photons you can actually count.

# Connections

- [[Optical Pumping]] — the cycling that initializes the spin into $m_s=0$
- [[Zeeman Effect (Atlas)]] — field-dependent splitting of $m_s=\pm1$, the magnetometry signal
- [[Spin Echo and Dynamical Decoupling]] — how NV coherence is extended for sensing
- [[Ramsey Interferometry]] — the phase-accumulation sequence used for DC field sensing
- [[Hyperfine Structure]] — coupling to $^{14}$N and $^{13}$C nuclear spins as a register
- [[Magnetism in Solids]] — an isolated spin embedded in a solid host
- [[Point Groups and Character Tables]] — $C_{3v}$: the level labels ($^3A_2$, $^3E$), what protects $m_s = \pm1$ at zero field, and the optical polarization selection rule

---
Source: Doherty et al., "The nitrogen-vacancy colour centre in diamond," *Phys. Rep.* 528, 1 (2013)
