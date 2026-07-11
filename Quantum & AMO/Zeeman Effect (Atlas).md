 #AMO

**A magnetic field splits each level by $m_F$: linear shifts of $g_F m_F \times 1.4\ \mathrm{MHz/G}$ — the number that sets both your addressing splittings and your field-noise sensitivity.**

# Reference

$H_Z = -\boldsymbol{\mu}\cdot\mathbf{B} = g_F \mu_B m_F B$ in the weak-field (good-$F$) regime, with

$$\frac{\mu_B}{h} = 1.3996\ \mathrm{MHz/G} \approx 1.4\ \mathrm{MHz/G}$$

Landé factors:

$$g_J = 1 + \frac{J(J{+}1) + S(S{+}1) - L(L{+}1)}{2J(J{+}1)}, \qquad g_F \simeq g_J\,\frac{F(F{+}1) + J(J{+}1) - I(I{+}1)}{2F(F{+}1)}$$

(nuclear moment neglected — $\mu_N/\mu_B \sim 1/1836$). Reference points: $S_{1/2}$ has $g_J = 2$; a $^2S_{1/2}$, $F = I \pm \tfrac{1}{2}$ manifold has $g_F = \pm g_J/(2I+1)$, e.g. $\pm 1$ for $^{171}$Yb⁺ $F=1$ ⇒ 1.4 MHz/G per $m_F$.

**Regimes:** linear ($m_F$ good) while $g\mu_B B \ll A$; as the field grows, $I$ and $J$ decouple (**Paschen–Back**): eigenstates become $|m_J, m_I\rangle$, shifts $\sim g_J \mu_B m_J B$. In between, diagonalize $A\,\mathbf{I}\cdot\mathbf{J} + H_Z$ — for $J = \tfrac{1}{2}$ that's the closed-form Breit–Rabi formula. Crossover scale: $B \sim A/\mu_B$ (hundreds to thousands of G for GHz-scale $A$).

**In practice:** a few-G bias field defines the quantization axis and fans out the $m_F$ levels by a few MHz — enough to resolve $\sigma^\pm/\pi$ transitions and pump to a single state. The same coefficient prices your decoherence: a stretched-state qubit with $\Delta(g_F m_F) = 1$ dephases at 1.4 kHz per mG of field noise, which is why clock ($m_F{=}0$) states or field-insensitive transitions win for memory.

> [!question]- Your qubit splitting drifts 3 kHz peak-to-peak. If it's a transition with net $g_F m_F$ difference of 1, what field stability does that imply, and what are the fixes?
> $3\ \mathrm{kHz} / (1.4\ \mathrm{MHz/G}) \approx 2\ \mathrm{mG}$ drift. Fixes: magnetic shielding, current-stabilized coils, switch to an $m_F = 0 \leftrightarrow 0$ clock transition (quadratic only), or dynamical decoupling if the noise is slow.

# Connections

- [[Hyperfine Structure]] — supplies the $F, m_F$ levels being split, and the $A$ that sets the Paschen–Back crossover
- [[Magnetostatics]] — coil and solenoid formulas for actually producing the bias field
- [[Spin-1-2]] — the same $\mu \cdot B$ physics as Larmor precession, in level-shift language

---
Source: Foot, *Atomic Physics*, §5.5 & §6.3
