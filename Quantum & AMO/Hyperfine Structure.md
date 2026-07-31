 #AMO

**Nuclear spin $I$ couples to electronic $J$, splitting each fine-structure level into total-$F$ manifolds — and the GHz-scale, magnetically clean splittings this produces are where hyperfine qubits live.**

# Reference

$$H_{\mathrm{hfs}} = A\,\mathbf{I}\cdot\mathbf{J}, \qquad \mathbf{F} = \mathbf{I} + \mathbf{J}, \quad F = |I-J|, \dots, I+J$$

$\mathbf{I}$ = nuclear spin (dimensionless, in units of $\hbar$; a fixed property of the isotope: $\tfrac12$ for $^{171}$Yb⁺, $\tfrac32$ for $^{9}$Be⁺); $\mathbf{J} = \mathbf{L} + \mathbf{S}$ = total *electronic* angular momentum, the label of the fine-structure level ([[Angular Momentum in QM]], [[Atomic Structure]]); $\mathbf{F}$ = grand total, the good quantum number once hyperfine is on. $A$ = magnetic dipole hyperfine constant, an energy — quoted as $A/h$ in Hz, which is why splittings are stated in GHz.

Using $\mathbf{I}\cdot\mathbf{J} = \tfrac{1}{2}(F^2 - I^2 - J^2)$ (the same algebraic trick as spin–orbit):

$$E_F = \frac{A}{2}\,K, \qquad K \equiv F(F{+}1) - I(I{+}1) - J(J{+}1)$$

$K$ = dimensionless coupling factor, the eigenvalue of $2\,\mathbf{I}\cdot\mathbf{J}/\hbar^2$ — it counts how much the two spins are aligned ($K > 0$ for parallel, $K < 0$ for antiparallel), so $E_F$ is in energy units and the *sign* of $A$ decides which $F$ lies lowest. Add the electric quadrupole $B$-term when $J \ge 1$ and $I \ge 1$. Interval rule: $E_F - E_{F-1} = A F$ — successive splittings grow linearly in $F$, the standard check that an observed multiplet is hyperfine.

**Scale:** GHz for ground states — $^{171}$Yb⁺ $S_{1/2}$: 12.6428 GHz; $^{133}$Cs: 9.192 631 770 GHz (defines the second); $^{9}$Be⁺: 1.25 GHz; H: 1.42 GHz (21 cm line). Microwave-addressable, hence the appeal.

**Clock states:** for half-integer-$I$ species like $^{171}$Yb⁺ ($I = \tfrac{1}{2}$), the $|F{=}0, m_F{=}0\rangle \leftrightarrow |F{=}1, m_F{=}0\rangle$ transition has no linear Zeeman shift — only quadratic ($\sim 310\ \mathrm{Hz/G^2}$ in $^{171}$Yb⁺). Field-insensitive to first order ⇒ $T_2$ measured in minutes-to-hours. That plus effectively infinite $T_1$ (no spontaneous decay between ground hyperfine levels) is why **the qubit lives here**.

Physical origin: Fermi contact interaction (s-electrons overlap the nucleus) plus dipole–dipole; $A \propto |\psi(0)|^2$ for $s$ states, which is why $S_{1/2}$ splittings dominate.

> [!question]- Why pick $m_F = 0 \leftrightarrow m_F = 0$ for the qubit rather than stretched states?
> Zeeman shifts go as $g_F m_F \mu_B B$; $m_F = 0$ states have zero linear sensitivity, leaving only a quadratic residual. Magnetic field noise — the dominant dephasing source — is suppressed by orders of magnitude. Cost: you need a small bias field anyway to define the axis and split off the $m_F = \pm1$ spectators.

# Connections

- [[Atomic Structure]] — hyperfine sits one $\sim m_e/m_p$ rung below fine structure
- [[Zeeman Effect (Atlas)]] — how these $F, m_F$ levels move in a field; Breit–Rabi at intermediate field
- [[Qubits]] — the hyperfine qubit as the trapped-ion workhorse encoding
- [[Optical Pumping]] — state prep into a chosen $|F, m_F\rangle$

---
Source: Foot, *Atomic Physics*, Ch. 6
