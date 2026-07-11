#solid-state #quantum-info

**A superconducting qubit is an LC circuit made nonlinear by a Josephson junction, so its energy levels become unequally spaced and the lowest two form an addressable qubit driven with microwaves.** It is an "artificial atom" on a chip, and the entire AMO toolkit — Rabi, Bloch sphere, Jaynes–Cummings, $T_1/T_2$ — maps directly onto circuit elements.

# Reference

A plain **LC oscillator** has evenly spaced levels (it is a harmonic oscillator), which is useless as a qubit: a drive resonant with $0\to1$ is equally resonant with $1\to2$, so you cannot isolate two levels. The **Josephson junction** (from [[Superconductivity]]) is a nonlinear, lossless inductor; replacing $L$ with it makes the spectrum **anharmonic**, separating the $0\to1$ transition (typically 4–8 GHz) from the rest.

**The circuit Hamiltonian.** With $\hat{n}$ the Cooper-pair number on the island and $\hat\varphi$ the junction phase ($[\hat\varphi, \hat n] = i$ — a conjugate pair, exactly like $\hat x, \hat p$):

$$H = 4E_C\,(\hat{n} - n_g)^2 - E_J\cos\hat\varphi, \qquad E_C = \frac{e^2}{2C_\Sigma},$$

with $n_g$ the offset charge (environment-controlled, noisy). Expanding $\cos\hat\varphi$: the quadratic term is the LC oscillator; the quartic term $-E_J\hat\varphi^4/24$ is the anharmonicity. It is a quantum pendulum: $E_C$ the kinetic (charging) energy, $E_J$ the gravitational (Josephson) term.

The dominant design is the **transmon**: a junction shunted by a large capacitor, run at $E_J/E_C \sim 50\text{–}100$. In this limit

$$\hbar\omega_{01} \approx \sqrt{8E_J E_C} - E_C, \qquad \alpha \equiv \omega_{12} - \omega_{01} \approx -E_C/\hbar,$$

and charge dispersion (the $n_g$ sensitivity) shrinks *exponentially* in $\sqrt{8E_J/E_C}$ while anharmonicity falls only *algebraically* — that asymmetry is the entire design insight. Typical numbers: $E_C/h \approx 200\text{–}300$ MHz, $E_J/h \approx 10\text{–}20$ GHz, $\omega_{01}/2\pi \approx 4\text{–}6$ GHz, $\alpha/2\pi \approx -200$ to $-300$ MHz. The weak anharmonicity caps gate speed: pulses much shorter than $\sim 1/|\alpha| \approx$ few ns leak into $|2\rangle$ (mitigated by pulse shaping, e.g. DRAG).

**Operation:**
- **Control** — resonant microwave drives produce [[Rabi Oscillations]]; flux through a SQUID loop tunes the frequency.
- **Readout and coupling** — circuit QED: the qubit couples to a microwave resonator (a [[Jaynes-Cummings Model|Jaynes–Cummings]] system on a chip, see [[Cavity QED]]) with strength $g/2\pi \sim 100$ MHz, detuned by $\Delta = \omega_q - \omega_r$. In the **dispersive regime** $|\Delta| \gg g$ the interaction becomes $H_{\text{disp}} = \hbar\chi\,\hat\sigma_z\, \hat a^\dagger\hat a$ with
$$\chi = \frac{g^2}{\Delta}\cdot\frac{\alpha}{\Delta + \alpha}$$
(the transmon's third level corrects the two-level $g^2/\Delta$). The resonator frequency shifts by $\pm\chi$ depending on qubit state — probe it with a weak tone, read the phase. Typical $\chi/2\pi \sim$ 1 MHz; readout in a few hundred ns with a quantum-limited (JPA/TWPA) amplifier chain.
- **Environment** — operated at millikelvin in a dilution fridge so that $k_B T \ll \hbar\omega$ and the superconducting gap holds; coherence $T_1, T_2$ reach tens to hundreds of microseconds.

> [!question]- Why can't a plain LC resonator be a qubit, and what exactly does the Josephson junction fix?
> A harmonic oscillator has equally spaced levels, so any drive that excites $0\to1$ also drives $1\to2$, $2\to3$, and population leaks out of the computational subspace. The junction's nonlinear inductance makes the level spacings unequal, so the $0\to1$ transition sits at a distinct frequency and can be driven in isolation. The junction manufactures a usable two-level system out of an oscillator.

# Connections

- [[Superconductivity]] — the Josephson junction and dissipationless circuits it provides
- [[LC Resonators]] — the linear circuit the junction makes anharmonic
- [[Jaynes-Cummings Model]] — qubit–resonator coupling, realized as circuit QED
- [[Cavity QED]] — dispersive readout and coupling on a chip
- [[Qubits]] — the abstract two-level system this physically implements
- [[T1 and T2]] — the coherence times that gate the technology

---
Source: Krantz et al., "A Quantum Engineer's Guide to Superconducting Qubits," *Appl. Phys. Rev.* 6, 021318 (2019); Koch et al., *Phys. Rev. A* 76, 042319 (2007)
