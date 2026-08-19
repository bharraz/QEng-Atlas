#solid-state #labwork

**Amorphous surfaces and interfaces host two-level fluctuators that absorb energy resonantly and shift frequencies slowly — the loss mechanism that limits superconducting qubits, microwave resonators, and ion-trap surface heating alike.**

# Reference

A **two-level system (TLS)** is a local degree of freedom in a disordered solid with two nearly degenerate configurations separated by a tunnel barrier — an atom or small group with two available sites, or a dangling bond reorienting. In an amorphous oxide there are many, with a **broad distribution of splittings and couplings**, which is the defining feature:

$$P(E, \lambda) \approx \text{const}$$

Roughly uniform in energy means: whatever your operating frequency, some TLS is resonant with it.

Each TLS carries an electric dipole, so it couples to the local electric field:
$$H = \frac{1}{2}\left(\epsilon\,\sigma_z + \Delta_0\,\sigma_x\right) + \mathbf{d}\cdot\mathbf{E}\,\sigma_z$$

with $\epsilon$ the asymmetry between the two wells, $\Delta_0$ the tunnel splitting, and $\mathbf d$ the dipole moment. Two distinct consequences follow from the *same* coupling, and keeping them apart is most of the practical content:

| | Resonant TLS ($\hbar\omega_{\text{TLS}} \approx \hbar\omega_{\text{device}}$) | Off-resonant / thermally switching TLS |
|---|---|---|
| Effect | absorbs a photon — **energy loss**, $T_1$ | shifts the device frequency — **dephasing**, $1/f$ noise |
| Observable | loss tangent $\tan\delta$, quality factor | frequency jitter, spectral diffusion, $T_2$ |
| Saturates at high power? | **yes** — a resonant TLS can only absorb so fast | no |
| Temperature dependence | $\tanh(\hbar\omega/2k_BT)$ — worse when cold | switching rates thermally activated |

**The power dependence is the fingerprint.** A resonant TLS is a two-level absorber and therefore **saturable**: drive it hard and it spends half its time excited and stops absorbing. So TLS-limited loss *decreases* with drive power,
$$\tan\delta(n) = \frac{\tan\delta_0}{\sqrt{1 + n/n_c}} + \tan\delta_{\text{other}}$$
which is diagnostic — measure $Q$ versus circulating photon number $n$, and a rise that saturates identifies TLS while a flat curve indicates conductor or radiative loss. **This is why single-photon $Q$ is the only figure that matters for qubits:** a resonator that looks excellent at high power can be TLS-dominated at the one-photon level a qubit actually lives at.

**Participation ratio — where the design leverage is.** Total loss is a weighted sum over the lossy regions:
$$\frac{1}{Q} = \sum_i p_i \tan\delta_i, \qquad p_i = \frac{\int_{V_i}\varepsilon_i|\mathbf E|^2\,dV}{\int_{\text{all}}\varepsilon|\mathbf E|^2\,dV}$$

$p_i$ = the fraction of total electric field energy stored in region $i$. The lossy regions are nanometers thick with $\tan\delta \sim 10^{-3}$, but $p_i \sim 10^{-3}$–$10^{-4}$, so they contribute comparably to a bulk with $\tan\delta \sim 10^{-7}$. **You cannot make the oxide good, so you make $p$ small:** widen gaps and electrodes so the field spreads into vacuum or crystalline substrate, and keep field maxima away from interfaces. The three interfaces that matter are metal–air, substrate–air, and metal–substrate.

**Where the TLS live:** native oxides on the metal, the substrate's damaged surface layer, resist and etch residue, the junction's own tunnel barrier and its edges. Mitigation is materials and geometry, not circuit design — surface treatment ([[Surface Preparation and Cleaning]]), encapsulation, substrate annealing, and larger feature sizes.

## The same physics off the superconducting platform

- **Microwave and optical resonators** — the intrinsic $Q$ floor at low temperature and low power.
- **Ion-trap anomalous heating.** Surface-electrode traps heat the ion motion far faster than thermal (Johnson) noise predicts, with electric-field noise $S_E \propto 1/f$ and a steep dependence on ion–electrode distance $d$ (roughly $d^{-4}$). Fluctuating surface dipoles — the same patch/TLS physics — are the leading explanation, which is why ion-trap coherence is a *surface-science* problem and why cleaning and in-situ treatment reduce heating rates ([[Resolved Sideband Cooling]] measures the rate; [[Noise Spectra and Coupling to Systems]] converts $S_E$ to a heating rate).
- **Glasses generally** — the uniform-$P(E)$ TLS model is the standard tunneling model of low-temperature glass anomalies (specific heat $\propto T$, thermal conductivity $\propto T^2$), and predates its quantum-device application by decades.

The unifying statement: **an amorphous surface is a bath of slow, saturable, dipole-coupled fluctuators**, and any device storing electric field near one inherits both resonant loss and $1/f$ frequency noise. The $1/f$ spectrum itself is the generic result of summing many two-state switchers with a broad distribution of rates ([[Flicker Noise]]).

> [!question]- A resonator has $Q = 10^6$ at high power but $10^5$ at single-photon level. What is the mechanism, and what do you change?
> Saturable loss, so TLS. At high drive the resonant fluctuators are saturated and stop absorbing; at one photon they absorb freely. Circuit changes will not help — reduce the participation ratio by widening gaps and moving field maxima off interfaces, and clean or remove the lossy oxide.

# Connections

- [[Superconducting Qubits]] — the platform this limits; single-photon $Q$ as the relevant figure
- [[Josephson Junction]] — the tunnel barrier and its edges as a TLS host
- [[Flicker Noise]] — why many two-state switchers sum to a $1/f$ spectrum
- [[Noise Spectra and Coupling to Systems]] — converting $S_E(\omega)$ into a heating or decoherence rate
- [[Surface Preparation and Cleaning]] — the mitigation that actually moves the number
- [[Resolved Sideband Cooling]] — how anomalous heating rates are measured on ions
- [[T1 and T2]] — resonant loss feeds $T_1$, slow switching feeds $T_2$
- [[Dielectrics and Polarizability]] — loss tangent as the imaginary part of $\varepsilon$

---
Source: Müller, Cole & Lisenfeld, "Towards understanding two-level-systems in amorphous solids," *Rep. Prog. Phys.* 82, 124501 (2019); Brownnutt et al., "Ion-trap measurements of electric-field noise near surfaces," *Rev. Mod. Phys.* 87, 1419 (2015)
