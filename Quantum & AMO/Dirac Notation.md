#quantum

**A quantum state is a vector; Dirac's notation writes it as a ket $|\psi\rangle$ — a column of amplitudes once a basis is chosen — and its conjugate transpose as a bra $\langle\psi|$, a row.** Placing a bra and a ket side by side multiplies them, so the shape of the bracket tells you what kind of object you have: $\langle\phi|\psi\rangle$ closes to a number, $|\psi\rangle\langle\phi|$ stays open as an operator, and $\langle m|A|n\rangle$ is one entry of a matrix.

# Reference

**Object types at a glance:**

| Expression | Type | In a basis |
|---|---|---|
| $\lvert\psi\rangle$ | ket: a state vector | column of amplitudes |
| $\langle\psi\rvert$ | bra: the dual vector | row of conjugated amplitudes |
| $\langle\phi\vert\psi\rangle$ | complex number | row × column |
| $\lvert\psi\rangle\langle\phi\rvert$ | operator | column × row: a matrix |
| $\langle m\vert A\vert n\rangle$ | number: a matrix element | the entry $A_{mn}$ |
| $A\lvert\psi\rangle$ | ket | matrix × column |
| $\lvert a\rangle\lvert b\rangle = \lvert a\rangle\otimes\lvert b\rangle$ | ket of a composite system | Kronecker product ([[Tensor Product]]) |

**Conjugation rules:**

$$
\langle\phi|\psi\rangle = \langle\psi|\phi\rangle^*, \qquad \langle\phi|A|\psi\rangle = \left(\langle\psi|A^\dagger|\phi\rangle\right)^*
$$

**Picture:** a bra is a question and a ket is a state — $\langle\phi|\psi\rangle$ is the answer, the amplitude of $\phi$ in $\psi$ — and $|a\rangle\langle b|$ is a machine that asks question $b$ and writes the answer along $a$.

**Resolution of identity.** For any orthonormal basis $\{|n\rangle\}$:

$$
\mathbb{1} = \sum_n |n\rangle\langle n| \quad\text{or}\quad \mathbb{1} = \int dx\, |x\rangle\langle x|
$$

Inserting it changes basis, expands a state, or turns an abstract expression into components: $\langle\phi|\psi\rangle = \sum_n \langle\phi|n\rangle\langle n|\psi\rangle$. It is the most frequently used identity in the notation.

**Wavefunctions are components.** $\psi(x) = \langle x|\psi\rangle$ is the state $|\psi\rangle$ expressed in the position basis. The momentum-space wavefunction is $\langle p|\psi\rangle$; the two are Fourier transforms of each other through

$$
\langle x|p\rangle = \frac{e^{ipx/\hbar}}{\sqrt{2\pi\hbar}}
$$

- $\lvert x\rangle$, $\lvert p\rangle$ — position and momentum eigenkets
- $\hbar$ — reduced Planck constant (J·s)

**Outer products build operators.** $|a\rangle\langle b|$ maps $|b\rangle \to |a\rangle$, and any operator is a sum of them:

$$
A = \sum_{mn} A_{mn}\,|m\rangle\langle n|, \qquad A_{mn} = \langle m|A|n\rangle = \langle \text{output}|A|\text{input}\rangle
$$

- $\lvert n\rangle$ — input basis state: labels the column
- $\lvert m\rangle$ — output basis state: labels the row
- $A_{mn}$ — amplitude of output $m$ per unit of input $n$

From this reading:
- The off-diagonal element $A_{mn}$ is what couples states $m$ and $n$.
- The diagonal element $A_{mm}$ is the energy of state $m$ when $A$ is a Hamiltonian, and its population when $A$ is a density matrix ([[Reading Matrices and Hamiltonians]], [[Density Matrix]]).

**Continuum kets.** Kets such as $|x\rangle$ are not normalizable — $\langle x|x'\rangle = \delta(x - x')$ — so they are basis tools, not physical states ([[Dirac Delta]]).

> [!question]- What does inserting $\mathbb{1}=\sum_n |n\rangle\langle n|$ between two operators do?
> It performs matrix multiplication: $\langle m|AB|k\rangle = \sum_n \langle m|A|n\rangle\langle n|B|k\rangle = \sum_n A_{mn}B_{nk}$, a sum over every intermediate state $n$. The bra-ket expression and the matrix product are the same calculation.

# Connections

- [[Inner Products and Orthogonality]] — the linear-algebra substrate; brackets are inner products
- [[Postulates of Quantum Mechanics]] — what the notation is for
- [[Projectors]] — $|v\rangle\langle v|$ as the building block of measurements and spectral decompositions
- [[Fourier Transform]] — position and momentum representations of the same ket
- [[Reading Matrices and Hamiltonians]] — what each entry $\langle m|A|n\rangle$ does
- [[Tensor Product]] — kets of several systems

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §1.2–1.7
