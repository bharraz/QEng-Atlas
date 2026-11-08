#quantum-info

**A quantum processor prepares a state with a short circuit whose gate angles $\theta$ are adjustable, and estimates the expectation value of an observable on that state from many repeated shots. A classical computer reads each estimate and changes $\theta$ to lower it; the loop stops at the best state that circuit can reach.** The variational quantum eigensolver (VQE) uses the loop to approximate ground states of molecules and spin models. The quantum approximate optimization algorithm (QAOA) uses it to find good bit strings for combinatorial problems. Neither has a proven speedup; both were designed for hardware without error correction, where only short circuits run reliably.

# Reference

**The loop:**
1. Prepare $|\psi(\theta)\rangle = U(\theta)\,|0\rangle^{\otimes n}$ with a parametrized circuit, the *ansatz*.
2. Estimate the cost $C(\theta)$ by measuring each Pauli term of $H$ in its own basis, many shots per term.
3. A classical optimizer proposes new angles; repeat until $C$ stops decreasing.

$$
C(\theta) = \langle\psi(\theta)|\,H\,|\psi(\theta)\rangle = \sum_k c_k\,\langle P_k\rangle_\theta \;\ge\; E_0
$$

- $\theta$ — the circuit's rotation angles (rad): what the optimizer adjusts
- $H$ — the observable being minimized: a Hamiltonian or an encoded cost function
- $P_k$ — Pauli strings such as $Z_1Z_2$ or $X_3$: measured one basis setting at a time
- $c_k$ — real coefficients of $H$ in the Pauli basis: weight each measured term
- $E_0$ — lowest eigenvalue of $H$: the floor $C$ cannot go below

The inequality is the variational principle ([[Rayleigh Quotient and Variational Principle]]). Every $\theta$ gives an upper bound on $E_0$, so a lower measured $C$ is always a better estimate. How close it can get depends on whether the ansatz can represent the ground state at all, and a good energy does not certify a good state.

**Picture:** gradient descent on an energy landscape you can only sample noisily, one expensive altitude reading at a time, restricted to the region of Hilbert space the circuit can reach.

**Ansatz families:**

| Ansatz | Built from | Strength | Weakness |
|---|---|---|---|
| hardware-efficient | layers of native single-qubit rotations and entangling gates | shallow on any device | no problem structure; prone to barren plateaus |
| unitary coupled cluster (UCC) | $e^{T - T^\dagger}$, with $T$ the electron excitation operators of quantum chemistry | physically motivated, systematically improvable | deep after Trotterization and the fermion-to-qubit mapping |
| Hamiltonian variational | alternating evolutions under groups of terms of $H$ itself | respects the symmetries of $H$ | depth grows with the number of noncommuting term groups |
| QAOA | alternating cost and mixer evolutions (below) | approaches adiabatic evolution as depth grows | needs many layers on hard instances |
| adaptive (ADAPT-VQE) | gates added one at a time from an operator pool, largest gradient first | compact circuits | many extra gradient measurements |

The more states a circuit family can reach (its expressibility), the flatter its average landscape tends to be, so expressibility and trainability pull against each other (barren plateaus, below).

## QAOA

The problem is a cost function on bit strings $z \in \{0,1\}^n$. The standard example is MaxCut: assign each vertex of a graph a bit, and count the edges whose two endpoints get different bits. Replacing each bit by the $Z$ eigenvalue of a qubit turns the count into a diagonal operator.

$$
H_C = \sum_{(i,j)\in E} \tfrac12\big(1 - Z_iZ_j\big), \qquad H_M = \sum_i X_i
$$

$$
|\gamma,\beta\rangle = e^{-i\beta_p H_M}\,e^{-i\gamma_p H_C}\cdots e^{-i\beta_1 H_M}\,e^{-i\gamma_1 H_C}\,|+\rangle^{\otimes n}
$$

- $H_C$ — cost operator, diagonal: eigenvalue = number of cut edges
- $H_M$ — mixer, a transverse field: moves amplitude between bit strings
- $E$ — the graph's edge set
- $\gamma_k, \beta_k$ — the $2p$ angles: what the optimizer adjusts
- $p$ — number of layers: sets circuit depth and reach
- $|+\rangle^{\otimes n}$ — uniform superposition: the top eigenstate of $H_M$

Each shot, measured in the computational basis, returns one candidate bit string. The optimizer maximizes the estimated $\langle H_C\rangle$, and the best string sampled is the answer.

