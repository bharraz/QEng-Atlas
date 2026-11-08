#quantum #AMO

**When two states are each coupled to a third state that lies far off resonance, the third state is barely populated, yet the two behave as if coupled directly: amplitude passes through the intermediate state virtually, at a rate set by the product of the two couplings divided by the detuning.** The same calculation applied to a single state gives its energy shift. Raman transitions, the spin–spin interaction of the far-detuned Mølmer–Sørensen gate, dispersive shifts in cavity QED, and superexchange in magnets are all this one calculation.

# Reference

**The setup.** Split the states into a low-energy set $P$ that you care about and a set $Q$ of intermediate states, separated by a gap much larger than the couplings $V$ between them. In block form ([[Block Matrices]]):

$$
H = \begin{pmatrix} H_P & V \\ V^\dagger & H_Q \end{pmatrix}, \qquad \lvert V\rvert \ll \lvert E_P - E_Q\rvert
$$

**Second-order effective Hamiltonian** on $P$:

$$
(H_\text{eff})_{mn} = (H_P)_{mn} + \frac12\sum_{k \in Q} H_{mk}H_{kn}\left(\frac{1}{E_m - E_k} + \frac{1}{E_n - E_k}\right)
$$

- $m, n$ — states in the low-energy set $P$
- $k$ — an intermediate state in $Q$, never substantially populated
- $H_{mk}, H_{kn}$ — couplings into and out of $k$ (J)
- $E_m - E_k$ — energy denominator (J): how far $k$ is off resonance

When $m = n$ the formula is the second-order energy shift of [[Time-Independent Perturbation Theory]]; when $m \neq n$ it is a coupling that $H$ does not contain directly ([[Reading Matrices and Hamiltonians]]). Each route through an intermediate state contributes separately, with its own sign, so routes can add or cancel.

**Adiabatic elimination, the same result from the equations of motion.** In a Λ system, two ground states $|1\rangle, |2\rangle$ couple to an excited state $|e\rangle$ with Rabi frequencies $\Omega_1, \Omega_2$, both detuned by $\Delta$. The excited amplitude responds at frequency $\Delta$, much faster than anything in the ground states, so it settles to follow them: set $\dot c_e = 0$, solve for $c_e$, and substitute back. The result:

$$
\Omega_\text{eff} = \frac{\Omega_1\Omega_2}{2\Delta}, \qquad \delta_i = \frac{\Omega_i^2}{4\Delta}, \qquad P_e \approx \frac{\lvert\Omega_1 c_1 + \Omega_2 c_2\rvert^2}{4\Delta^2}
$$

- $\Omega_\text{eff}$ — effective Rabi frequency between $\lvert 1\rangle$ and $\lvert 2\rangle$ (rad/s)
- $\delta_i$ — light shift of ground state $i$ (rad/s)
- $P_e$ — excited-state population (dimensionless): sets scattering
- $\Delta$ — detuning of both beams from $\lvert e\rangle$ (rad/s)

Signs depend on the sign convention for $\Delta$ ([[Raman Transitions]], [[Conventions and Factor-of-Two Traps]]).

**Picture:** the intermediate state is a relay that holds each message for only about $1/\Delta$, so it never fills up, yet messages still pass between the two ends at a rate set by both links and the holding time.

**Schrieffer–Wolff transformation.** The systematic version: a unitary $e^{S}$, close to the identity, rotates the basis so that the couplings between $P$ and $Q$ vanish to first order. What remains inside $P$ at second order is the formula above. Higher orders add corrections smaller by further factors of $V/\Delta$. The effective states are the slightly rotated, dressed ones; a measurement in the bare basis sees them with an admixture of order $(V/\Delta)^2$ from $Q$.

**Instances:**

