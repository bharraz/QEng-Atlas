#quantum

**THE structure: if $[H, O] = \lambda O$, then $O$ maps eigenstates to eigenstates with energy shifted by exactly $\lambda$ — an eigenoperator of the commutator generates a ladder.** Everything else (oscillators, angular momentum, field modes) is this one identity wearing different clothes.

# Reference

**The master identity.** From $[H,O] = \lambda O$: if $H|E\rangle = E|E\rangle$,
$$
H\,(O|E\rangle) = (OH + [H,O])|E\rangle = (E + \lambda)\,(O|E\rangle)
$$
so $O|E\rangle$ is an eigenstate at $E + \lambda$ (or zero). **A commutation relation, not a differential equation, generates the spectrum.**

**Oscillator instance:** $[a, a^\dagger] = 1$, $\hat n = a^\dagger a$, $H = \hbar\omega(\hat n + \tfrac12)$ gives
$$
[H, a] = -\hbar\omega\, a, \qquad [H, a^\dagger] = +\hbar\omega\, a^\dagger
$$
$$
a|n\rangle = \sqrt{n}\,|n{-}1\rangle, \qquad a^\dagger|n\rangle = \sqrt{n{+}1}\,|n{+}1\rangle
$$
Ladder bounded below because $\langle n|\hat n|n\rangle = \|a|n\rangle\|^2 \geq 0$ forces termination: $a|0\rangle = 0$. (The $\sqrt{n+1}$ is bosonic enhancement — the same factor in JC coupling and sideband Rabi rates.)

**Conversion table** (convention $x_0 = \sqrt{\hbar/2m\omega}$, $p_0 = \hbar/2x_0 = \sqrt{m\hbar\omega/2}$):

| | |
|---|---|
| $x = x_0\,(a + a^\dagger)$ | $a = \dfrac{x}{2x_0} + \dfrac{i\,x_0\,p}{\hbar}$ |
| $p = i\,p_0\,(a^\dagger - a)$ | $a^\dagger = \dfrac{x}{2x_0} - \dfrac{i\,x_0\,p}{\hbar}$ |
| $x^2 = x_0^2\,(a^2 + a^{\dagger 2} + 2\hat n + 1)$ | $\langle 0\|x^2\|0\rangle = x_0^2$, i.e. $\Delta x_{\text{zpf}} = x_0$ |

(Watch conventions: some texts use $x_0 = \sqrt{\hbar/m\omega}$ — a stray $\sqrt2$ in Lamb-Dicke parameters comes from exactly this.)

**Same trick elsewhere:** $[J_z, J_\pm] = \pm\hbar J_\pm$ ladders $m$; $[\hat n, a] = -a$ ladders photon number; any equally-spaced spectrum admits such an eigenoperator. Spot a candidate $O$ with $[H,O] \propto O$ and the problem is algebraically solved.

> [!question]- Why does $[H, O] = \lambda O$ produce a ladder, and what terminates the oscillator's?
> $H(O|E\rangle) = (E+\lambda)(O|E\rangle)$: applying $O$ shifts the eigenvalue by $\lambda$ every time, generating the whole ladder from one state. For the oscillator, $\|a|n\rangle\|^2 = n \geq 0$ can't go negative — the chain must hit a state with $a|0\rangle = 0$, fixing the ground state and the $\hbar\omega/2$ offset.

# Connections

- [[Quantum Harmonic Oscillator]] — the canonical deployment
- [[Commutators and Anticommutators]] — the algebra this insight lives in
- [[Second Quantization]] — the same operators promoted to field modes
- [[Angular Momentum in QM]] — $J_\pm$: the other famous ladder
- [[Lamb-Dicke Regime]] — where $x = x_0(a + a^\dagger)$ enters $e^{ikx}$ and makes sidebands

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §2.3
