#AMO #quantum

**A Raman transition couples two stable ground states through a far-detuned excited state using two lasers; adiabatically eliminating the excited state leaves an effective two-level system whose Rabi frequency is $\Omega_1\Omega_2/2\Delta$ and whose "photon" is the difference of the two beams.** It is how you drive a microwave-frequency qubit with optical photons — buying optical momentum kicks and optical focusing for a hyperfine transition.

# Reference

**The Λ system.** States $|1\rangle, |2\rangle$ (hyperfine/Zeeman ground states, splitting $\omega_{12}$) each coupled to excited $|e\rangle$ with Rabi frequencies $\Omega_1, \Omega_2$, both lasers detuned by the *same* large $\Delta \gg \Omega_i, \Gamma$, with their frequency *difference* matched to the qubit: $\omega_{L1} - \omega_{L2} = \omega_{12}$ (two-photon resonance). Second-order perturbation theory (adiabatic elimination of $|e\rangle$) gives the effective two-level Hamiltonian:

$$\Omega_{\text{eff}} = \frac{\Omega_1 \Omega_2}{2\Delta}, \qquad \delta_{\text{AC}} = \frac{\Omega_1^2 - \Omega_2^2}{4\Delta}\ (\text{differential light shift}), \qquad P_e \sim \frac{\Omega_i^2}{4\Delta^2},$$

with spontaneous-emission error per π-pulse $\sim \Gamma/\Delta \times$ (order unity) — **the central trade: detune further to suppress scattering, pay in Rabi frequency (linear in $1/\Delta$ both ways), then recover $\Omega_{\text{eff}}$ with power.** Error per gate $\propto \Gamma/\Delta$ is why high-power lasers at huge detunings (or clock/optical qubits that skip Raman entirely) are the fidelity route.

**What the two-photon process inherits from light:**

- **Momentum:** the atom absorbs $\hbar\mathbf{k}_1$ and emits $\hbar\mathbf{k}_2$ — net kick $\hbar(\mathbf{k}_1 - \mathbf{k}_2)$. **Co-propagating** beams: $\Delta k \approx 0$ — no motional coupling, Doppler-insensitive, a pure qubit drive. **Counter-propagating**: $|\Delta k| \approx 2k$ — full optical Lamb-Dicke coupling on a microwave transition, which is what makes [[Sideband Transitions]] and ion gates possible on hyperfine qubits ([[Lamb-Dicke Regime]] with $\eta$ computed from $\Delta k$). You *choose* the coupling by beam geometry — the defining engineering freedom of Raman.
- **Focusability:** optical beams address single atoms/ions in a chain — µm resolution for a GHz transition that a microwave horn would drive globally.
- **Phase:** the qubit sees the *difference phase* $\phi_1 - \phi_2$. Both beams from one laser through one AOM path → common-mode phase noise cancels; separate paths → interferometric stability required. Beam-path engineering is qubit-coherence engineering.

**Doppler/motional sensitivity** follows the same rule: two-photon detuning shifts by $\Delta\mathbf{k}\cdot\mathbf{v}$ — co-propagating Raman is velocity-insensitive; counter-propagating picks up full Doppler width (why Rydberg two-photon excitation and atom interferometry care about temperature).

**The differential light shift** $\delta_{\text{AC}}$ is the standard systematic: it moves the qubit frequency with laser intensity, converting intensity noise into dephasing. Mitigations: balance $\Omega_1 = \Omega_2$, choose "magic" detunings between fine-structure lines where the shifts cancel, or calibrate and track.

**Relatives, one line each:** **STIRAP** ([[EIT and STIRAP]]) uses the same Λ system adiabatically instead of with pulse areas — robust transfer, no $\Omega t$ calibration. **Coherent population trapping/EIT** — the dark state of the same system. **Raman spectroscopy** (chemistry) — same virtual-state physics, vibrational states as the ground manifold. **Stimulated Raman with shaped pulses** — atom-interferometer beamsplitters ($\pi/2$–$\pi$–$\pi/2$ with momentum transfer).

> [!question]- Your co-propagating Raman carrier is clean, but switching to counter-propagating beams the π-time got longer and fringe contrast dropped. What physics turned on?
> Two things came with $\Delta k \neq 0$. The coupling now carries the Debye-Waller/Lamb-Dicke factor $e^{-\eta^2(2\bar n + 1)/2}$ — a hot ion/atom smears the optical phase over its wavepacket, weakening the carrier (longer π-time) and, since $\bar n$ fluctuates shot to shot, washing contrast. And the transition is now Doppler-sensitive, so motional heating and thermal velocity dephase the fringe. Both are the price of the very coupling you switched geometries to obtain — and the reason gate performance depends on ground-state cooling even for "internal-state" operations.

# Connections

- [[Lamb-Dicke Regime]] — $\eta$ built from $\Delta k$; the coupling and its thermal suppression
- [[Sideband Transitions]] — what counter-propagating Raman drives
- [[Stark Effect and Light Shifts]] — $\delta_{\text{AC}}$ is a differential AC Stark shift
- [[Dressed States]] / [[Rotating Wave Approximation]] — the adiabatic-elimination machinery
- [[EIT and STIRAP]] — the same Λ system used adiabatically
- [[Rydberg Atoms and Blockade]] — two-photon excitation with the same Doppler bookkeeping
- [[Acousto-Optic Modulator]] — where the frequency difference and common path are made

---
Source: Wineland et al., *J. Res. NIST* 103, 259 (1998), Sec. 3; Foot, *Atomic Physics*, Ch. 9.7; Ozeri et al., *Phys. Rev. A* 75, 042329 (2007) (scattering error budget)
