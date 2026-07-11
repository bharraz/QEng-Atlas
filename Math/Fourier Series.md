#math

**Any periodic function is a sum of harmonics of its fundamental** — period $T$ forces the spectrum to be discrete lines at $n\omega_0 = 2\pi n/T$, and orthogonality of the harmonics lets you project out each coefficient independently.

# Reference

**Complex form** (use this one; the sin/cos form is the same thing unpacked):
$$
f(t) = \sum_{n=-\infty}^{\infty} c_n\, e^{in\omega_0 t}, \qquad
c_n = \frac{1}{T}\int_0^T f(t)\, e^{-in\omega_0 t}\, dt
$$
Real $f$ means $c_{-n} = c_n^*$. Sin/cos version: $a_n = c_n + c_{-n}$, $b_n = i(c_n - c_{-n})$.

**The projection is just an inner product:** harmonics are orthonormal under $\frac{1}{T}\int_0^T e^{i(n-m)\omega_0 t} dt = \delta_{nm}$, so each $c_n$ is "the component of $f$ along mode $n$" — the same move as expanding a state in an eigenbasis.

**Convergence facts worth knowing:** smoothness sets decay — a discontinuity gives $c_n \sim 1/n$ (square wave), a kink gives $1/n^2$ (triangle). **Gibbs:** at a jump the partial sums overshoot by ~9% no matter how many terms you keep; the overshoot narrows but never shrinks.

**Parseval:** $\frac{1}{T}\int_0^T |f|^2 dt = \sum_n |c_n|^2$ — power splits among the harmonics. This is why a square-wave drive at $\omega_0$ also hits resonances at $3\omega_0, 5\omega_0, \ldots$ (with $1/n$ amplitudes) — relevant for anything driven with fast edges.

> [!question]- Why does a square-wave drive excite a high-Q resonator sitting at three times the drive frequency?
> The square wave's series has only odd harmonics with amplitudes $\propto 1/n$ — its $n=3$ line lands exactly on the resonance and the $Q$ does the rest. Any non-sinusoidal drive is secretly a comb of tones.

# Connections

- [[Fourier Transform]] — send $T\to\infty$ and the line spectrum densifies into the continuous transform
- [[Inner Products and Orthogonality]] — coefficient extraction is orthogonal projection in L²
- [[Sturm-Liouville Theory]] — sines/cosines are the simplest S-L eigenbasis; the pattern generalizes
- [[Cavity Modes]] — periodic boundary conditions ⇒ discrete mode expansion, same math

---
Source: Boas, *Mathematical Methods in the Physical Sciences*, Ch. 7 §1–5
