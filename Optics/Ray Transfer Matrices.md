#optics

**A paraxial ray is a 2-vector (height, angle); every element is a 2×2 matrix** — cascade a system by multiplying matrices, and the same matrices propagate Gaussian beams through the q-parameter.

# Reference

$$
\begin{pmatrix} y_2 \\ \theta_2 \end{pmatrix} = \begin{pmatrix} A & B \\ C & D \end{pmatrix} \begin{pmatrix} y_1 \\ \theta_1 \end{pmatrix}
$$

| Element | Matrix |
|---|---|
| Free space $d$ | $\begin{pmatrix} 1 & d \\ 0 & 1 \end{pmatrix}$ |
| Thin lens $f$ | $\begin{pmatrix} 1 & 0 \\ -1/f & 1 \end{pmatrix}$ |
| Mirror, radius $R$ | $\begin{pmatrix} 1 & 0 \\ -2/R & 1 \end{pmatrix}$ |
| Flat interface $n_1 \to n_2$ | $\begin{pmatrix} 1 & 0 \\ 0 & n_1/n_2 \end{pmatrix}$ |

**System matrix = product in reverse order** — last element hit is leftmost. $\det M = n_1/n_2$ (unity in air, a good sanity check).

**Imaging condition: $B = 0$** — output height independent of input angle, so a point maps to a point; magnification is then $A$. A curved mirror is a lens with $f = R/2$.

**Gaussian beams ride the same matrices:**
$$
q_2 = \frac{A q_1 + B}{C q_1 + D}
$$
so one 2×2 product designs both the ray layout and the beam waists. Cavity stability is the statement that the round-trip matrix has bounded powers: $|A+D| \le 2$.

> [!question]- Why does the *ray* matrix correctly propagate a *Gaussian beam's* complex q?
> The paraxial wave equation and paraxial ray optics share the same quadratic phase structure — a Gaussian is fully specified by the curvature and width that $1/q$ encodes, and both transform exactly like the ratio $y/\theta$ of a ray pencil. Huygens integral with the ABCD kernel makes it exact (Siegman Ch. 20).

# Connections

- [[Gaussian Beams]] — the $q' = (Aq+B)/(Cq+D)$ rule is why this table matters daily
- [[Telescopes and Beam Expanders]] — two-lens matrices give magnification and divergence scaling in one line
- [[Mode Matching]] — design lens solutions by demanding the output $q$ equals the target
- [[Optical Cavity Stability]] — the $|A+D| \le 2$ criterion is the $g_1g_2$ condition in disguise

---
Source: Siegman, *Lasers*, Ch. 15
