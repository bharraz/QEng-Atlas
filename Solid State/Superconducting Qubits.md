#solid-state #quantum-info

**An LC circuit made nonlinear by a Josephson junction, so its levels become unequally spaced and the lowest two form an addressable qubit — with one dimensionless ratio, $E_J/E_C$, naming every design in the field.**

# Reference

A plain **LC oscillator** cannot be a qubit: its levels are evenly spaced, so a drive resonant with $0\to1$ is equally resonant with $1\to2$ and population leaks out. The [[Josephson Junction]] is a nonlinear *lossless* inductor; replacing $L$ with it makes the spectrum **anharmonic** and isolates the $0\to1$ transition.

**The circuit Hamiltonian.** With $\hat n$ the Cooper pairs transferred across the junction and $\hat\varphi$ the phase difference ($[\hat\varphi, \hat n] = i$ — conjugate, exactly like $\hat x, \hat p$):

$$H = 4E_C\,(\hat{n} - n_g)^2 - E_J\cos\hat\varphi, \qquad E_C = \frac{e^2}{2C_\Sigma}, \qquad E_J = \frac{\Phi_0 I_c}{2\pi}$$

$\hat n$ = pair number (dimensionless integer operator — the "momentum"); $\hat\varphi$ = phase across the junction (rad — the "position"); $n_g$ = offset charge in pairs, set by the environment and drifting, the noise source the transmon defeats; $E_C$ = charging energy per electron, with $C_\Sigma$ the total island capacitance — the factor 4 converts to per-Cooper-pair, $(2e)^2/2C_\Sigma = 4E_C$; $E_J$ = Josephson energy, the depth of the cosine. Expanding $\cos\hat\varphi$, the quadratic term is the LC oscillator and the quartic term $-E_J\hat\varphi^4/24$ is the anharmonicity. It is a quantum pendulum: $E_C$ the inertia, $E_J$ the gravity.

## $E_J/E_C$ names the qubit

The two energies compete as kinetic vs. potential. Large $E_C$ (small capacitor) localizes charge and makes phase uncertain; large $E_J$ localizes phase and makes charge uncertain. That single ratio therefore fixes which variable is well defined, which noise channel dominates, and how anharmonic the spectrum is:

| $E_J/E_C$ | Name | Well-defined variable | Dominant noise | Anharmonicity |
|---|---|---|---|---|
| $\ll 1$ | charge qubit / box | charge $n$ | charge ($n_g$) — severe | large |
| $\sim 50$–$100$ | **transmon** | neither; phase-ish | flux (if SQUID-tuned), TLS | weak, $\approx -E_C$ |
| $\gg 1$ | flux / phase qubit | phase $\varphi$ | flux | large |
| $\gg 1$ with inductive shunt | fluxonium | phase, in a multi-well potential | flux | very large |

**The transmon's design insight, in one line:** as $E_J/E_C$ grows, charge dispersion (sensitivity to $n_g$) falls **exponentially** in $\sqrt{8E_J/E_C}$ while anharmonicity falls only **algebraically**. Trading a little anharmonicity buys an enormous amount of charge-noise immunity, so the optimum sits far into the large-$E_J/E_C$ regime rather than at a balance point. In that limit
$$\hbar\omega_{01} \approx \sqrt{8E_J E_C} - E_C, \qquad \alpha \equiv \omega_{12} - \omega_{01} \approx -E_C/\hbar$$

The price is a speed limit: pulses shorter than $\sim 1/|\alpha|$ have spectral content at $\omega_{12}$ and leak into $|2\rangle$, mitigated by pulse shaping (DRAG). **Gate speed and charge-noise immunity are the same trade**, read off the one ratio.

$\omega_{01}$ lands in the 4–8 GHz band for reasons that will not move: below it, $\hbar\omega \not\gg k_BT$ at millikelvin; above it, microwave components and $\Delta$ for aluminium get difficult.

## Coupling and readout