**Behaviour with depth:**
- **Large $p$ is adiabatic evolution.** Each layer is one Trotter step of a sweep from $H_M$ to $H_C$. With many small angles following a slow schedule, QAOA tracks the top eigenstate from $|+\rangle^{\otimes n}$ to an optimal bit string, so as $p \to \infty$ it reaches the optimum ([[Adiabatic Ramps and Shortcuts]], [[Trotterization (Atlas)]]). At finite $p$ the angles are free, so the optimizer can beat a Trotterized ramp of the same depth.
- **Small $p$ is local.** After $p$ layers, $\langle Z_iZ_j\rangle$ depends only on the part of the graph within $p$ steps of edge $(i,j)$, its light cone. For $p = 1$ on 3-regular graphs the guaranteed approximation ratio is 0.6924, below the 0.878 that the classical Goemans–Williamson algorithm guarantees for any graph. Proven bounds show low-depth QAOA cannot reach good ratios on some graph families, because no qubit sees enough of the graph.
- **Good angles concentrate.** For typical instances of a graph family the optimal $(\gamma, \beta)$ are nearly the same, so angles optimized on small instances transfer to large ones and the outer loop becomes cheap.

**Platform fit.** A cost layer needs one two-qubit $ZZ$ rotation per edge. On nearest-neighbour hardware, dense graphs then require SWAP networks. On trapped ions the Mølmer–Sørensen interaction couples every pair and generates Ising couplings natively. A cost operator with the long-range couplings the ion chain provides can then be applied in one global step, and other graphs compile from addressed two-qubit gates without SWAPs ([[Molmer-Sorensen Gate]]). In Rydberg arrays the blockade forbids neighbouring excitations, which natively encodes the maximum-independent-set problem on unit-disk graphs ([[Rydberg Atoms and Blockade]]).

## Gradients from the hardware

**Parameter-shift rule.** For a gate $e^{-i\theta P/2}$ whose generator $P$ is a Pauli string, $C$ depends on $\theta$ as $a + b\cos\theta + c\sin\theta$, so two evaluations give the exact derivative:

$$
\frac{\partial C}{\partial \theta} = \tfrac12\Big[\,C\big(\theta + \tfrac{\pi}{2}\big) - C\big(\theta - \tfrac{\pi}{2}\big)\Big]
$$

- **It is exact, not a finite difference.** The shift is large, so the difference is not swamped by shot noise the way a small finite-difference step would be.
- **The cost is two circuits per parameter.** A gradient over $m$ parameters takes $2m$ cost estimates. Backpropagation is unavailable, because intermediate quantum states cannot be stored and reused ([[Gradient Descent and Backpropagation]]).
- **Shared parameters add.** A parameter that appears in several gates, such as QAOA's $\gamma$ in every edge rotation, gets the sum of the shift-rule derivatives of each gate.

## Shot budget

A Pauli expectation estimated from $N_k$ shots has variance $(1 - \langle P_k\rangle^2)/N_k$. Measuring the terms separately:

$$
\mathrm{Var}\big(\hat C\big) = \sum_k c_k^2\,\frac{1 - \langle P_k\rangle^2}{N_k}
$$

- $N_k$ — shots spent on term $k$: allocate in proportion to $\lvert c_k\rvert$
- $\hat C$ — the estimated cost: what the optimizer receives

Reaching precision $\epsilon$ takes up to about $(\sum_k \lvert c_k\rvert)^2/\epsilon^2$ shots for **one** evaluation of $C$; an optimization multiplies that by the number of iterations, and by $2m$ when gradients are measured. In chemistry the usual target is chemical accuracy, 1.6 mHartree (about 1 kcal/mol), and molecular Hamiltonians have $O(n^4)$ Pauli terms. This is the most common practical limit on VQE.

**Reducing it:** terms that commute qubit by qubit ($Z_1Z_2$ and $Z_1$) share one measurement setting. Larger commuting groups share a setting after a Clifford rotation ([[Clifford Group]], [[Pauli Group]]). Randomized-measurement estimators (classical shadows) estimate many terms from the same data ([[Quantum State Tomography (Atlas)]]).

## Barren plateaus

When a circuit is deep and unstructured enough to spread states nearly uniformly over Hilbert space, the cost gradient averages to zero over random $\theta$ and its variance falls exponentially with qubit number $n$:

$$
\mathrm{Var}_\theta\big[\partial_k C\big] \sim 2^{-n}
$$

Resolving a gradient of typical size $2^{-n/2}$ then takes about $2^n$ shots. The landscape is not trapped in a local minimum; it has no measurable slope at all.

| Cause | Why the landscape flattens | Mitigation |
|---|---|---|
| deep unstructured circuits | states spread over all of Hilbert space; any one direction carries exponentially little signal | shallow, structured ansätze |
| global cost (an observable on all qubits, such as fidelity with a target) | flat even for shallow circuits | local costs: sums of few-qubit terms |
| hardware noise | depolarizing noise at depth $L$ contracts the state toward maximally mixed, so gradients shrink exponentially in $L$ | shorter circuits; [[Quantum Error Mitigation]] |
| random initialization | the starting point lies on the plateau | start from identity blocks, a classical solution (Hartree–Fock), or transferred angles |

