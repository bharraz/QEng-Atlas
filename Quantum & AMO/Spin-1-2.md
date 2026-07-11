#quantum #AMO

**The minimal quantum system: two states, $S = \tfrac{\hbar}{2}\boldsymbol{\sigma}$, and everything about it is rotations.** Every qubit is secretly this.

# Reference

Spin operators are the Pauli matrices scaled: $S_i = \tfrac{\hbar}{2}\sigma_i$, satisfying $[S_i, S_j] = i\hbar\,\epsilon_{ijk}S_k$ with $S^2 = \tfrac{3}{4}\hbar^2$ fixed. Rotation by $\theta$ about axis $\hat{n}$:

$$R_{\hat{n}}(\theta) = e^{-i\theta\,\hat{n}\cdot\boldsymbol{\sigma}/2} = \cos\tfrac{\theta}{2}\,\mathbb{1} - i\sin\tfrac{\theta}{2}\,\hat{n}\cdot\boldsymbol{\sigma}$$

**A $2\pi$ rotation gives $-1$, not $+1$** — spinors need $4\pi$ to come home. The global sign is unobservable on an isolated spin but real in interferometry (rotate one arm by $2\pi$: fringes flip).

**Magnetic moment and Larmor precession:** $\boldsymbol{\mu} = \gamma \mathbf{S}$ with $\gamma = -g_s\mu_B/\hbar$, $g_s \approx 2.0023$ for the electron. In field $B\hat{z}$, $H = -\boldsymbol{\mu}\cdot\mathbf{B}$ makes the spin precess at

$$\omega_L = |\gamma| B \qquad (\approx 2\pi \times 2.8\ \text{MHz/G for a free electron})$$

— the Bloch vector circles $\hat{z}$ at $\omega_L$. Every magnetic resonance experiment (NMR, ESR, qubit control) is this precession plus a resonant drive viewed in the rotating frame.

Any pure state: $|\psi\rangle = \cos\tfrac{\theta}{2}|{\uparrow}\rangle + e^{i\phi}\sin\tfrac{\theta}{2}|{\downarrow}\rangle$ — a point $(\theta, \phi)$ on the [[Bloch Sphere]].

> [!question]- Why does a $\pi$ rotation about $\hat{x}$ swap $|{\uparrow}\rangle \leftrightarrow |{\downarrow}\rangle$ but a $2\pi$ rotation not return the identity?
> $R_{\hat{n}}(\theta)$ carries half-angles: $\theta = \pi$ gives $-i\sigma_x$ (a flip, up to phase), $\theta = 2\pi$ gives $\cos\pi = -\mathbb{1}$. SU(2) double-covers rotations — spinors keep track of the covering.

# Connections

- [[Pauli Matrices]] — the operator algebra this note runs on
- [[Bloch Sphere]] — the state space, with rotations as the gates
- [[Zeeman Effect (Atlas)]] — $\mu \cdot B$ level shifts, the atomic-structure face of the same moment
- [[Two-Level Systems]] — any two levels inherit this formalism, spin or not

---
Source: Sakurai, *Modern Quantum Mechanics*, Ch. 3 (spinor rotations §3.2)