| System | Low-energy states | Intermediate states | Effective term |
|---|---|---|---|
| Raman transition | two ground hyperfine or Zeeman states | excited state, detuned $\Delta$ | coupling $\Omega_1\Omega_2/2\Delta$ plus light shifts $\Omega_i^2/4\Delta$ ([[Raman Transitions]]) |
| far-detuned Mølmer–Sørensen interaction | spins of $N$ ions | motional modes, detuned $\delta_k$ | spin–spin coupling $J_{ij} \propto \Omega_i\Omega_j\sum_k \eta_{ik}\eta_{jk}/\delta_k$ ([[Molmer-Sorensen Gate]]) |
| dispersive cavity or circuit QED | qubit with any photon number | qubit–photon exchange, detuned $\Delta$ | a photon-number-dependent qubit frequency, $2\chi$ per photon with $\chi = g^2/\Delta$ ([[Circuit QED]]) |
| two qubits on a common bus | the two qubits | a detuned cavity, spin, or motional mode | exchange coupling $g_1g_2/\Delta$ |
| superexchange, Hubbard model with $U \gg t$ | spin configurations, one particle per site | doubly occupied sites, energy $U$ | Heisenberg coupling $J = 4t^2/U$ ([[Exchange Interactions]]) |
| Rydberg dressing | ground-state atoms | Rydberg state with blockade | fourth order: a soft-core interaction $\propto \Omega^4/\Delta^3$ ([[Rydberg Atoms and Blockade]]) |

**Where elimination fails:**
- **Detuning not large enough.** Corrections grow as $(\Omega/\Delta)^2$, and near resonance the intermediate state must be kept explicitly ([[EIT and STIRAP]]).
- **The intermediate state decays.** Its population $(\Omega/2\Delta)^2$ scatters at $\Gamma$, so the scattering rate falls as $1/\Delta^2$ while the effective coupling falls only as $1/\Delta$. Larger detuning at higher intensity improves the ratio of coherent coupling to scattering.
- **Several intermediate states.** Their contributions add with signs. Raman coupling between hyperfine ground states falls off once $\Delta$ exceeds the excited-state fine-structure splitting, because the routes through the two fine-structure levels cancel.
- **Couplings that change quickly.** The derivation assumes the couplings vary slowly compared with $1/\Delta$; abrupt switching populates $Q$ ([[Adiabatic Theorem]]).
- **Residual entanglement with the eliminated system.** In spin–motion gates the eliminated mode is not left exactly untouched; the leftover spin–motion entanglement is of order $(\eta\Omega/\delta)^2$ unless loops are closed ([[Magnus Expansion]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| effective Rabi rate against detuning | a $1/\Delta$ dependence confirms a two-photon process; deviations show other intermediate states |
| decoherence or scattering against detuning at fixed effective rate | the trade between speed and intermediate-state population |
| shift of each state alone, by Ramsey | the diagonal second-order terms, which must be compensated or matched |
| interaction strength against distance or mode detuning | which intermediate states carry the coupling |

> [!question]- In a Raman transition with $\Omega_1 = \Omega_2 = \Omega$, you double the detuning and double both Rabi frequencies. What happens to the effective coupling, the light shifts, and the spontaneous scattering?
> $\Omega_\text{eff} = \Omega^2/2\Delta$ and $\delta = \Omega^2/4\Delta$ both double, since the numerator grows by 4 and the denominator by 2. Scattering goes as $\Gamma\Omega^2/\Delta^2$, which is unchanged. The ratio of coherent coupling to scattering therefore doubles: the reason Raman beams are detuned far and driven hard, until laser power or the fine-structure cancellation runs out.

# Connections

- [[Reading Matrices and Hamiltonians]] — why a zero entry still permits a route through an intermediate state
- [[Block Matrices]] — the Schur complement $A - BD^{-1}C$, the exact form of this elimination
- [[Time-Independent Perturbation Theory]] — the diagonal case: second-order shifts
- [[Raman Transitions]] — the Λ system worked through
- [[Molmer-Sorensen Gate]] — spin–spin couplings mediated by motional modes
- [[Circuit QED]] — dispersive shifts from a detuned resonator
- [[Exchange Interactions]] — superexchange as virtual hopping
- [[Stark Effect and Light Shifts]] — the single-state shift from an off-resonant level
- [[Rydberg Atoms and Blockade]] — dressing at fourth order

---
Source: D. F. V. James & J. Jerke, "Effective Hamiltonian theory and its applications in quantum information," *Can. J. Phys.* 85, 625 (2007); S. Bravyi, D. P. DiVincenzo & D. Loss, "Schrieffer–Wolff transformation for quantum many-body systems," *Ann. Phys.* 326, 2793 (2011); E. Brion, L. H. Pedersen & K. Mølmer, "Adiabatic elimination in a lambda system," *J. Phys. A* 40, 1033 (2007)