**Trainability and classical simulability are linked.** For deep circuits the gradient variance scales inversely with the dimension of the circuit's dynamical Lie algebra, the span of everything its generators produce under commutation ([[Dynamical Lie Algebras and Closure]]). Ansätze proven free of barren plateaus are mostly those confined to a polynomially small algebra or subspace, and that same confinement often makes them efficiently simulable classically.

## Optimizers

| Optimizer | Cost per step | Fits when |
|---|---|---|
| gradient descent or Adam, with parameter shift | $2m$ cost estimates | moderate $m$, smooth landscape |
| SPSA (simultaneous perturbation) | 2 cost estimates, any $m$ | many parameters, high shot noise |
| COBYLA, Nelder–Mead | gradient-free, a few estimates | few parameters; degrades with noise |
| quantum natural gradient | gradient plus the state's metric (quantum Fisher information) | badly scaled parametrizations |

See [[Optimization and Curve Fitting]] and [[Fisher Information and the Cramér-Rao Bound]].

**Noise and the loop.** Noise biases $C$ toward its value on the maximally mixed state. The loop absorbs coherent errors such as calibration over-rotations, because the optimizer re-tunes $\theta$ to compensate, but it cannot remove incoherent ones. Postselecting on conserved quantities (particle number, spin, parity) discards some error events cheaply.

## Where the claims stand

- No speedup is proven for VQE or QAOA. The variational principle guarantees an upper bound on energy, not accuracy.
- The meaningful comparison is with the best classical method on the same instance. For ground states that means tensor networks and coupled cluster ([[Tensor Networks and MPS]]). For optimization it means Goemans–Williamson, simulated annealing, and tuned heuristic solvers.
- For chemistry energies at scale, the long-term route is fault-tolerant phase estimation, whose cost scales as $1/\epsilon$ rather than $1/\epsilon^2$ ([[Quantum Phase Estimation]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| $C(\theta)$ against iteration number | convergence; flat from the very start suggests a barren plateau or a bad initial point |
| final $C$ against exact $E_0$, on instances small enough to diagonalize | combined ansatz and noise error; rerun the final $\theta$ on a noiseless simulator to separate them |
| gradient magnitudes at random $\theta$, for increasing $n$ | trainability: exponential decay with $n$ is a barren plateau |
| conserved quantities (particle number, $S_z$, parity) on the final state | noise-induced leakage out of the physical sector |
| distribution of sampled bit strings (QAOA) | approximation ratio of typical samples and of the best sample, which can differ widely |
| $C$ at amplified noise levels | how much of the error is hardware noise; the input to extrapolation |

> [!question]- A hardware paper runs depth-1 QAOA for MaxCut on a 40-qubit 3-regular graph and gets cut values matching theory. Does that show a quantum advantage?
> No. At depth 1 each edge's expectation value depends only on the graph within one step of that edge (at most 6 vertices), so the expected cut is a sum of small classical calculations; at any fixed depth on a bounded-degree graph the cost per edge is set by $p$ and the degree, not by $n$. The result validates the hardware's gates. An advantage claim needs light cones covering much of the graph and a comparison with the best classical solver (for MaxCut, Goemans–Williamson guarantees 0.878). Sampling the output can be classically hard even at depth 1, but that is not an optimization advantage.

# Connections

- [[Canonical Quantum Algorithms]] — the fault-tolerant algorithms these near-term methods sit beside
- [[Rayleigh Quotient and Variational Principle]] — why every measured $C$ bounds $E_0$ from above
- [[Adiabatic Ramps and Shortcuts]] — the sweep QAOA discretizes, and annealing as its analog version
- [[Trotterization (Atlas)]] — each QAOA layer as one product-formula step
- [[Spin Chains and Magnons]] — transverse-field Ising, the model behind cost and mixer
- [[Gradient Descent and Backpropagation]] — the classical optimizer, and why backpropagation is unavailable
- [[Optimization and Curve Fitting]] — gradient-free and stochastic optimizers
- [[Dynamical Lie Algebras and Closure]] — the algebra whose dimension sets gradient variance
- [[Quantum Error Mitigation]] — correcting the expectation values the loop reads
- [[Pauli Group]] — the measured terms and how they group into settings
- [[Molmer-Sorensen Gate]] — native all-to-all Ising couplings for cost layers on ions
- [[Rydberg Atoms and Blockade]] — blockade as a native optimization constraint
- [[Tensor Networks and MPS]] — the classical competitor for ground-state problems
- [[Pulse Shaping and Optimal Control]] — the same closed loop applied to control pulses
- [[Quantum Phase Estimation]] — the fault-tolerant route to energies

---
Source: A. Peruzzo et al., *Nat. Commun.* 5, 4213 (2014); E. Farhi, J. Goldstone & S. Gutmann, arXiv:1411.4028 (2014); M. Cerezo et al., "Variational quantum algorithms," *Nat. Rev. Phys.* 3, 625 (2021); J. R. McClean et al., *Nat. Commun.* 9, 4812 (2018); K. Mitarai et al., *Phys. Rev. A* 98, 032309 (2018)
