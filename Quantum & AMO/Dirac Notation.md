#quantum

**Kets are column vectors, bras are their conjugate-transpose row vectors, and the notation is built so that anything that looks like it should contract, does.** $\langle\phi|\psi\rangle$ is a number, $|\psi\rangle\langle\phi|$ is an operator — the bracket shape tells you the object type at a glance.

# Reference

$$
\langle\phi|\psi\rangle = \langle\psi|\phi\rangle^*, \qquad \langle\phi|A|\psi\rangle = \left(\langle\psi|A^\dagger|\phi\rangle\right)^*
$$

**Resolution of identity** — the workhorse move. For any orthonormal basis $\{|n\rangle\}$:
$$
\mathbb{1} = \sum_n |n\rangle\langle n| \quad\text{or}\quad \mathbb{1} = \int dx\, |x\rangle\langle x|
$$
Insert it anywhere to change basis, expand a state, or turn an abstract expression into components: $\langle\phi|\psi\rangle = \sum_n \langle\phi|n\rangle\langle n|\psi\rangle$.

**Wavefunctions are components:** $\psi(x) = \langle x|\psi\rangle$ — the state $|\psi\rangle$ expressed in the position basis, nothing more. Momentum-space wavefunction is $\langle p|\psi\rangle$; the two are Fourier transforms of each other via $\langle x|p\rangle = e^{ipx/\hbar}/\sqrt{2\pi\hbar}$.

**Outer products build operators:** $|a\rangle\langle b|$ maps $|b\rangle \to |a\rangle$; any operator is $A = \sum_{mn} A_{mn}|m\rangle\langle n|$ with matrix elements $A_{mn} = \langle m|A|n\rangle$.

Gotcha: continuum kets like $|x\rangle$ aren't normalizable — $\langle x|x'\rangle = \delta(x-x')$ — so they're basis tools, not physical states.

> [!question]- What does inserting $\mathbb{1}=\sum_n |n\rangle\langle n|$ between operators actually do?
> Matrix multiplication: $\langle m|AB|k\rangle = \sum_n \langle m|A|n\rangle\langle n|B|k\rangle = \sum_n A_{mn}B_{nk}$. The abstract notation and matrix algebra are the same thing.

# Connections

- [[Inner Products and Orthogonality]] — the linear-algebra substrate; brackets are inner products
- [[Postulates of Quantum Mechanics]] — what the notation is for
- [[Projectors]] — $|v\rangle\langle v|$ as the atomic building block of measurements and spectral decompositions
- [[Fourier Transform]] — position ↔ momentum representations of the same ket

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §1.2–1.7