The qubit couples to a microwave resonator — **circuit QED**, a [[Jaynes-Cummings Model (Atlas)|Jaynes–Cummings]] system on a chip ([[Cavity QED]]) — detuned by $\Delta = \omega_q - \omega_r$. In the **dispersive regime** $|\Delta| \gg g$ the interaction becomes $H_{\text{disp}} = \hbar\chi\,\hat\sigma_z\,\hat a^\dagger\hat a$ with

$$\chi = \frac{g^2}{\Delta}\cdot\frac{\alpha}{\Delta + \alpha}$$

the second factor being the transmon's third level correcting the two-level result. The resonator frequency shifts by $\pm\chi$ with qubit state, so a weak probe tone carries the answer in its phase — a **QND** measurement, since $\hat\sigma_z$ commutes with $H_\text{disp}$.

Readout only works because the signal is amplified before it can be swamped: a Josephson parametric amplifier or TWPA provides near-quantum-limited gain using the *same* junction nonlinearity that makes the qubit. Dispersive readout is a trade too — larger $\chi$ reads out faster but opens a **Purcell** channel for the qubit to decay through the resonator, fixed with a Purcell filter that is transparent at $\omega_r$ and opaque at $\omega_q$.

**Two-qubit gates** come from turning couplings on and off, not from a fixed interaction: flux-tune two qubits into resonance (iSWAP), drive one at the other's frequency (cross-resonance, CR), or interpose a **tunable coupler** whose flux bias nulls the effective $g$ — the dominant modern choice, because always-on coupling means always-on crosstalk ([[Entangling Gates]]).

## What limits coherence

Structural mechanisms rather than current records, since the records move and the mechanisms do not:

| Channel | Mechanism | Scaling / mitigation |
|---|---|---|
| **Dielectric loss (TLS)** | resonant absorption by surface and interface fluctuators | reduce participation ratio; saturable, so single-photon $Q$ is the figure that matters ([[TLS and Dielectric Loss]]) |
| **Flux noise** | $1/f$ magnetic fluctuations, likely surface spins, entering through the SQUID loop | vanishes at the flux sweet spot where $\partial\omega/\partial\Phi = 0$; otherwise $\propto \partial\omega/\partial\Phi$ ([[Flicker Noise]]) |
| **Charge noise** | $1/f$ offset-charge drift | exponentially suppressed by large $E_J/E_C$ — the transmon's reason for existing |
| **Purcell decay** | emission into the readout resonator | $\Gamma \approx \kappa (g/\Delta)^2$; Purcell filter |
| **Quasiparticles** | broken pairs tunnelling across the junction | gap engineering, infrared shielding, phonon traps |
| **Thermal photons** | residual population in the readout line | attenuation and filtering at each fridge stage ([[Cryogenics]]) |

> [!question]- Why does the transmon deliberately give up anharmonicity, when anharmonicity is the thing that makes a qubit possible?
> Because the two costs scale differently in $E_J/E_C$: charge dispersion falls exponentially while anharmonicity falls only as a power. A modest loss of level separation — paid for later with pulse shaping — buys charge-noise immunity that no amount of shielding could.

# Connections

- [[Josephson Junction]] — the nonlinear lossless element, $E_J$, and SQUID tunability
- [[Superconductivity]] — Cooper pairs and the gap the whole circuit relies on
- [[TLS and Dielectric Loss]] — the dominant coherence limit and how design fights it
- [[LC Resonators]] — the linear circuit the junction makes anharmonic
- [[Jaynes-Cummings Model (Atlas)]] / [[Cavity QED]] — circuit QED and the dispersive limit
- [[Quantum Dots]] — the normal-state cousin: same charging energy, no pair tunneling
- [[T1 and T2]] — the coherence vocabulary the table above feeds
- [[Entangling Gates]] — where CR and tunable-coupler gates sit among two-qubit families
- [[Cryogenics]] — why millikelvin, and the filtering the readout chain needs

---
Source: Krantz et al., "A Quantum Engineer's Guide to Superconducting Qubits," *Appl. Phys. Rev.* 6, 021318 (2019); Koch et al., *Phys. Rev. A* 76, 042319 (2007)
