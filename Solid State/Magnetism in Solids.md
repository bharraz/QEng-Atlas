#solid-state

**Magnetism in a solid comes from electron spins and the exchange coupling between them, not from classical magnetic forces; the sign and size of that exchange decides whether a material is paramagnetic, ferromagnetic, or antiferromagnetic.** It is where many-body spin physics is spoken, and the spin algebra is the same one qubits use.

# Reference

**Response types** (susceptibility $\chi = M/H$, dimensionless SI):
- **Diamagnetism** — induced currents oppose the applied field; weak ($\chi \sim -10^{-5}$), universal, temperature-independent.
- **Paramagnetism** — unpaired local moments align with the field. Quantitatively, a spin-$J$ moment magnetizes along the **Brillouin function** $M = n g_J \mu_B J\, B_J(g_J \mu_B J B / k_B T)$; in the common regime $\mu_B B \ll k_B T$ this linearizes to the **Curie law**
$$\chi = \frac{C}{T}, \qquad C = \frac{n\,\mu_0\, g_J^2 \mu_B^2\, J(J+1)}{3k_B},$$
so a $1/T$ fit yields the effective moment $\mu_{\text{eff}} = g_J\sqrt{J(J+1)}\,\mu_B$ — the standard way to count unpaired spins in a sample. (Conduction electrons instead give the small, $T$-independent **Pauli paramagnetism** $\chi_P = \mu_0 \mu_B^2 g(E_F)$: only the $k_BT/E_F$ sliver at the Fermi surface is free to flip, cancelling the Curie $1/T$.)
- **Ordered magnetism** — spontaneous alignment below a critical temperature, no field needed.

**Exchange** is the engine of ordering: Coulomb repulsion plus Pauli exclusion makes the electrostatic energy depend on relative spin orientation, producing an effective spin–spin coupling captured by the **Heisenberg model**

$$H = -\sum_{ij} J_{ij}\,\mathbf{S}_i\cdot\mathbf{S}_j.$$

$J>0$ favors parallel spins (**ferromagnet**); $J<0$ favors alternating spins (**antiferromagnet**). Exchange is large because it is electrostatic: $J/k_B \sim 10\text{–}10^3$ K, versus millikelvin for dipole–dipole.

**Mean-field treatment** — replace neighbors by their average, $H_i \approx -g\mu_B \mathbf{S}_i \cdot (\mathbf{B} + \lambda \mathbf{M})$: order onsets at

$$T_C = \frac{z J S(S+1)}{3 k_B}$$

($z$ = coordination number), and above $T_C$ the susceptibility follows **Curie–Weiss**,

$$\chi = \frac{C}{T - \theta},$$

with $\theta > 0$ signalling ferromagnetic and $\theta < 0$ antiferromagnetic correlations — the intercept of a $1/\chi$ vs $T$ plot diagnoses the sign of exchange before any order sets in. (Mean field overestimates $T_C$ and fails within the critical region; fluctuations kill order entirely in low dimensions — Mermin–Wagner.)

Below $T_C$ ($T_N$ for antiferromagnets) a ferromagnet breaks into **domains** and shows hysteresis. Spin waves — the low-energy excitations of an ordered magnet — are quantized as bosonic **magnons**, with dispersion $\omega \propto k^2$ (ferromagnet) giving a magnon heat capacity $\propto T^{3/2}$.

**Lab relevance beyond magnetic materials**: paramagnetic impurities and surface spins are dominant magnetic-noise sources — surface electron spins ($g \approx 2$: $28$ GHz/T) are a chief decoherence channel for shallow NV centers and a flux-noise source in superconducting loops; their $1/T$ polarization is why some noise freezes out at millikelvin.

> [!question]- Why is ferromagnetism a quantum effect with no classical explanation?
> Magnetic dipole–dipole interaction between electron moments is far too weak — it would order spins only in the millikelvin range. Real magnets order at hundreds of kelvin because the alignment energy is *exchange*: an electrostatic energy difference between symmetric and antisymmetric spatial wavefunctions, forced by Pauli exclusion. Magnetism is Coulomb interaction plus quantum statistics wearing a magnetic mask.

# Connections

- [[Spin-1-2]] — the elementary moment and its operators
- [[Angular Momentum in QM]] — the spin algebra the Heisenberg model is built from
- [[Zeeman Effect (Atlas)]] — how an external field couples to and splits the spins
- [[Pauli Matrices]] — the same $\mathbf{S}_i\cdot\mathbf{S}_j$ coupling appears in qubit Hamiltonians
- [[Symmetry in Quantum Mechanics]] — ordering spontaneously breaks spin-rotation symmetry

---
Source: Ashcroft & Mermin, *Solid State Physics*, Ch. 31–33; Blundell, *Magnetism in Condensed Matter*, Ch. 3–5
