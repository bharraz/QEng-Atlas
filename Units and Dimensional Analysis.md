#reference #units

**Everything in this vault converts through energy: $E = \hbar\omega = hf = k_BT = hc/\lambda = \mu B = mc^2$. Memorize a handful of anchor conversions and every estimate becomes arithmetic.** This is a reference sheet, not a lesson.

# The energy currency

One quantity, six habitats:

| 1 unit of ↓ equals → | Hz        | K       | eV       | cm⁻¹       |
| -------------------- | --------- | ------- | -------- | ---------- |
| 1 GHz                | —         | 48 mK   | 4.14 µeV | 0.033 cm⁻¹ |
| 1 K                  | 20.8 GHz  | —       | 86.2 µeV | 0.695 cm⁻¹ |
| 1 eV                 | 241.8 THz | 11604 K | —        | 8065 cm⁻¹  |
| 1 cm⁻¹               | 30.0 GHz  | 1.44 K  | 124 µeV  | —          |

**Anchors:**
- $\lambda\,[\text{nm}] \times E\,[\text{eV}] = 1240$ (this is $hc$; 500 nm ↔ 2.48 eV ↔ 600 THz)
- $k_B T$ at 300 K = 25.9 meV ≈ 6.2 THz ≈ 208 cm⁻¹ (the "is it frozen out?" comparator)
- $k_B/h$ = 20.8 GHz/K (a 10 mK fridge ↔ 208 MHz: everything below is thermally occupied — why qubits live at 4–8 GHz)
- $\hbar$ = 1.055×10⁻³⁴ J·s = **6.58×10⁻¹⁶ eV·s**; $h$ = 4.14×10⁻¹⁵ eV·s
- 1 µK ↔ 20.8 kHz (Doppler limits, trap depths in frequency units)

**ω vs f — the factor-2π tax:** $\omega = 2\pi f$. "Rabi frequency $\Omega/2\pi$ = 1 MHz" means a π-pulse takes $\pi/\Omega$ = 0.5 µs. Linewidths: $\Gamma$ is usually angular; FWHM in Hz is $\Gamma/2\pi$. When a formula is off by ~6, it's a 2π; when off by ~40, it's $(2\pi)^2$... check the convention *of the source* before the algebra.

# Dimensional identities of the workhorses

| Object                                                     | Dimensions                                                  | The check it enables                                                        |
| ---------------------------------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------- |
| $\hbar$                                                    | energy·time = momentum·length = **action**                  | $\hbar k$ is a momentum; $\hbar/\Delta E$ is a time; phase = action/$\hbar$ |
| $\hbar\omega,\ \hbar\Gamma,\ \hbar\times(\text{any rate})$ | energy                                                      | any rate can be an energy scale and vice versa                              |
| $\hbar c$ = 197 eV·nm                                      | energy·length                                               | pairs with $E$ to make lengths: confinement scales                          |
| $e^2/4\pi\epsilon_0$ = 1.44 eV·nm                          | energy·length                                               | Coulomb estimates without SI constants                                      |
| $[\psi]$ in $d$ dims                                       | length$^{-d/2}$                                             | $\psi^2 d^dx$ dimensionless                                                 |
| Spectral density $S_x(f)$                                  | $x^2$/Hz; amplitude form $\sqrt{S}$ in $x/\sqrt{\text{Hz}}$ | variance = ∫S df; see [[PSD Estimation]]                                    |
| Transition dipole                                          | $e a_0$ = 2.54 Debye = 8.48×10⁻³⁰ C·m                       | Rabi: $\hbar\Omega = dE$                                                    |
| Fine structure α = 1/137                                   | dimensionless                                               | $a_0 = \lambda_C/2\pi\alpha$, atomic velocity $= \alpha c$                  |

**Atomic units** (set $\hbar = e = m_e = 4\pi\epsilon_0 = 1$): length $a_0$ = 0.0529 nm; energy 1 Hartree = 27.2 eV = 2 Ry; time 24.2 as; E-field 5.14×10¹¹ V/m ("the field an electron feels in hydrogen" — the benchmark for *strong* laser fields).

**Natural-units workflow:** set $\hbar = k_B = 1$, compute, and reinstate dimensions at the end by multiplying by the unique combination of $\hbar, k_B, c$ that fixes the units — the anchor table does the arithmetic.

# Magnetic and spin

- $\mu_B/h$ = **14.0 GHz/T** ⇒ electron ($g \approx 2$): **28 GHz/T = 2.80 MHz/G** (the number under every Zeeman splitting, ESR line, NV magnetometry formula)
- Nuclear magneton: 7.6 MHz/T; proton NMR: 42.6 MHz/T — nuclei are ~2000× stiffer, which is the whole story of nuclear-spin memories and of why NMR needs big fields
- 1 G = 10⁻⁴ T = 0.1 mT. Earth's field ≈ 0.5 G ≈ 1.4 MHz of electron Zeeman — never negligible in a lab
- Flux quantum $\Phi_0 = h/2e$ = 2.07×10⁻¹⁵ Wb = 2.07 mT·µm²; Josephson: 483.6 MHz per µV

# Electrical engineering numbers

