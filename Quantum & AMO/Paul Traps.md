#quantum #AMO #ions

**Earnshaw forbids a static 3D electric minimum, so drive the quadrupole at RF: the time-averaged wiggle energy makes an effective bowl — the ponderomotive pseudopotential.** The ion's motion splits into slow secular oscillation in that bowl plus fast driven micromotion at the RF frequency.

# Reference

Static quadrupoles saddle ($\nabla^2 V = 0$); oscillating $V_0\cos(\Omega_{\mathrm{rf}} t)$ turns the saddle into confinement. Averaging the driven jitter gives the pseudopotential

$$\Psi(\mathbf{r}) = \frac{Q^2 E_0^2(\mathbf{r})}{4 m \Omega_{\mathrm{rf}}^2}$$

$\Psi$ = pseudopotential energy (J); $Q$ = ion charge (C); $E_0(\mathbf{r})$ = amplitude of the RF electric field at position $\mathbf{r}$ (V/m); $m$ = ion mass (kg); $\Omega_{\mathrm{rf}}$ = RF drive angular frequency (rad/s). Depth $\propto E_0^2$ (field *intensity*, not potential) so the ion seeks the RF null; $\propto 1/m\Omega_{\mathrm{rf}}^2$ because a heavier ion or a faster drive wiggles less per cycle, storing less kinetic energy to average.

Exact dynamics: the Mathieu equation, whose dimensionless stability parameters are $q$ (RF strength) and $a$ (static strength):

$$q = \frac{2 Q V_0}{m r_0^2 \Omega_{\mathrm{rf}}^2}$$

$V_0$ = RF amplitude on the electrodes (V); $r_0$ = ion–electrode distance (m), so $V_0/r_0^2$ is the quadrupole field gradient — note $q \propto V_0/(m r_0^2 \Omega_{\mathrm{rf}}^2)$: smaller traps reach the same confinement at far lower voltage, which is why surface traps run tens of volts where 3D traps ran hundreds. Read $q$ as the ratio of RF force to the restoring effect of inertia over one drive cycle: motion is stable for $q \lesssim 0.9$ (at $a \approx 0$), and one operates at $q \sim 0.1$–$0.3$ where the secular motion cleanly separates from the drive, giving

$$\omega_{\mathrm{sec}} \approx \frac{q\,\Omega_{\mathrm{rf}}}{2\sqrt{2}}$$

— the slow harmonic frequency (rad/s) in the pseudopotential bowl, always well below $\Omega_{\mathrm{rf}}$ (the separation of timescales that makes the averaging valid).

Typical: $\Omega_{\mathrm{rf}}/2\pi \sim 20$–50 MHz, $\omega_{\mathrm{sec}}/2\pi \sim 1$–5 MHz, trap depths $\sim$ eV ($\sim 10^4$ K — ions stay for days). Linear traps: RF confines radially, static endcaps axially; a chain lines up along the RF-null axis.

**Micromotion:** intrinsic (at the secular turning points) is unavoidable and small; **excess micromotion** — a stray DC field pushing the equilibrium off the RF null — is driven motion at $\Omega_{\mathrm{rf}}$ that Doppler-modulates every laser interaction (sideband structure at $\Omega_{\mathrm{rf}}$, reduced carrier Rabi rates, second-order Doppler clock shifts) and couples RF noise into heating. Compensate with shim electrodes; diagnose via RF-photon correlation or micromotion sidebands.

> [!question]- Why does the ion sit at the RF null, and what happens when a patch potential moves it off?
> The pseudopotential $\propto E_0^2$ minimizes where the RF field vanishes. A stray DC force displaces equilibrium to where the RF field is finite, so the ion is *driven* at $\Omega_{\mathrm{rf}}$ — excess micromotion: modulated laser coupling, Doppler shifts, heating. Hence compensation is a routine calibration, not a one-off.

# Connections

- [[Normal Modes of Ion Chains]] — many ions in one pseudopotential well; the collective coordinates gates use
- [[Method of Images]] — electrode-potential intuition for what voltages make which fields at the ion
- [[Driven Damped Harmonic Oscillator]] — the secular/micromotion split is the classic slow-envelope-plus-fast-drive decomposition
- [[Quantum Harmonic Oscillator]] — the secular motion, quantized, is the phonon ladder everything else runs on

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003), §II
