#quantum

**Split a Hamiltonian into a part $H_0$ you can solve exactly — usually the bare energy levels — and the rest $V$; then let $H_0$'s fast, known phase evolution be carried by the operators, so that the states change only because of $V$.** This removes the trivial phases and leaves slow dynamics that can be approximated. It is where perturbation theory and the rotating-wave approximation are carried out.

# Reference

With $U_0 = e^{-iH_0 t/\hbar}$:

$$
|\psi_I(t)\rangle = U_0^\dagger|\psi_S(t)\rangle, \qquad O_I(t) = U_0^\dagger\, O\, U_0, \qquad i\hbar\,\partial_t|\psi_I\rangle = V_I(t)\,|\psi_I\rangle, \qquad V_I = U_0^\dagger V U_0
$$

- $\lvert\psi_S\rangle$ — the state in the ordinary (Schrödinger) picture
- $\lvert\psi_I\rangle$ — the same state with $H_0$'s evolution removed
- $V_I(t)$ — the perturbation as seen in the interaction picture: now time-dependent

States evolve under $V_I$ only; if $V = 0$, interaction-picture states stand still.

**Picture:** watch a carousel from one of its seats — the ride's rotation ($H_0$) disappears, and only motion relative to the ride ($V$) remains.

**Every matrix element now oscillates at its transition frequency.** Sandwiching a term $|m\rangle\langle n|$ of $V$ between the $U_0$'s gives

$$
\big(V_I\big)_{mn} = V_{mn}\,e^{i\omega_{mn}t}, \qquad \omega_{mn} = \frac{E_m - E_n}{\hbar}
$$

- $V_{mn}$ — the coupling in the original picture (J)
- $\omega_{mn}$ — transition frequency between the two bare levels (rad/s)

The diagonal energy difference has moved into the time dependence of the off-diagonal coupling ([[Reading Matrices and Hamiltonians]]). A drive at $\omega$ near $\omega_{mn}$ produces slow terms $e^{i(\omega_{mn}-\omega)t}$, which are kept, and fast terms $e^{i(\omega_{mn}+\omega)t}$, which are dropped: the [[Rotating Wave Approximation (Atlas)]].

| Term in $V_I$ | Oscillates at | Effect over many periods |
|---|---|---|
| resonant: $\omega \approx \omega_{mn}$ | $\lvert\omega_{mn} - \omega\rvert \ll \lvert V_{mn}\rvert/\hbar$ | acts fully: population transfer |
| near resonant | comparable to $\lvert V_{mn}\rvert/\hbar$ | partial transfer at the generalized Rabi frequency |
| far off resonance | $\gg \lvert V_{mn}\rvert/\hbar$ | averages away at first order; leaves a second-order shift $\lvert V\rvert^2/\hbar\Delta$ |
| counter-rotating | $\omega_{mn} + \omega$ | dropped in the RWA; leaves a Bloch–Siegert shift at second order |

**Why it converges:** the remaining evolution is slow, at a rate of order $V/\hbar$ rather than $E_n/\hbar$, so iterating the equation of motion converges. That iteration is the Dyson series of [[Time-Dependent Perturbation Theory]].

An interaction picture built from $H_0 = \hbar\omega_\text{drive} \times$ (a number-like operator) instead of the true atomic $H_0$ is a [[Rotating Frame Transformation]]: the same formulas, with a different choice of what to rotate away.

> [!question]- Why do the matrix elements of $V_I$ oscillate at the transition frequencies?
> $U_0^\dagger |m\rangle\langle n| U_0 = e^{i(E_m - E_n)t/\hbar}|m\rangle\langle n|$: the ket and the bra each contribute their own energy phase. Resonance is then visible by inspection — a drive component at $\omega \approx \omega_{mn}$ makes that term nearly static, while everything else averages away.

# Connections

- [[Rotating Frame Transformation]] — the same unitary change of frame, with a frame you choose
- [[Rotating Wave Approximation (Atlas)]] — carried out on $V_I$'s fast terms
- [[Time-Dependent Perturbation Theory]] — iterate $i\hbar\,\partial_t|\psi_I\rangle = V_I|\psi_I\rangle$
- [[Heisenberg and Schrodinger Pictures]] — the two limits this interpolates between
- [[Reading Matrices and Hamiltonians]] — diagonal differences reappearing as rotating couplings
- [[Effective Hamiltonians and Adiabatic Elimination]] — what far-off-resonant terms leave behind at second order

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §5.5
