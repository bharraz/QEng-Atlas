#solid-state #quantum-info

**A single electron spin in a crystal, such as an NV center in diamond, can sit a few nanometres below the surface, closer to a sample than most magnetometers can get, and a microwave pulse sequence selects which signal its phase records: a static field, a field oscillating at one frequency, the weak field of nuclear spins in a sample, or the magnetic noise that makes it relax.** Optical readout then turns each choice into a measurement — magnetometry, nanoscale NMR, or relaxometry.

# Reference

**The protocols, by what the sequence selects:**

| Protocol | Sequence | Senses | Limited by | What is read |
|---|---|---|---|---|
| DC magnetometry | Ramsey, or continuous ODMR | static field | $T_2^*$ | phase, or the ODMR line position ([[Spin-Dependent Fluorescence and ODMR]]) |
| AC magnetometry | Hahn echo, CPMG, XY8 with π-pulse spacing $\tau$ | field oscillating at $f = 1/2\tau$ | $T_2$ | coherence against $\tau$ |
| noise spectroscopy | decoupling sequences at varied spacing | the spectral density of the environment | $T_2$ | coherence decay, inverted with filter functions ([[Noise Spectroscopy and Filter Functions]]) |
| correlation spectroscopy | two sensing blocks separated by a variable delay, the first result stored as spin population | a signal's frequency, with resolution set by the delay | $T_1$, or a nuclear-spin memory | oscillation of the correlation against delay |
| synchronized readout (quantum heterodyne) | sensing blocks repeated in step with an external clock | a coherent signal's frequency and phase | the clock and the total measurement time, not the spin's coherence | the beat in the record of outcomes |
| nanoscale NMR | AC magnetometry or correlation spectroscopy at a nuclear Larmor frequency | nuclear spins in a sample on the surface | depth of the defect | signal at the nuclear frequency |
| $T_1$ relaxometry | prepare $m_s = 0$, wait, read | magnetic noise at the GHz spin transition: paramagnetic species, spin waves, current noise in metals | intrinsic $T_1$ | relaxation rate |
| thermometry, electrometry, strain sensing | the same sequences on the temperature-, field-, and strain-dependent terms of the spin Hamiltonian | temperature, electric field, stress | the corresponding couplings | shifts of the resonance ([[NV Centers (atlas)]]) |

**AC sensing.** A signal $b\cos(2\pi f t)$ matched to the π-pulse spacing adds phase in every interval, because each π pulse flips the spin as the signal changes sign:

$$
\phi_\text{AC} = \frac{2}{\pi}\,\gamma\, b\, T
$$

- $\gamma$ — gyromagnetic ratio of the sensor spin (rad s⁻¹ T⁻¹)
- $b$ — amplitude of the oscillating field (T)
- $T$ — total sensing time (s): number of π pulses × spacing $\tau$
- $2/\pi$ — the factor lost by sensing with a square-wave sign pattern

AC sensing gives up only the factor $2/\pi$ against DC sensing but runs for up to $T_2$ instead of $T_2^*$, which is usually far longer ([[Quantum Sensing]]).

**Picture:** the spin is a compass needle that the pulse sequence tells to listen only to fields that oscillate in step with the flips.

**Nanoscale NMR.** A few nanometres from the surface, the defect senses a sample volume of roughly its depth cubed. That volume holds so few nuclei that their random statistical polarization outweighs the thermal one, so the signal is a fluctuating field with an rms value that falls as depth$^{-3/2}$. Shallow defects therefore gain sensitivity but lose coherence and charge stability from the nearby surface.

**Ensembles versus single defects.** An ensemble of $N$ defects improves sensitivity as $\sqrt N$ but averages over a larger volume, and denser ensembles have shorter coherence (interactions between defects and with other impurities) and broader lines (strain and field inhomogeneity, four NV orientations). Wide-field imaging with a camera over an ensemble layer gives magnetic images with diffraction-limited resolution; a single defect on a scanning tip gives nanometre resolution, one point at a time.

**Other spin defects** use the same protocols: silicon-vacancy and divacancy centres in SiC, and boron vacancies in hexagonal boron nitride, which can be placed in direct contact with a 2D material ([[Color Centers]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| splitting of the ODMR lines | the field component along the defect axis |
| a coherence dip at pulse spacing $\tau$ | a signal or nuclear species at $f = 1/2\tau$ — check for dips from the host's own $^{13}$C nuclei and from harmonics of the pulse sequence before assigning it |
| $T_1$ shortened near a sample | magnetic noise at the spin's transition frequency |
| oscillation of a correlation-spectroscopy signal against delay | a frequency, resolved far more finely than one echo can |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| spurious dips in decoupling spectra | the host $^{13}$C Larmor frequency and finite pulse widths create signals at harmonics | a "signal" that moves with the bias field the way $^{13}$C would |
| temperature mistaken for field | the zero-field splitting shifts with temperature | drifting resonances that track laser or microwave heating |
| charge-state conversion | near surfaces, and under strong illumination, the negative charge state converts to a dark neutral one | falling contrast; blinking |
| misaligned bias field | a field off the defect axis mixes spin states | reduced optical contrast and shorter coherence |

> [!question]- Why does correlation spectroscopy resolve a signal's frequency far more finely than an echo sequence, using the same spin?
> In an echo, frequency resolution is about $1/T$ with $T$ limited by the phase-coherence time $T_2$. Correlation spectroscopy converts the first block's phase into population, which survives for $T_1$ (or longer in a nuclear-spin memory), then correlates it with a second block a delay $t$ later. The resolution becomes $1/t$, limited by $T_1$ rather than $T_2$.

# Connections

- [[NV Centers (atlas)]] — the spin Hamiltonian and its sensing channels
- [[Color Centers]] — other defects that run the same protocols
- [[Spin-Dependent Fluorescence and ODMR]] — the optical readout every protocol ends with
- [[Quantum Sensing]] — the sensitivity formula and quantum limits
- [[Noise Spectroscopy and Filter Functions]] — sequences as filters, and inverting them
- [[Spin Echo and Dynamical Decoupling]] — the sequences themselves
- [[Ramsey Interferometry]] — DC phase accumulation
- [[Hyperfine Structure]] — coupling to nuclear spins, as signal or as memory
- [[Lock-In Detection]] — the classical analogue of synchronized sensing
- [[Photon Detectors]] — collecting the readout fluorescence

---
Source: C. L. Degen, F. Reinhard & P. Cappellaro, "Quantum sensing," *Rev. Mod. Phys.* 89, 035002 (2017); J. F. Barry et al., "Sensitivity optimization for NV-diamond magnetometry," *Rev. Mod. Phys.* 92, 015004 (2020); R. Schirhagl, K. Chang, M. Loretz & C. L. Degen, *Annu. Rev. Phys. Chem.* 65, 83 (2014)
