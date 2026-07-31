#solid-state

**Below a critical temperature some materials lose all DC resistance and expel magnetic field; the microscopic cause is electrons binding into Cooper pairs that condense into a single coherent quantum state protected by an energy gap.** The macroscopic phase and the Josephson junction that follow are the entire foundation of superconducting qubits.

# Reference

**Signatures:** zero DC resistance, and the **Meissner effect** — active expulsion of magnetic flux, a thermodynamic state, not merely perfect conductivity. Type I vs. Type II differ in how flux penetrates; each has critical field and critical current limits.

**Mechanism (BCS):** a phonon-mediated attraction (see [[Phonons]]) binds electrons of opposite momentum and spin into **Cooper pairs**, which are bosonic and condense. The condensate opens an **energy gap** $\Delta$: the cheapest excitation costs $2\Delta$, so at low energy there is nothing to scatter into. The BCS quantitative core:

$$\Delta(0) = 1.764\, k_B T_c, \qquad \Delta \approx 2\hbar\omega_D\, e^{-1/N(0)V},$$

$\Delta$ = superconducting energy gap (J), the binding energy per electron in a Cooper pair (so breaking a pair costs $2\Delta$); $T_c$ = critical temperature (K); $\omega_D$ = Debye frequency (rad/s), the phonon energy scale that sets the *cutoff* for which electrons can pair; $N(0)$ = density of states at the Fermi level (states per J per volume); $V$ = attractive pairing interaction strength (J·volume), so $N(0)V$ is dimensionless — the coupling constant — note the *non-perturbative* $e^{-1/x}$: no power series in the coupling finds superconductivity, and the tiny exponential is why $T_c \sim$ K while $E_F \sim 10^4$ K. For aluminum ($T_c = 1.2$ K): $2\Delta/h \approx 90$ GHz — the frequency ceiling below which a superconducting circuit is lossless, comfortably above the 4–8 GHz qubit band.

**Two lengths** organize all magnetic behavior: the **penetration depth** $\lambda$ (how far field leaks in — the Meissner screening length, from $\nabla^2\mathbf{B} = \mathbf{B}/\lambda^2$; ~50 nm in Al) and the **coherence length** $\xi$ (the Cooper-pair size, $\xi_0 = \hbar v_F/\pi\Delta$; ~1.6 µm in Al, ~40 nm in Nb). Their ratio $\kappa = \lambda/\xi$ decides Type I ($\kappa < 1/\sqrt{2}$, flux fully expelled) vs Type II ($\kappa > 1/\sqrt{2}$, flux enters as quantized vortices between $H_{c1}$ and $H_{c2}$). Trapped vortices are a loss and noise mechanism in qubit chips — hence magnetic shielding and, sometimes, flux-pinning holes in the ground plane.

**Macroscopic wavefunction:** the whole condensate is described by one complex order parameter $\psi = |\psi|\,e^{i\varphi}$ with a single phase $\varphi$ — the same macroscopic-coherence idea as a [[Bose-Einstein Condensation|BEC]]. Two consequences are the qubit toolkit:
- **Flux quantization** — the phase must be single-valued around a loop, so enclosed flux comes in units of $\Phi_0 = h/2e = 2.07\times10^{-15}$ Wb (the $2e$ is direct evidence of pairing). Lab number: $\Phi_0 \approx$ one 20 mG field through a $(10\,\mu\text{m})^2$ loop — why SQUIDs are exquisitely sensitive and why qubit loops need shielding.
- **Josephson junction** — two superconductors separated by a thin barrier carry a dissipationless supercurrent with the two Josephson relations
$$I = I_c\sin\varphi, \qquad \dot{\varphi} = \frac{2eV}{\hbar}.$$
Combining them: the junction behaves as a **nonlinear inductance** $L_J(\varphi) = \frac{\hbar}{2eI_c\cos\varphi} = \frac{\Phi_0}{2\pi I_c \cos\varphi}$, with energy $U(\varphi) = -E_J\cos\varphi$, $E_J = \hbar I_c/2e$. A typical transmon junction ($I_c \sim 30$ nA) gives $E_J/h \sim 15$ GHz and $L_J \sim 10$ nH — a huge lossless inductance in a µm² footprint. Two junctions in a loop (a **SQUID**) act as one junction with $E_J^{\text{eff}} = E_{J\Sigma}|\cos(\pi\Phi/\Phi_0)|$: a flux-tunable inductor, which is how tunable-frequency qubits tune.

> [!question]- Why does a small energy gap give exactly zero resistance rather than merely low resistance?
> Resistance requires carriers to scatter into nearby empty states. The paired condensate has a gap $2\Delta$ to every excitation, so at energies below the gap there are no states to scatter into — the current-carrying condensate cannot decay. That is genuine zero DC resistance, qualitatively different from a very good normal conductor.

# Connections

- [[Phonons]] — the pairing glue behind conventional superconductivity
- [[Bose-Einstein Condensation]] — Cooper pairs condensing is the same macroscopic-coherence phenomenon
- [[Superconducting Qubits]] — the Josephson junction and macroscopic phase are their building blocks
- [[LC Resonators]] — superconducting circuits are lossless LC elements plus junctions
- [[Bloch's Theorem and Band Structure]] — pairing happens among electrons near the Fermi level

---
Source: Tinkham, *Introduction to Superconductivity*, Ch. 1–3; Ashcroft & Mermin, *Solid State Physics*, Ch. 34
