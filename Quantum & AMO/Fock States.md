#quantum

**Exactly $n$ quanta, no amplitude: the energy eigenstates $|n\rangle$ have definite number but completely undefined phase — maximally non-classical, the opposite pole from coherent states.** "One photon" is a Fock state, and nothing classical emits one.

# Reference

$$
\hat n|n\rangle = n|n\rangle, \qquad |n\rangle = \frac{(a^\dagger)^n}{\sqrt{n!}}|0\rangle, \qquad E_n = \hbar\omega\left(n+\tfrac12\right)
$$

**No field amplitude, ever:** $\langle n|a|n\rangle = 0$, so $\langle x\rangle = \langle E\rangle = 0$ for all $t$ — yet $\langle x^2\rangle = (2n+1)x_0^2$ grows with $n$. Energy without a waveform: in phase space, a ring of radius $\sim\sqrt{n}$ with uniform (i.e., undefined) phase. This is number-phase complementarity: $\Delta n = 0$ forces the phase fully random.

**Statistics:** $\Delta n = 0$ — infinitely sub-Poissonian, $g^{(2)}(0) = 1 - 1/n < 1$ (0 for $n=1$: perfect antibunching, the single-photon signature no classical field can fake). Wigner function has negative rings for every $n \geq 1$ — nonclassicality certified.

**Fragility:** one lost photon takes $|n\rangle \to |n{-}1\rangle$, orthogonal — Fock states decohere at rate $\propto n$, which is why big ones are hard to keep. Contrast the loss-immune coherent state.

Lab reality: heralded down-conversion, single emitters, and in ions deterministic Fock-state prep of the motion by stacked blue-sideband $\pi$ pulses ($|n\rangle$ climbed one rung at a time — each pulse duration rescaled by the $\sqrt{n+1}$ ladder factor).

> [!question]- A Fock state has energy $n\hbar\omega$ but $\langle E$-field$\rangle = 0$ at every instant. How?
> The field operator is $\propto a + a^\dagger$, which only connects $n \to n\pm1$: diagonal expectation vanishes. All the energy sits in the *variance* — a definite-photon-number state is an equal mixture of all field phases, so the mean waveform averages to zero while $\langle E^2\rangle \propto n + \tfrac12$.

# Connections

- [[Quantum Harmonic Oscillator]] — these are its eigenstates
- [[Photon Statistics and g2]] — $g^{(2)}(0) < 1$ as the nonclassical flag
- [[Ladder Operators]] — $a^\dagger$ builds them, $\sqrt{n}$ factors and all
- [[Coherent States]] — the antithesis: defined phase, Poissonian number
- [[Sideband Transitions]] — how ion trappers actually synthesize $|n\rangle$

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 2
