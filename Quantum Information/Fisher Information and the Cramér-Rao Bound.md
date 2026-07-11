#quantum-info #metrology #statistics

**Estimation theory in one line: the variance of any unbiased estimate of a parameter θ is bounded by the inverse of the Fisher information, and the quantum Fisher information is the best any measurement could ever do on a given state.** This is the framework the entire sensing literature is written in — every "sensitivity" formula is a Cramér-Rao bound in disguise.

# Reference

**Classical.** For data with likelihood $p(x|\theta)$, the Fisher information is the mean-square sensitivity of the log-likelihood:

$$F(\theta) = \left\langle \left(\partial_\theta \ln p(x|\theta)\right)^2 \right\rangle, \qquad \mathrm{Var}(\hat\theta) \geq \frac{1}{N F(\theta)} \quad (\text{Cramér–Rao, } N \text{ repetitions}).$$

Fisher information is *additive* over independent shots — hence every sensitivity improves as $1/\sqrt{N\,\text{(shots)}} \propto 1/\sqrt{T}$, the universal $\sqrt{\text{Hz}}$ in sensitivity units. [[Maximum Likelihood Estimation|MLE]] saturates the bound asymptotically, which is *why* MLE is the default estimator.

**Quantum.** A parameter is imprinted on a state, $\rho_\theta$; a measurement (POVM) converts it to a likelihood; the classical bound then applies. Maximizing over all possible measurements gives the **quantum Fisher information** $F_Q$ and the quantum Cramér-Rao bound:

$$\mathrm{Var}(\hat\theta) \geq \frac{1}{N F_Q}, \qquad F_Q = 4\left(\langle \partial_\theta\psi|\partial_\theta\psi\rangle - |\langle\psi|\partial_\theta\psi\rangle|^2\right) \;\;(\text{pure states}).$$

For the ubiquitous case — phase imprinted by a generator, $|\psi_\phi\rangle = e^{-i\phi \hat{G}}|\psi\rangle$:

$$F_Q = 4\,\mathrm{Var}(\hat{G}).$$

**Read that equation twice; it is the design principle of all quantum sensing:** sensitivity to a phase is the *variance of the generator* in your probe state. A state spread widely across the eigenvalues of $\hat G$ rotates "faster" per unit φ. Everything in metrology — squeezing, entanglement, Fock states, Schrödinger cats — is a scheme to enlarge $\mathrm{Var}(\hat G)$ subject to practical constraints.

**Worked instances:**

- **Ramsey on one qubit** ($\hat G = \sigma_z/2$, superposition state): $\mathrm{Var}(G) = 1/4$, $F_Q = 1$ → $\Delta\phi = 1/\sqrt{N}$. This is the [[Binomial Errors in State Detection|projection-noise]] limit of [[Ramsey Interferometry]], now derived from first principles.
- **$N$ qubits, unentangled**: variances add, $F_Q = N$ → $\Delta\phi = 1/\sqrt{N}$ — the **standard quantum limit (SQL)**.
- **GHZ state** $(|00\cdots0\rangle + |11\cdots1\rangle)/\sqrt{2}$: the two branches differ by $N$ quanta of the generator, $\mathrm{Var}(G) = N^2/4$, $F_Q = N^2$ → $\Delta\phi = 1/N$ — the **Heisenberg limit**. Same $N$ atoms, quadratically better, purely from state structure. (The catch lives on the [[Standard Quantum Limit and Spin Squeezing|next page]].)
- **Coherent light, phase measurement**: $F_Q = 4\bar n$ → $\Delta\phi = 1/2\sqrt{\bar n}$ — photon shot noise, the interferometer SQL.

**Two practical corollaries:**

- *Which measurement saturates $F_Q$?* Generally the one that projects onto the eigenbasis of the "symmetric logarithmic derivative" — but for Ramsey-type experiments the ordinary population measurement after the second π/2 pulse already saturates it at the fringe's steepest point. Operating at mid-fringe isn't folklore; it's where $\partial_\theta p$ is maximal.
- *Slope-over-noise is the same bound.* The lab formula $\Delta\theta = \sigma_{\text{signal}}/|\partial S/\partial\theta|$ is the Cramér-Rao bound for a Gaussian readout — signal slope² / variance *is* the Fisher information of that measurement. When you optimize a lock-in or an error signal's slope, you are maximizing F.

> [!question]- Your Ramsey fringe contrast is C < 1 (decoherence, readout error). How does the achievable sensitivity actually degrade?
> Contrast enters the Fisher information *quadratically* while shot noise is unchanged: $F = C^2 \sin^2\phi / (1 - C^2\cos^2\phi) \leq C^2$ per shot, so $\Delta\phi \geq 1/(C\sqrt{N})$. A contrast of 0.5 costs you 4× in averaging time — which is why fighting for readout fidelity and coherence usually beats adding shots, and why sensitivity formulas carry that C (cf. the NV sensitivity expression in [[NV Centers (atlas)]]).

# Connections

- [[Standard Quantum Limit and Spin Squeezing]] — SQL vs Heisenberg made operational: squeezing, GHZ fragility, decoherence limits
- [[Maximum Likelihood Estimation]] — the estimator that saturates Cramér-Rao
- [[Ramsey Interferometry]] — the canonical phase-estimation protocol
- [[Binomial Errors in State Detection]] — projection noise = the SQL seen in raw counts
- [[Allan Variance]] — how sensitivity per √Hz integrates into stability vs averaging time
- [[Shot Noise]] — the photonic face of the same bound

---
Source: Braunstein & Caves, *Phys. Rev. Lett.* 72, 3439 (1994); Degen, Reinhard & Cappellaro, "Quantum sensing," *Rev. Mod. Phys.* 89, 035002 (2017), Sec. IV–V
