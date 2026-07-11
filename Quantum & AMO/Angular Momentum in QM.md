#quantum #AMO

**Angular momentum is anything obeying $[J_i, J_j] = i\hbar\,\epsilon_{ijk}J_k$ — the algebra alone forces the entire ladder structure**, half-integer $j$ included, no wavefunctions required. Orbital, spin, total: identical machinery.

# Reference

Commuting pair $J^2, J_z$ label states:

$$J^2|j,m\rangle = \hbar^2 j(j+1)|j,m\rangle, \qquad J_z|j,m\rangle = \hbar m|j,m\rangle, \quad m = -j, \dots, +j$$

Ladders $J_\pm = J_x \pm iJ_y$ walk $m$ up and down:

$$J_\pm|j,m\rangle = \hbar\sqrt{j(j+1) - m(m\pm1)}\;|j,m\pm1\rangle$$

— vanishing at the ends is what quantizes $j$ to $0, \tfrac{1}{2}, 1, \tfrac{3}{2}, \dots$ Orbital $l$ is restricted to integers (spherical harmonics must be single-valued in $\varphi$); spin has no spatial wavefunction, so half-integers survive.

**Addition of two angular momenta:** $j_1 \otimes j_2$ decomposes into total $J = |j_1 - j_2|, \dots, j_1 + j_2$ in integer steps, one copy each; dimension check $\sum_J (2J+1) = (2j_1+1)(2j_2+1)$. The unitary connecting product basis to coupled basis is the table of [[Clebsch-Gordan Coefficients]].

$J_z$ generates rotations about $z$: $R_z(\theta) = e^{-i\theta J_z/\hbar}$ — this is why $[J_i,J_j]$ has that form (rotations don't commute).

> [!question]- Why can spin be $\tfrac{1}{2}$ but orbital angular momentum can't?
> The commutator algebra permits all half-integer $j$. Orbital $L$ additionally acts on functions of position: $e^{im\varphi}$ must return to itself after $2\pi$, forcing integer $m$ and hence integer $l$. Spin lives in an internal space with no such constraint.

# Connections

- [[Clebsch-Gordan Coefficients]] — the numbers that implement addition of angular momenta
- [[Spin-1-2]] — the smallest ($j=\tfrac{1}{2}$) representation, worked out explicitly
- [[Generators and the Exponential Map]] — $J$ as generator of rotations; SU(2) from the algebra
- [[Legendre Polynomials and Spherical Harmonics]] — the position-space faces of $|l,m\rangle$

---
Source: Sakurai, *Modern Quantum Mechanics*, Ch. 3
