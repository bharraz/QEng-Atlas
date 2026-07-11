#quantum-optics

**Put a mechanical oscillator inside a cavity so that its position shifts the cavity frequency; a drive detuned to the red sideband then does to a milligram mirror exactly what resolved-sideband cooling does to an ion — beamsplitter coupling, ground-state cooling, sidebands and all.** Optomechanics is trapped-ion physics with the roles re-cast: the "internal state" is a driven cavity mode, and the oscillator can be anything from a photonic-crystal beam to a kilogram LIGO mirror.

# Reference

**The coupling.** Cavity frequency depends on mechanical position: $\omega_c(x) \approx \omega_c - G x$ (moving mirror, membrane, or a breathing photonic-crystal mode). With $x = x_{\text{zpf}}(b + b^\dagger)$:

$$H = -\hbar g_0\, a^\dagger a\, (b + b^\dagger), \qquad g_0 = G\, x_{\text{zpf}}$$

— **radiation pressure per photon**, typically Hz–kHz: far too weak alone. Drive the cavity with $\bar n_{\text{cav}}$ photons and linearize: the coupling becomes $g = g_0\sqrt{\bar n_{\text{cav}}}$ between the mechanical mode and the cavity *fluctuations* — MHz-scale, tunable by drive power, and its character selected by detuning:

- **Red-detuned** ($\Delta = -\omega_m$): $H \propto a^\dagger b + a b^\dagger$ — beamsplitter. Phonon → photon → leaks out the cavity: **sideband cooling**, cooling rate $\Gamma_{\text{opt}} = 4g^2/\kappa$, exactly the [[Resolved Sideband Cooling]] Hamiltonian with the cavity linewidth κ playing spontaneous emission. Requires the **resolved-sideband regime** $\omega_m \gg \kappa$; final occupation $\bar n_{\min} \approx (\kappa/4\omega_m)^2$ plus the thermal load $\bar n_{\text{th}}\gamma_m/\Gamma_{\text{opt}}$.
- **Blue-detuned** ($\Delta = +\omega_m$): $H \propto a^\dagger b^\dagger + ab$ — two-mode squeezing: amplification, entanglement, self-oscillation ("phonon lasing") when gain beats $\gamma_m$.
- **On resonance**: phase readout — the cavity output phase measures $x$ with sensitivity that runs into the **standard quantum limit**: shot noise (imprecision) improves with power while radiation-pressure backaction worsens, crossing at the SQL — the concrete stage where measurement backaction, [[Squeezed States|squeezed-light]] evasion, and quantum-nondemolition ideas are demonstrated (and the physics of LIGO's quantum noise budget).

**Figures of merit:** single-photon cooperativity $C_0 = 4g_0^2/\kappa\gamma_m$; the quantum-enabled condition is $C_0 \bar n_{\text{cav}} > \bar n_{\text{th}}$ (coupling beats thermal decoherence); $Q_m \times f_m > k_BT/h$ (~6×10¹² at 300 K) marks where a mechanical mode holds coherence for one period — the reason for the field's obsession with high-$Q_m$ materials (strained Si₃N₄, soft-clamped membranes reach $Q_m > 10^9$).

**Why it matters** (the literature's threads): ground-state cooling of macroscopic objects (2010–11 milestones — quantum mechanics at the µg–mg scale, and tests of collapse models); **microwave-to-optical transduction** — one mechanical mode coupled to both a superconducting circuit and an optical cavity is the leading route to networking dilution-fridge qubits over fiber; mechanical modes as quantum memories and force/acceleration/mass sensors at their thermal limits ($\sqrt{4k_BT m \gamma_m}$ force noise — the mechanical Johnson noise, see [[Johnson-Nyquist Noise]]); and levitated optomechanics (optically trapped nanospheres, [[Optical Tweezers]] pushed to the quantum regime) for matter-wave interferometry of massive objects.

**The dictionary to your ion intuition:** trap frequency ↔ $\omega_m$; Lamb-Dicke parameter ↔ $g_0/\kappa$ being small; carrier/red/blue sidebands ↔ $\Delta = 0, \mp\omega_m$; sideband asymmetry thermometry works identically (red/blue scattering ratio = $\bar n/(\bar n + 1)$); resolved-sideband condition κ vs $\omega_m$ ↔ Γ vs trap frequency. The one structural difference: the coupling is *parametric* (photon number × position), so it must be activated by a drive, which is also what makes it switchable.

> [!question]- Why does optomechanical sideband cooling need a good cavity ($\omega_m \gg \kappa$) when Doppler cooling of atoms works fine with $\Gamma \gg \omega_{\text{trap}}$?
> Same tradeoff as the atomic case, run in reverse preference. A broad line (κ or Γ large) cools via velocity-dependent force but cannot tell red from blue sideband — absorption of both is allowed, and the blue (heating) events set the Doppler-type limit $\bar n \sim \kappa/\omega_m \gg 1$. Reaching the ground state requires energy resolution: scatter *only* red-sideband photons, i.e. the linewidth must resolve the sidebands, $\kappa \ll \omega_m$ — precisely why ion ground-state cooling uses a narrow transition (or Raman line) rather than the broad Doppler line, and why optomechanics needed high-finesse microcavities before ground-state cooling fell.

# Connections

- [[Resolved Sideband Cooling]] — the same physics on an ion; this page's Rosetta stone
- [[Sideband Transitions]] — red/blue sideband algebra
- [[Cavity QED]] / [[Jaynes-Cummings Model]] — the two-level analogue; optomechanics is the oscillator-oscillator version
- [[Input-Output Theory]] — how the cooling and readout leave through κ
- [[Squeezed States]] — backaction evasion and the blue-detuned interaction
- [[Optical Tweezers]] — levitated optomechanics
- [[Johnson-Nyquist Noise]] — thermal force noise as mechanical Johnson noise

---
Source: Aspelmeyer, Kippenberg & Marquardt, "Cavity optomechanics," *Rev. Mod. Phys.* 86, 1391 (2014); Chan et al., *Nature* 478, 89 (2011) (ground-state cooling)
