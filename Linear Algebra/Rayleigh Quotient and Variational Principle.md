#linear-algebra #math

**The expectation value of a Hermitian operator in any state is trapped between its extreme eigenvalues — so minimizing $\langle x|A|x\rangle$ over normalized states hunts down the ground state.** Any trial state gives an upper bound; you can only overestimate the ground energy, never undershoot it.

# Reference

$$
R(x) = \frac{\langle x|A|x\rangle}{\langle x|x\rangle}, \qquad \lambda_{\min} \le R(x) \le \lambda_{\max}
$$
with equality iff $x$ is the corresponding eigenvector. Proof in one move: expand $x$ in the eigenbasis, $R$ is a convex combination of eigenvalues weighted by $|c_i|^2$.

**Stationarity ⇔ eigenvectors:** $\nabla R = 0$ exactly at eigenvectors, with $R = \lambda$ there. Eigenvalue problems *are* constrained optimization — this is why "diagonalize" and "extremize" keep being the same task.

**Error is second order — the reason variational methods work at all:** a trial state wrong by $O(\epsilon)$ gives an energy wrong by only $O(\epsilon^2)$. A sloppy wavefunction still yields a decent energy (the converse gotcha: a good variational *energy* does not certify a good *state*, and other observables can be badly off).

**Beyond the ground state:** min-max (Courant-Fischer) gives $\lambda_k$ by minimizing over $k$-dimensional subspaces; practically, get excited states by constraining trial states orthogonal to the lower ones, or diagonalize $A$ in a small trial subspace (Rayleigh-Ritz — the finite basis truncations you use daily are exactly this).

**Where you meet it:** variational ground states (Hartree-Fock, matrix product states, the helium-atom trial-wavefunction classic), VQE energy landscapes, and power/Lanczos iterations using $R(x)$ as the running eigenvalue estimate.

> [!question]- Why is the variational energy error quadratic in the state error?
> Write $|x\rangle = |0\rangle + \epsilon|\perp\rangle$. The cross terms $\langle 0|A|\perp\rangle$ vanish because $|0\rangle$ is an eigenvector (stationary point of $R$), so the first surviving correction is the $|\epsilon|^2\langle\perp|A|\perp\rangle$ term.

# Connections

- [[Hermitian Matrices]] — real spectrum and orthogonal eigenbasis are what make the bound work
- [[Eigenvalues and Eigenvectors]] — the variational characterization is often the most useful definition of them
- [[Canonical Quantum Algorithms]] — VQE is Rayleigh-quotient minimization with a quantum computer evaluating $\langle x|H|x\rangle$
- [[Quantum Harmonic Oscillator]] — standard playground: any trial Gaussian bounds $\hbar\omega/2$ from above

---
Source: Horn & Johnson, *Matrix Analysis*, §4.2 (Courant-Fischer); Griffiths, *Intro to QM*, Ch. 8 for the physics side
