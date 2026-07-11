#quantum-info #metrology

**A pulse sequence acting on a qubit is a band-pass filter on the noise: the decoherence it leaves equals the noise power spectral density overlapped with the sequence's filter function. Run the logic forward to design decoupling; run it backwards and the qubit becomes a spectrum analyzer for its own environment.** This is the quantitative link between your [[Spin Echo and Dynamical Decoupling]] page and how the literature actually characterizes noise.

# Reference

**The formula.** For dephasing noise $\delta\omega(t)$ with (angular-frequency) PSD $S(\omega)$, a sequence of π-pulses defines a modulation $y(t) = \pm 1$ (sign flips at each π-pulse). The coherence after total time $T$ is $W(T) = e^{-\chi(T)}$ with

$$\chi(T) = \int_0^\infty \frac{d\omega}{\pi}\; S(\omega)\, \frac{F(\omega T)}{\omega^2},$$

where $F(\omega T) = |\int_0^T y(t)e^{i\omega t}dt|^2 \omega^2$-normalized is the **filter function** — the squared Fourier transform of the flip pattern. Decoherence = spectral overlap. Everything else is reading this integral:

- **Ramsey** (free evolution): filter peaked at DC — $T_2^*$ measures the *quasi-static* noise, integrated down to the inverse data-run time (why $T_2^*$ depends on how long you average!).
- **Spin echo**: one flip kills the DC lobe; passband centered at $\omega \sim \pi/T$. Echo decay probes noise at $1/T$ — sweeping $T$ *is* coarse spectroscopy.
- **CPMG/periodic DD, $N$ pulses, spacing $\tau$**: a narrow passband at $\omega_0 = \pi/\tau$ (plus odd harmonics), width $\sim 1/T$. The sequence is a lock-in amplifier whose reference is the pulse train.

**Noise spectroscopy = inverting the map.** Fix total time, sweep the CPMG spacing $\tau$: each setting samples $S(\pi/\tau)$ through a narrow filter, and

$$S(\omega_0) \approx \frac{\pi^2}{4}\,\frac{\chi(T)}{T} \quad (\text{narrow-filter limit})$$

reconstructs the spectrum point by point. This is how the standard results were established: the $1/f$-like flux and charge noise in superconducting qubits, the Lorentzian $^{13}$C bath spectrum seen by an NV, spin-bath vs charge-noise attribution in quantum dots. More elaborate protocols (varying pulse number at fixed rate, spectral deconvolution, non-Gaussian extensions) refine the same idea. For $T_1$-type (transverse) noise, the complementary probe is **spin-locking / $T_{1\rho}$**: drive continuously at Rabi frequency $\Omega_R$ and the decay rate samples $S(\Omega_R)$ — sweep the drive power to sweep the probe frequency.

**Design direction.** Given a measured $S(\omega)$, choose the sequence whose filter avoids it: $1/f$-dominated → push the passband high (many fast pulses — coherence grows as $T_2 \propto N^{2/3}$ for $1/f$); a sharp spur (50 Hz, a mechanical resonance) → place filter notches on it; finite-width real π-pulses → their errors accumulate, hence the phase-alternating families (XY-8, KDD) whose filter functions are engineered to cancel pulse imperfections too. The [[Reference Atlas/Math/Magnus Expansion]] is the time-domain view of the same design problem; the filter function is its frequency-domain twin.

**AC sensing is the same object used as a receiver:** an AC field at the filter's passband frequency accumulates *coherently* while everything else is filtered — DD sensing of nT AC fields at kHz–MHz (the NV workhorse), and by sweeping $\tau$, spectroscopy of single nearby nuclear spins (the NMR-of-single-molecules program). Sensitivity bookkeeping then follows [[Fisher Information and the Cramér-Rao Bound]] with $T_2^{\text{(DD)}}$ as the interrogation time.

**Fine print worth knowing:** the exponential-of-integral form assumes *Gaussian, classical* dephasing noise; strongly coupled two-level fluctuators (random telegraph noise) and genuinely quantum baths produce non-exponential decays and filter-function corrections — flagged in the literature as "non-Gaussian noise spectroscopy."

> [!question]- CPMG shows coherence *revivals* at specific pulse spacings instead of monotonic decay. Malfunction?
> Signal, not malfunction: the passband is sweeping across a narrow spectral feature. Collapses occur when $\pi/\tau$ hits the feature — classically a spur, but in the canonical NV/quantum-dot case the feature is a bath's Larmor precession, and the physics is coherent: the sequence periodically echoes the entanglement with the precessing bath spins back out. The revival positions read the Larmor frequency (hence the nuclear species) and the modulation depth reads the coupling — this "malfunction" is precisely how single ¹³C nuclear spins are detected and, with extended sequences, coherently controlled as register qubits.

# Connections

- [[Spin Echo and Dynamical Decoupling]] — the sequences, now with their transfer functions
- [[PSD Estimation]] / [[Power Spectral Density]] — the $S(\omega)$ being measured, and its unit conventions
- [[Flicker Noise]] — the $1/f$ spectra that dominate solid-state qubits
- [[Lock-In Detection]] — the classical instrument this scheme reimplements on a qubit
- [[Reference Atlas/Math/Magnus Expansion]] — time-domain design; filter functions are the frequency-domain view
- [[Fisher Information and the Cramér-Rao Bound]] — from filtered phase to sensitivity
- [[NV Centers (atlas)]] — the platform where DD-based sensing is the core business

---
Source: Bylander et al., *Nat. Phys.* 7, 565 (2011); Degen, Reinhard & Cappellaro, *Rev. Mod. Phys.* 89, 035002 (2017), Sec. VI–VII; Álvarez & Suter, *Phys. Rev. Lett.* 107, 230501 (2011)
