#solid-state #quantum

**Two superconductors separated by a thin barrier form the only known circuit element that is both nonlinear and lossless — which is what makes an artificial atom possible.**

# Reference

Two relations define it. $\varphi$ is the gauge-invariant phase difference across the barrier:

$$I = I_c \sin\varphi \qquad\text{(DC)}, \qquad \frac{d\varphi}{dt} = \frac{2eV}{\hbar} = \frac{2\pi V}{\Phi_0} \qquad\text{(AC)}$$

with the **flux quantum** $\Phi_0 = h/2e = 2.068\times10^{-15}$ Wb. The $2e$ is the Cooper pair charge — every factor of two in superconducting circuits traces to it.

- **DC relation:** current flows with *zero voltage* for $|I| < I_c$, carried by pair tunneling. $I_c$ = critical current, set by the barrier.
- **AC relation:** any voltage makes the phase wind, at $2e/h = 483.6$ MHz/µV. This is exact and is the basis of the volt standard.

**Nonlinear inductance.** Differentiate the DC relation and substitute the AC one:
$$V = \frac{\Phi_0}{2\pi\cos\varphi}\frac{dI}{dt} \quad\Rightarrow\quad L_J(\varphi) = \frac{\Phi_0}{2\pi I_c\cos\varphi} = \frac{L_{J0}}{\cos\varphi}$$

- Behaves as an inductor $L_{J0} = \Phi_0/2\pi I_c$ for small $\varphi$, but the inductance **depends on the current through it** — the nonlinearity.
- $L_J \to \infty$ as $\varphi \to \pi/2$: the junction stiffens and cannot carry more than $I_c$.
- **Lossless** because pair tunneling is dissipationless: no resistor, no Johnson noise, no added decoherence. Every other nonlinear element (diode, transistor) dissipates. This is the whole reason superconducting qubits exist ([[Superconducting Qubits]]).

**Energy.** Integrating $IV\,dt$ gives the potential
$$U(\varphi) = -E_J\cos\varphi, \qquad E_J = \frac{\Phi_0 I_c}{2\pi} = \frac{\hbar I_c}{2e}$$
A cosine well, not a parabola — expanding, $-E_J(1 - \varphi^2/2 + \varphi^4/24 - \cdots)$: the quadratic term is an ordinary inductor and **the quartic term is the anharmonicity** that separates $0\!\to\!1$ from $1\!\to\!2$.

**Conjugate variables.** With $\hat n$ the number of Cooper pairs transferred, $[\hat\varphi, \hat n] = i$ — a position–momentum pair ([[Commutators and Anticommutators]]). The junction is a quantum pendulum: $E_J$ is gravity, the charging energy is inertia.

## Getting the parameters you want

**Ambegaokar–Baratoff** ties the critical current to the normal-state resistance and the superconducting gap:
$$I_c R_n = \frac{\pi\Delta}{2e}$$

This is the practical bridge: $R_n$ is measurable at **room temperature** with a probe station, so a two-terminal resistance check predicts $E_J$ before the chip ever goes in the fridge. For Al ($\Delta/e \approx 200$ µV), $I_cR_n \approx 300$ µV.

| Design goal | Knob | Mechanism |
|---|---|---|
| Set $E_J$ | junction area and barrier thickness | $I_c \propto$ area, and **exponentially** in barrier thickness — hence oxidation dose control, and why $E_J$ scatter is the yield problem |
| Set $E_C$ | shunt capacitor geometry | $E_C = e^2/2C_\Sigma$; large pad ⇒ small $E_C$ ⇒ transmon regime |
| Make $E_J$ tunable | two junctions in a loop (**DC SQUID**) | $I_c(\Phi) = 2I_c\left\lvert\cos(\pi\Phi/\Phi_0)\right\rvert$ — thread flux, tune $E_J$, tune the qubit frequency in situ |

The SQUID is the standard trick and the standard liability: it buys frequency tunability and pays with sensitivity to flux noise, since $\partial\omega/\partial\Phi \neq 0$ away from the flux sweet spot.

**Fabrication.** Al/AlO$_x$/Al with a 1–2 nm thermal oxide, patterned by double-angle shadow evaporation through a suspended resist bridge (**Dolan bridge**) — the two-angle deposition that [[Thin-Film Deposition]] describes as a use for line-of-sight arrival. Barrier thickness enters $I_c$ exponentially, so the tunnel barrier is the most damage-sensitive structure on the chip: a few-eV sputtered atom is a large fraction of it.

**Where else it appears:** SQUID magnetometers (flux resolution $\ll\Phi_0$); the Josephson voltage standard (Shapiro steps — irradiate at $f$, get quantized $V = nf\Phi_0$); Josephson parametric amplifiers, where the same nonlinearity provides near-quantum-limited gain for [[Superconducting Qubits|dispersive readout]]; and superconducting digital logic.

> [!question]- Why can a Josephson junction make a qubit when a diode — also nonlinear — cannot?
> The diode dissipates. Nonlinearity alone gives unequal level spacings, but any resistive element couples the circuit to a thermal bath and destroys coherence faster than gates can run. Pair tunneling carries current with no voltage and no dissipation, so the junction supplies anharmonicity *for free*.

# Connections

- [[Superconducting Qubits]] — the artificial atom this element makes possible; $E_J/E_C$ regimes
- [[Superconductivity]] — Cooper pairs, the gap $\Delta$, and macroscopic phase coherence
- [[LC Resonators]] — the linear circuit the junction makes anharmonic
- [[TLS and Dielectric Loss]] — the barrier and its interfaces as the dominant loss host
- [[Thin-Film Deposition]] — shadow evaporation, and why the barrier is damage-sensitive
- [[Commutators and Anticommutators]] — $[\hat\varphi,\hat n] = i$ as a conjugate pair
- [[Quantum Dots]] — the normal-state cousin: charging energy without pair tunneling

---
Source: Tinkham, *Introduction to Superconductivity*, Ch. 6; Krantz et al., "A Quantum Engineer's Guide to Superconducting Qubits," *Appl. Phys. Rev.* 6, 021318 (2019)
