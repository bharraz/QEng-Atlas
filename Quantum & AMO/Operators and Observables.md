#quantum #math

**An observable is a Hermitian operator; its eigenvalues are the possible measurement outcomes and its eigenbasis is the set of states with definite outcome. Everything else — expectation values, uncertainty, dynamics — is linear algebra on that spectral decomposition.** Operators that do not commute define incompatible measurements, and their commutator is the quantitative statement of the incompatibility.

# Reference

Spectral decomposition and what each piece means ([[Spectral Theorem]], [[Projectors]]):

$$A = \sum_a a\, P_a, \qquad \langle A \rangle = \langle\psi|A|\psi\rangle = \sum_a a\, \|P_a|\psi\rangle\|^2, \qquad \Delta A^2 = \langle A^2\rangle - \langle A\rangle^2.$$

$a$ = outcomes, $P_a$ = projector onto the eigenspace, $\|P_a|\psi\rangle\|^2$ = probability. Non-commuting observables share no full eigenbasis ([[Simultaneous Diagonalization]]); the Robertson bound quantifies the trade:

$$\Delta A\, \Delta B \geq \tfrac{1}{2}\left|\langle [A, B] \rangle\right|.$$

Operators come in three overlapping families: **Hermitian** ($A^\dagger = A$: real spectrum, observables), **unitary** ($U^\dagger U = 1$: norm-preserving, symmetries and evolution, $U = e^{-iA}$ for Hermitian $A$ — [[Generators and the Exponential Map]]), **normal** ($[A, A^\dagger] = 0$: diagonalizable by a unitary — everything above, plus e.g. non-Hermitian effective Hamiltonians when they happen to commute with their adjoint; ladder operators are none of these and have no orthogonal eigenbasis).

## Identities

**Similarity / conjugation** $X \mapsto VXV^{-1}$ is a change of basis (or frame): the operator's *action* is unchanged, its *representation* moves. Consequences, all from $(VXV^{-1})^n = VX^nV^{-1}$:

$$f(VXV^{-1}) = V f(X)\, V^{-1} \;\;\text{(any power series — in particular } V e^{X} V^{-1} = e^{VXV^{-1}}),$$

spectrum invariant; eigenvectors map $|v\rangle \mapsto V|v\rangle$; trace and determinant invariant ($\mathrm{Tr}\,ABC = \mathrm{Tr}\,BCA$, cyclic — [[Trace Identities]]). Reading: to evolve, rotate, or re-frame an *exponential*, conjugate its *generator* — never expand the exponential.

**Conjugation by an exponential** (Hadamard lemma, the workhorse of frame changes):

$$e^{A} B\, e^{-A} = B + [A, B] + \tfrac{1}{2!}[A,[A,B]] + \tfrac{1}{3!}[A,[A,[A,B]]] + \cdots$$

Terminates or closes in the common cases:

- $[A, B] = c$ (c-number): $e^A B e^{-A} = B + c$. Translation: $e^{-ip x_0/\hbar}\, \hat x\, e^{ip x_0/\hbar} = \hat x + x_0$; displacement: $D^\dagger(\alpha)\, a\, D(\alpha) = a + \alpha$ ([[Displacement Operator]]).
- $[A, B] \propto B$: $e^{A} B e^{-A} = e^{\lambda} B$ (scaling). Number operator vs ladder: $e^{i\theta n}\, a\, e^{-i\theta n} = a\, e^{-i\theta}$ — phase rotation, the interaction picture of an oscillator; squeezing scales quadratures the same way.
- $A, B$ two Paulis: the series is a rotation,
$$e^{-i\frac{\theta}{2}\sigma_z}\, \sigma_x\, e^{i\frac{\theta}{2}\sigma_z} = \sigma_x \cos\theta - \sigma_y \sin\theta$$
(and cyclic) — Bloch-sphere rotations, and the recipe for conjugating any Pauli string through a Clifford gate.

**Composing exponentials** ([[Baker-Campbell-Hausdorff]]): $e^A e^B = e^{A + B + \frac12[A,B] + \cdots}$; if $[A,B]$ is a c-number, exactly $e^{A+B} e^{[A,B]/2}$ — the phase-space geometric phase. $e^{A+B} \neq e^A e^B$ unless they commute ([[Trotter Product Formula]] for the workaround).

**Commutators with functions** ($[A,B]$ a c-number): $[A, f(B)] = [A,B]\, f'(B)$ — e.g. $[\hat x, f(\hat p)] = i\hbar f'(\hat p)$. General derivative rule: $\frac{d}{d\lambda} e^{X(\lambda)} \neq X' e^X$ unless $[X, X'] = 0$; the correct form is $\int_0^1 e^{sX} X' e^{(1-s)X} ds$ — the trap behind naive perturbation of exponentials.

**Picture changes as conjugation:** Heisenberg $A_H(t) = U^\dagger A U$; rotating frame / interaction picture $\tilde H = V H V^\dagger + i\hbar \dot V V^\dagger$ — the extra term appears because the frame itself moves ([[Rotating Frame Transformation]], [[Interaction Picture]]). Frame changes and gate conjugation are the same operation with different names.

> [!question]- Why is $V e^{X} V^{-1} = e^{VXV^{-1}}$ the identity to reach for, rather than transforming the exponential's series term by term?
> They are the same computation, but conjugating the generator converts an infinite sum of transformed powers into a single transformed operator exponentiated once — and the generator is usually simple (a Pauli, a quadratic) even when the exponential is not. Practical instances: a rotated MS interaction is the MS unitary with rotated spin operators; a Clifford conjugates a Pauli-string exponential to another Pauli-string exponential (the basis of stabilizer updates); a frame change moves a drive term's phase into the generator where it can be cancelled.

# Connections

- [[Spectral Theorem]] / [[Hermitian Matrices]] — the decomposition observables rest on
- [[Projectors]] — measurement probabilities as projections
- [[Commutators and Anticommutators]] — the algebra of the identities above
- [[Baker-Campbell-Hausdorff]] — composing exponentials in full
- [[Generators and the Exponential Map]] — unitaries from Hermitian generators
- [[Rotating Frame Transformation]] / [[Interaction Picture]] — conjugation as frame change
- [[Displacement Operator]] — the c-number case in daily use
- [[Simultaneous Diagonalization]] — commuting = jointly measurable

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, Ch. 1–2; Barnett & Radmore, *Methods in Theoretical Quantum Optics*, Ch. 3
