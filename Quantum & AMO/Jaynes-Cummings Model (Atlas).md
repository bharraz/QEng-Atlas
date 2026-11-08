#quantum #AMO

**One two-level system + one quantized mode + RWA: the simplest fully-quantum light-matter model, exactly solvable because it breaks into 2×2 blocks — a ladder of doublets split by $2g\sqrt{n+1}$.** Cavity QED and ion sideband physics are both this Hamiltonian.

# Reference

$$
H = \frac{\hbar\omega_0}{2}\sigma_z + \hbar\omega\, a^\dagger a + \hbar g\left(a\,\sigma_+ + a^\dagger\sigma_-\right)
$$

- $\omega_0$ — atomic transition frequency (rad/s): with the inversion $\sigma_z$, sets the atom's energy
- $\omega$ — mode frequency (rad/s): with the photon number $a^\dagger a$, sets the field's energy
- $g$ — single-photon coupling rate (rad/s): the strength of the exchange term
- $a\sigma_+$ — absorb a photon and excite the atom; $a^\dagger\sigma_-$ is the reverse

Keeping only these two exchange terms, and dropping $a\sigma_-$ and $a^\dagger\sigma_+$ (which would create or destroy two excitations at once), is the [[Rotating Wave Approximation (Atlas)|rotating wave approximation]]. It conserves excitation number $N = a^\dagger a + \sigma_+\sigma_-$, so $H$ block-diagonalizes on pairs $\{|e,n\rangle, |g,n{+}1\rangle\}$ — each block a [[Two-Level Systems]] problem with detuning $\Delta = \omega_0 - \omega$ and coupling $2g\sqrt{n+1}$:

$$
E_{\pm,n} = \hbar\omega\left(n+\tfrac12\right) \pm \frac{\hbar}{2}\sqrt{\Delta^2 + 4g^2(n+1)}
$$

**Picture:** an atom and a cavity mode trading one excitation back and forth; with $n$ photons already present they trade faster, by $\sqrt{n+1}$.

- $n$ — photon number of the lower member of the pair

The square root is the ordinary two-level splitting with effective coupling $2g\sqrt{n+1}$. The $\sqrt{n+1}$ comes from $a^\dagger|n\rangle = \sqrt{n+1}\,|n{+}1\rangle$: coupling grows as the square root of photon number, as for a classical field (amplitude $\propto \sqrt{\text{intensity}}$), except that the $+1$ survives at $n = 0$.

**On resonance:** doublets split by $2\hbar g\sqrt{n+1}$ — the **quantized-Rabi** anharmonic ladder. Splitting exists even for $n = 0$: **vacuum Rabi splitting $2g$** — an excited atom and an *empty* cavity exchange one quantum coherently at $2g$ (reversible spontaneous emission; observable when $g \gg \kappa, \Gamma$). The $\sqrt{n+1}$ anharmonicity is intrinsically quantum — a classical field gives $n$-independent Rabi — and its observation (collapse-and-revival of Rabi oscillations for a coherent field, since each $n$ flops at its own rate and rephases) was direct evidence for field quantization.

**Dispersive limit** ($|\Delta| \gg g\sqrt{n+1}$): atom and field no longer exchange energy, they only shift each other's frequency:

$$
H_\text{disp} \approx \hbar(\omega + \chi\sigma_z)\,a^\dagger a + \tfrac{\hbar}{2}(\omega_0 + \chi)\,\sigma_z, \qquad \chi = \frac{g^2}{\Delta}
$$

- $\chi$ — dispersive shift (rad/s)

Equivalently, $|e,n\rangle$ shifts by $+\chi(n+1)$ and $|g,n\rangle$ by $-\chi n$. The cavity frequency moves by $\pm\chi$ depending on the atom's state, which is the readout mechanism of circuit QED ([[Superconducting Qubits]]); the atom's frequency moves by $2\chi$ per photon, the light shift.

**Ion-trap realization:** in the Lamb-Dicke regime, the red sideband drives $|g,n\rangle \leftrightarrow |e,n{-}1\rangle$ with $g \to \eta\Omega/2$ — JC with the phonon mode playing the cavity field (blue sideband = anti-JC, $a^\dagger\sigma_+$).

> [!question]- What experimental signature separates the JC model from a two-level atom driven by a classical field?
> The $\sqrt{n+1}$: a classical drive flops at one Rabi frequency, JC flops at $2g\sqrt{n+1}$ per Fock component. A coherent field's spread of $n$ dephases the flopping (collapse), then discretely rephases (revival) — impossible for any classical field, which has a continuous amplitude.

# Connections

- [[Rotating Wave Approximation (Atlas)]] — what reduces the Rabi model to this solvable form
- [[Sideband Transitions]] — the trapped-ion incarnation, phonons for photons
- [[Cavity QED]] — the platform where $g$ vs $\kappa, \Gamma$ decides visibility
- [[Dressed States]] — $|\pm, n\rangle$ are their fully quantized version
- [[Ladder Operators]] — source of the $\sqrt{n+1}$ matrix elements
- [[Circuit QED]] — the dispersive limit used for qubit readout

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 4
