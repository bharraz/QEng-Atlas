#quantum

**Split $H = H_0 + V$, let the boring part $H_0$ carry the operators and only the interesting part $V$ drive the states.** This strips the fast trivial phases so what's left is slow dynamics you can approximate — it's where perturbation theory and the RWA live.

# Reference

With $U_0 = e^{-iH_0 t/\hbar}$:
$$
|\psi_I(t)\rangle = U_0^\dagger|\psi_S(t)\rangle, \qquad O_I(t) = U_0^\dagger\, O\, U_0
$$
$$
i\hbar\,\partial_t|\psi_I\rangle = V_I(t)\,|\psi_I\rangle, \qquad V_I = U_0^\dagger V U_0
$$

States evolve under $V_I$ *only* — if $V=0$, interaction-picture states sit still. The price: $V_I$ picks up oscillating factors. Sandwiching $|m\rangle\langle n|$ terms of $V$ between the $U_0$'s dresses them with $e^{i\omega_{mn}t}$, $\omega_{mn} = (E_m - E_n)/\hbar$ — **every matrix element now oscillates at its transition frequency.** A drive at $\omega$ near $\omega_{mn}$ produces slow terms $e^{i(\omega_{mn}-\omega)t}$ (keep) and fast terms $e^{i(\omega_{mn}+\omega)t}$ (drop — that's the [[Rotating Wave Approximation]]).

**Why bother:** the remaining evolution is slow (rate $\sim V/\hbar$, not $E_n/\hbar$), so iterating the equation of motion converges — that iteration is the Dyson series of [[Time-Dependent Perturbation Theory]].

Interaction picture with $H_0 = \hbar\omega_{\text{drive}}\,(\text{number-like operator})$ rather than the true atomic $H_0$ is the same maneuver as a [[Rotating Frame Transformation]] — same formulas, different choice of what to rotate away.

> [!question]- Why do the matrix elements of $V_I$ oscillate at the transition frequencies?
> $U_0^\dagger |m\rangle\langle n| U_0 = e^{i(E_m - E_n)t/\hbar}|m\rangle\langle n|$ — each ket and bra contributes its energy phase. Resonance is then visible by inspection: a drive component at $\omega \approx \omega_{mn}$ makes that term quasi-static while everything else averages away.

# Connections

- [[Rotating Frame Transformation]] — the same unitary trick with a frame you choose, not necessarily $H_0$
- [[Rotating Wave Approximation]] — executed on $V_I$'s fast terms
- [[Time-Dependent Perturbation Theory]] — iterate $i\hbar\,\partial_t|\psi_I\rangle = V_I|\psi_I\rangle$ and you have it
- [[Heisenberg and Schrodinger Pictures]] — the two limits this interpolates between

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §5.5