- **Thermal voltage** $k_BT/e$ = 25.9 mV (300 K) — diode/transistor exponentials, the 60 mV/decade subthreshold slope
- **Johnson noise**: $\sqrt{4k_BTR}$ → **4.1 nV/√Hz for 1 kΩ at 300 K** (scales as √R, √T); as power: −174 dBm/Hz, the RF noise floor
- **Shot noise**: $\sqrt{2eI}$ → 18 pA/√Hz at 1 mA (√I); photon shot noise is the same formula wearing optics clothes
- **dBm into 50 Ω**: 0 dBm = 1 mW = **224 mV rms** = 632 mV pp; +10 dB = ×3.16 in voltage... every 20 dB is ×10 voltage (see [[dB Conventions]])
- **Impedance anchors**: free space 377 Ω; coax 50 Ω; resistance quantum $h/e^2$ = 25.8 kΩ (tunnel junctions must beat this for charge quantization — see [[Quantum Dots]]); superconducting $R_Q = h/4e^2$ = 6.45 kΩ
- **Signals travel** ~5 ns/m in coax (2/3 c), 1 ns per 15 cm on FR4 — a 10 cm trace is a transmission line above ~300 MHz (rise time < 2× delay; see [[Transmission Lines]])
- **RC corner**: $f = 1/2\pi RC$ → 1 kΩ × 1 nF = 159 kHz; scale from there
- 1 dB ≈ 26% power, ≈ 12% voltage; 3 dB = ×2 power; 10 dB = ×10 power

# Optics and atoms

- Photon flux: 1 mW at λ = 500 nm = **2.5×10¹⁵ photons/s** (1 photon/s per 0.4 fW — sets what "single-photon level" means for detectors)
- Intensity → field: $E\,[\text{V/m}] = 27.4\sqrt{I\,[\text{W/m}^2]}$ (1 W focused to 10 µm ≈ 10⁷ V/m — compare to 5×10¹¹ atomic)
- Saturation intensity (dipole transitions): $I_{\text{sat}} = \pi h c \Gamma/3\lambda^3$ ~ mW/cm² for alkali D lines
- Recoil: $v_r = \hbar k/m$ ~ cm/s; recoil energy/frequency $\hbar k^2/2m \sim$ kHz–MHz — the floor under Doppler cooling and the scale in [[Lamb-Dicke Regime]]
- Doppler shift: $kv$ → 1 m/s ↔ ~2 MHz at optical λ (hence MHz-scale laser locks)
- Beam waist ↔ divergence: $\theta = \lambda/\pi w_0$ (see [[Numerical Aperture and Spot Size]])

# Vacuum and gas

- 1 mbar = 100 Pa = 0.75 Torr; 1 atm = 1013 mbar
- Number density: $n = P/k_BT$ → **2.4×10¹⁶ cm⁻³ per mbar** (300 K); at 10⁻¹⁰ mbar: 2.4×10⁶ cm⁻³ — "UHV" still has millions per cm³
- Mean free path (air, 300 K): $\lambda \approx 6.6\,\text{cm} \times \frac{10^{-3}\,\text{mbar}}{P}$
- Monolayer time ≈ 1 s at 10⁻⁶ mbar, scaling as $1/P$ (the surface-science clock — see [[Vacuum Engineering]])

# The dimensional-analysis moves themselves

1. **Rate-energy-time triangle:** any energy scale ÷ $\hbar$ is a rate; any rate is a linewidth; $\Delta E\,\Delta t \sim \hbar$ is dimensional analysis, not mysticism. Coupling 1 MHz ⇒ dynamics on µs ⇒ needs linewidths ≪ 1 MHz to resolve.
2. **Compare to the relevant $k_BT$, not to zero.** Is 5 GHz big? At 300 K, tiny ($k_BT$ = 6 THz); at 10 mK, huge (208 MHz). Every "can I neglect thermal?" question is this division.
3. **Build the answer from the only scales present.** A trap with frequency $\omega$ and mass $m$ has exactly one length: $\sqrt{\hbar/m\omega}$ (the ground-state size — no solving needed). One energy and a dipole ⇒ one field. If your formula has a quantity the physics doesn't contain, it's wrong.
4. **π's are physics, powers are dimensions.** Dimensional analysis fixes exponents exactly and prefactors to within ~10. If an estimate misses by 10³, the *scaling* is wrong — find the missing physics, don't tune prefactors.
5. **Track dB *of what*.** Power dB and voltage/amplitude dB differ by a factor 2 in the exponent; optical density, RF attenuation, and noise figures all quietly choose one. (See [[dB Conventions]].)
6. **Angular or not** — see the 2π tax above; worst in spectral densities, where one-sided vs two-sided *and* Hz vs rad/s give four conventions differing by 2π and 2 (see [[PSD Estimation]]).

# Connections

- [[dB Conventions]] — the logarithmic half of this sheet
- [[PSD Estimation]] — units of noise, where conventions bite hardest
- [[Vacuum Engineering]] — pressure/density/mean-free-path in working context
- [[Numerical Aperture and Spot Size]] — the optics scalings in full
- [[Floating Point and Numerical Error]] — rescaling to O(1) units as numerical hygiene

---
Source: CODATA 2022 values; Steck, *Alkali D Line Data* (steck.us/alkalidata) for the AMO numbers
