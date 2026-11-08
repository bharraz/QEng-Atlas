#quantum-info

**Two separated parties, Alice and Bob, share a pair of particles; each chooses one of two measurement settings at random and records an outcome $\pm1$. If each outcome is fixed by variables shared in advance and cannot depend on the other side's setting, one combination of their correlations can never exceed 2 — yet measurements on an entangled pair reach $2\sqrt2$.** That gap is Bell nonlocality. It rules out every local hidden-variable account of the correlations, and a violation can be certified from the recorded statistics alone, without trusting the devices that produced them.

# Reference

**The CHSH inequality.** With settings $a, a'$ for Alice and $b, b'$ for Bob, and $E(a,b)$ the average of the product of their outcomes:

$$
S = E(a,b) + E(a,b') + E(a',b) - E(a',b'), \qquad \lvert S\rvert \le 2 \ \text{(local)}, \qquad \lvert S\rvert \le 2\sqrt2 \ \text{(quantum)}
$$

- $a, a'$ — Alice's two measurement settings
- $b, b'$ — Bob's two measurement settings
- $E(a,b)$ — correlation: average of the product of outcomes, between $-1$ and $1$
- $S$ — the CHSH combination

The local bound in one line: if every outcome $A, A', B, B'$ is a predetermined $\pm1$, then $A(B + B') + A'(B - B')$ is $\pm 2$, because one bracket is zero and the other is $\pm2$; averaging over the shared variables cannot exceed 2. The quantum bound $2\sqrt2$ is Tsirelson's. Correlations limited only by no-signalling (a "PR box") could reach 4.

**Picture:** two sealed envelopes prepared in advance can make answers agree, but they cannot make the agreement depend on which questions both parties later choose to ask in the way an entangled pair does.

**Reaching $2\sqrt2$.** For $|\Phi^+\rangle = (|00\rangle + |11\rangle)/\sqrt2$, measuring $\cos\theta\, Z + \sin\theta\, X$ on each side gives $E = \cos(\theta_A - \theta_B)$. With $\theta_a = 0$, $\theta_{a'} = \pi/2$, $\theta_b = \pi/4$, $\theta_{b'} = -\pi/4$, each term contributes $1/\sqrt2$ in magnitude, and $S = 2\sqrt2$ ([[Bell States]]).

**For any two-qubit state** the maximum over settings is known (the Horodecki criterion):

$$
S_\text{max} = 2\sqrt{t_1^2 + t_2^2}
$$

- $T_{ij} = \mathrm{Tr}\big(\rho\,\sigma_i\otimes\sigma_j\big)$ — the state's correlation matrix
- $t_1, t_2$ — the two largest singular values of $T$

**Assumptions behind the local bound, and the loopholes that test them:**

| Assumption | Meaning | Loophole if not enforced | How experiments close it |
|---|---|---|---|
| locality | one side's setting cannot influence the other side's outcome | locality loophole | choose settings and record outcomes at spacelike separation |
| measurement independence | settings are uncorrelated with the shared variables | freedom-of-choice loophole | fast random-number generators; settings from distant astronomical sources |
| fair sampling | the detected events represent all events | detection loophole | detection efficiency above a threshold: about 82.8% for a maximally entangled state, down to 2/3 with less entangled states (Eberhard) |
| outcomes defined per trial | each run gives a definite $\pm1$ | memory and coincidence-time loopholes | predefined time windows; statistics that tolerate memory |

Experiments closing the locality and detection loopholes simultaneously were reported in 2015 with NV-centre electron spins and with photons ([[Remote Entanglement and Quantum Networks]]).

**Entanglement, steering, and nonlocality are different.** Every nonlocal state is entangled, but not the reverse. A Werner state $\rho = p\,|\Psi^-\rangle\langle\Psi^-| + (1-p)\,\mathbb{1}/4$:
- is entangled for $p > 1/3$;
- violates CHSH for $p > 1/\sqrt2$;
- admits a local hidden-variable model for all projective measurements when $p \le 1/2$.

Steering, in which one party's measurement prepares the other's state in a way no local model explains, sits between the two ([[Entanglement Measures]]).

**GHZ: a contradiction without an inequality.** For three qubits in $(|000\rangle + |111\rangle)/\sqrt2$, quantum mechanics predicts with certainty $XXX = +1$ and $XYY = YXY = YYX = -1$. Predetermined values would make the product of the last three equal to $x_1x_2x_3$, since each $y_i$ appears twice; that product is $-1$, contradicting $XXX = +1$ in a single deterministic statement. The $N$-qubit Mermin inequalities extend this, with a quantum-to-local ratio that grows exponentially in $N$.

**Contextuality** is the broader property: outcomes cannot be assigned independently of which compatible measurements accompany them (Kochen–Specker). Nonlocality is contextuality enforced by spatial separation, and contextuality is also linked to magic states, the resource needed for universal fault-tolerant computation ([[Magic and Nonstabilizerness]]).

**Uses:**
- **Device-independent protocols.** Key distribution and randomness generation whose security follows from the observed $S$ alone, with no model of the devices.
- **Self-testing.** A violation close to $2\sqrt2$ certifies that the devices share a state close to a Bell pair and perform near-ideal measurements, up to local changes of basis.
- **Entanglement certification.** $S > 2$ proves entanglement without trusting the measurement calibration, a standard check on remote-entanglement links.

**No signalling.** Nonlocal correlations cannot send messages: Bob's outcome statistics do not depend on Alice's setting, and the correlations appear only when the records are compared ([[No-Cloning Theorem]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| $S$ above 2 with its statistical uncertainty | correlations no local model reproduces, given the assumptions enforced |
| $S$ compared with $2\sqrt2$ | how close the state and measurements are to ideal; $S = 2\sqrt2\,p$ for a Werner state |
| detection efficiency and coincidence window | whether the fair-sampling assumption is needed |
| timing of setting choice and detection against light travel time | whether locality was enforced |
| Mermin or GHZ parities for $N$ qubits | multipartite nonlocality, and a check on GHZ-state coherence |

> [!question]- A photon experiment reports $S = 2.4 \pm 0.1$ with 10% overall detection efficiency, counting only coincidences. Has it ruled out local hidden variables?
> Not without the fair-sampling assumption. With most events undetected, a local model can reproduce $S > 2$ among the detected pairs by correlating detection with the settings. The result still shows entanglement if the detectors are assumed to behave as modelled, but a device-independent conclusion needs overall efficiency above the threshold — about 82.8% for a maximally entangled state.

# Connections

- [[Bell States]] — the states that reach Tsirelson's bound
- [[Entanglement Measures]] — entanglement as a quantity, distinct from nonlocality
- [[Remote Entanglement and Quantum Networks]] — loophole-free tests and device-independent links
- [[Quantum Teleportation]] — another use of shared Bell pairs, with classical communication
- [[No-Cloning Theorem]] — why nonlocal correlations still cannot signal
- [[Magic and Nonstabilizerness]] — contextuality as a computational resource
- [[Projective Measurement and POVMs]] — the measurements whose statistics are being tested
- [[Density Matrix]] — mixed states, where entanglement and nonlocality separate

---
Source: J. F. Clauser, M. A. Horne, A. Shimony & R. A. Holt, *Phys. Rev. Lett.* 23, 880 (1969); N. Brunner, D. Cavalcanti, S. Pironio, V. Scarani & S. Wehner, "Bell nonlocality," *Rev. Mod. Phys.* 86, 419 (2014); R. F. Werner, *Phys. Rev. A* 40, 4277 (1989); B. Hensen et al., *Nature* 526, 682 (2015)
