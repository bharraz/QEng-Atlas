#quantum-info

**A gate set is universal if it can approximate any unitary to arbitrary accuracy — Clifford+T is the canonical choice** because Cliffords are cheap in error-corrected hardware and $T$ supplies the one ingredient they lack.

# Reference

**Discrete route: $\{H, S, \text{CNOT}\} + T$**, with $T = \mathrm{diag}(1, e^{i\pi/4})$. The Cliffords alone form a finite group (never dense in $SU(2^n)$, and Gottesman-Knill simulable); one non-Clifford gate breaks both obstructions.

**Continuous route: any entangling two-qubit gate + arbitrary single-qubit rotations** is universal — this is what hardware natively has (e.g. Mølmer-Sørensen + $R_{\hat n}(\theta)$, compiled down to CNOT when needed).

**Solovay-Kitaev**: any single-qubit unitary is approximated to $\epsilon$ using $O(\log^c(1/\epsilon))$ gates from any dense finite set — precision is *cheap*, only polylog overhead. Modern number-theoretic synthesis does better: $\approx 3\log_2(1/\epsilon)$ $T$ gates per rotation.

**Cost accounting in fault tolerance**: Cliffords are (nearly) free — transversal or lattice-surgery-native — while every $T$ consumes a distilled magic state. Circuit cost $\approx$ $T$-count, which is why compilers minimize $T$'s, not total gates.

> [!question]- Why can't the Clifford group alone be universal, even though it generates massive entanglement?
> It's a *finite* group — orbits of stabilizer states never fill Hilbert space — and Gottesman-Knill makes every Clifford circuit classically simulable. Universality requires escaping both, which any single non-Clifford gate ($T$) does.

# Connections

- [[Clifford Group]] — the free, simulable backbone that $T$ completes
- [[Single-Qubit Gates]] — the $SU(2)$ layer; two rotation axes already give all of it
- [[Entangling Gates]] — the one two-qubit ingredient the continuous criterion needs
- [[Magic and Nonstabilizerness]] — what the $T$ gate actually adds, as a resource

---
Source: Nielsen & Chuang, Ch. 4.5 + Appendix 3 (Solovay-Kitaev)
