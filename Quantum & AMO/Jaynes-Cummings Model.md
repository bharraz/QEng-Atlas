#quantum #AMO

**One two-level system + one quantized mode + RWA: the simplest fully-quantum light-matter model, exactly solvable because it breaks into 2×2 blocks — a ladder of doublets split by $2g\sqrt{n+1}$.** Cavity QED and ion sideband physics are both this Hamiltonian.

# Reference

$$
H = \frac{\hbar\omega_0}{2}\sigma_z + \hbar\omega\, a^\dagger a + \hbar g\left(a\,\sigma_+ + a^\dagger\sigma_-\right)
$$

Term by term: $\omega_0$ = atomic transition frequency (rad/s) with $\sigma_z$ the inversion — the atom's energy; $\omega$ = mode frequency (rad/s) with $a^\dagger a$ the photon number — the field's energy; $g$ = single-photon coupling rate (rad/s), the exchange term. $a\sigma_+$ = absorb a photon and excite the atom, $a^\dagger\sigma_-$ = its reverse; keeping only these two (and dropping $a\sigma_-$, $a^\dagger\sigma_+$, which would create or destroy two excitations at once) is the RWA and is what makes excitation number conserved.

The RWA coupling conserves excitation number $N = a^\dagger a + \sigma_+\sigma_-$, so $H$ block-diagonalizes on pairs $\{|e,n\rangle, |g,n{+}1\rangle\}$ — each block a [[Two-Level Systems]] problem with detuning $\Delta = \omega_0 - \omega$ and coupling $2g\sqrt{n+1}$:

$$
E_{\pm,n} = \hbar\omega\left(n+\tfrac12\right) \pm \frac{\hbar}{2}\sqrt{\Delta^2 + 4g^2(n+1)}
$$

$n$ = photon number of the lower member of the pair; $\Delta = \omega_0 - \omega$ = atom–cavity detuning (rad/s); the square root is the familiar two-level generalized splitting with effective coupling $2g\sqrt{n+1}$. The $\sqrt{n+1}$ comes directly from $a^\dagger|n\rangle = \sqrt{n+1}\,|n{+}1\rangle$ — coupling grows as the square root of photon number, which is exactly the classical-field limit (amplitude $\propto \sqrt{\text{intensity}}$) except that the $+1$ survives at $n = 0$.

**On resonance:** doublets split by $2\hbar g\sqrt{n+1}$ — the **quantized-Rabi** anharmonic ladder. Splitting exists even for $n = 0$: **vacuum Rabi splitting $2g$** — an excited atom and an *empty* cavity exchange one quantum coherently at $2g$ (reversible spontaneous emission; observable when $g \gg \kappa, \Gamma$). The $\sqrt{n+1}$ anharmonicity is intrinsically quantum — a classical field gives $n$-independent Rabi — and its observation (collapse-and-revival of Rabi oscillations for a coherent field, since each $n$ flops at its own rate and rephases) was direct evidence for field quantization.

**Dispersive limit** ($|\Delta| \gg g\sqrt n$): second-order shifts $\pm\frac{g^2}{\Delta}(n + \tfrac12 \pm \tfrac12)$-type — atom frequency pulled per photon (light shift), cavity pulled per qubit state: the readout mechanism of circuit QED.

**Ion-trap realization:** in the Lamb-Dicke regime, the red sideband drives $|g,n\rangle \leftrightarrow |e,n{-}1\rangle$ with $g \to \eta\Omega/2$ — JC with the phonon mode playing the cavity field (blue sideband = anti-JC, $a^\dagger\sigma_+$).

> [!question]- What experimental signature separates the JC model from a two-level atom driven by a classical field?
> The $\sqrt{n+1}$: a classical drive flops at one Rabi frequency, JC flops at $2g\sqrt{n+1}$ per Fock component. A coherent field's spread of $n$ dephases the flopping (collapse), then discretely rephases (revival) — impossible for any classical field, which has a continuous amplitude.

# Connections

- [[Rotating Wave Approximation]] — what reduces the Rabi model to this solvable form
- [[Sideband Transitions]] — the trapped-ion incarnation, phonons for photons
- [[Cavity QED]] — the platform where $g$ vs $\kappa, \Gamma$ decides visibility
- [[Dressed States]] — $|\pm, n\rangle$ are their fully quantized version
- [[Ladder Operators]] — source of the $\sqrt{n+1}$ matrix elements

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 4
