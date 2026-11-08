#quantum #AMO #ions

**Holding a charged particle needs a potential minimum, but a static electric potential cannot have one in free space: Laplace's equation $\nabla^2 V = 0$ forces any curvature that confines along one axis to anti-confine along another (Earnshaw's theorem), so a static quadrupole is a saddle.** A Paul trap flips the saddle at radio frequency (RF), faster than the ion can roll off it; averaged over the drive, the ion feels an effective bowl, the ponderomotive pseudopotential. Its motion splits into slow secular oscillation in that bowl plus fast driven micromotion at the RF frequency.

# Reference

**Setup:** electrodes around the ion carry a static voltage $U_0$ and an RF voltage $V_0\cos\Omega_{\mathrm{rf}}t$. Near the center an ideal linear trap makes the quadrupole potential $\Phi = (U_0 + V_0\cos\Omega_{\mathrm{rf}}t)\,(x^2 - y^2)/2r_0^2$: focusing along $x$ and defocusing along $y$, then the reverse half a cycle later. The ion's driven jitter is out of phase with the RF force, so it sits farther from the center when the force points inward than when it points outward; because the RF field grows with distance from the center, the inward pushes dominate on average. The result is a net restoring force toward the point where the RF field vanishes, the RF null.

**Pseudopotential** — the time average of that driven jitter:

$$\Psi(\mathbf{r}) = \frac{Q^2 E_0^2(\mathbf{r})}{4 m \Omega_{\mathrm{rf}}^2}$$

- $\Psi$ — pseudopotential energy (J)
- $Q$ — ion charge (C)
- $E_0(\mathbf{r})$ — amplitude of the RF electric field at position $\mathbf{r}$ (V/m)
- $m$ — ion mass (kg)
- $\Omega_{\mathrm{rf}}$ — RF drive angular frequency (rad/s)

Depth $\propto E_0^2$ (field *intensity*, not potential), so the ion seeks the RF null; $\propto 1/m\Omega_{\mathrm{rf}}^2$ because a heavier ion or a faster drive wiggles less per cycle, storing less kinetic energy to average.

**Picture:** a ball on a rotating saddle: if the saddle turns fast enough, the ball stays near the centre even though the surface is never a bowl.

**Exact dynamics: the Mathieu equation.** In the ideal quadrupole each radial coordinate $u$ obeys $d^2u/d\xi^2 + (a - 2q\cos 2\xi)\,u = 0$ with $\xi = \Omega_{\mathrm{rf}}t/2$. The two dimensionless stability parameters are $q$ (RF strength) and $a$ (static strength):

$$q = \frac{2 Q V_0}{m r_0^2 \Omega_{\mathrm{rf}}^2}, \qquad a = \frac{4 Q U_0}{m r_0^2 \Omega_{\mathrm{rf}}^2}$$

- $V_0$ — RF amplitude on the electrodes (V)
- $U_0$ — static voltage in the same quadrupole geometry (V)
- $r_0$ — ion–electrode distance (m), so $V_0/r_0^2$ is the quadrupole field gradient

$a$ and $q$ take opposite signs along $x$ and $y$ (the sign of $q$ only shifts the drive phase); real electrode shapes multiply both by a geometric factor below 1. Note $q \propto V_0/(m r_0^2 \Omega_{\mathrm{rf}}^2)$: smaller traps reach the same confinement at far lower voltage, which is why surface traps run tens of volts where 3D traps ran hundreds. Read $q$ as the ratio of RF force to the restoring effect of inertia over one drive cycle.

**Stability and secular frequency:** motion is stable for $q \lesssim 0.9$ at $a \approx 0$ (precisely $0 < q < 0.908$), and one operates at $q \sim 0.1$–$0.3$ where the secular motion cleanly separates from the drive, giving

$$\omega_{\mathrm{sec}} \approx \frac{q\,\Omega_{\mathrm{rf}}}{2\sqrt{2}}$$

— the slow harmonic frequency (rad/s) in the pseudopotential bowl, always well below $\Omega_{\mathrm{rf}}$ (the separation of timescales that makes the averaging valid). With a static term, $\omega_{\mathrm{sec}} \approx (\Omega_{\mathrm{rf}}/2)\sqrt{a + q^2/2}$.

**Depth:** for the ideal quadrupole at $a = 0$ the pseudopotential at the electrode distance is $qQV_0/8$ — for example $q = 0.3$ and $V_0 = 200$ V give about 7.5 eV for a singly charged ion.

| Quantity | Typical value |
|---|---|
| $\Omega_{\mathrm{rf}}/2\pi$ | 20–50 MHz |
| $\omega_{\mathrm{sec}}/2\pi$ | 1–5 MHz |
| $q$ | 0.1–0.3 |
| Trap depth | $\sim$ eV ($\sim 10^4$ K — ions stay for days) |
| RF amplitude | tens of volts (surface traps) to hundreds (3D traps) |

**Linear traps:** RF confines radially, static endcaps axially; a chain lines up along the RF-null axis. The endcap potential obeys Laplace's equation too, so its axial confinement comes with radial *anti*-confinement: the radial frequency drops to $\omega_r \approx \sqrt{\omega_{\mathrm{sec}}^2 - \omega_z^2/2}$, with $\omega_z$ the axial frequency.

**Micromotion:**

| | Intrinsic | Excess |
|---|---|---|
| Cause | the secular motion itself carries the ion off the RF null, where it is driven | a stray DC field (for example patch potentials on the electrodes) pushes the equilibrium off the RF null |
| Size | unavoidable and small; largest at the secular turning points | grows with the displacement; removable |
| Effect | follows the secular motion; reduced by cooling | driven motion at $\Omega_{\mathrm{rf}}$ that Doppler-modulates every laser interaction (sideband structure at $\Omega_{\mathrm{rf}}$, reduced carrier Rabi rates, second-order Doppler clock shifts) and couples RF noise into heating |
| Handling | cool the secular motion | compensate with shim electrodes (extra DC electrodes that push the ion back onto the null); diagnose via RF–photon correlation (fluorescence timed against the RF phase) or micromotion sidebands |

> [!question]- Why does the ion sit at the RF null, and what happens when a patch potential moves it off?
> The pseudopotential $\propto E_0^2$ minimizes where the RF field vanishes. A stray DC force displaces equilibrium to where the RF field is finite, so the ion is *driven* at $\Omega_{\mathrm{rf}}$ — excess micromotion: modulated laser coupling, Doppler shifts, heating. Hence compensation is a routine calibration, not a one-off.

# Connections

- [[Normal Modes of Ion Chains]] — many ions in one pseudopotential well; the collective coordinates gates use
- [[Method of Images]] — electrode-potential intuition for what voltages make which fields at the ion
- [[Driven Damped Harmonic Oscillator]] — the secular/micromotion split is the standard slow-envelope-plus-fast-drive decomposition
- [[Quantum Harmonic Oscillator]] — the secular motion, quantized, is the phonon ladder everything else runs on
- [[Sideband Transitions]] — where secular and micromotion sidebands show up in the laser spectrum
- [[Qubit Transport and Shuttling]] — moving ions between trap zones

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003), §II
