#AMO
**Cooling and trapping from the same three beam pairs** — optical molasses is just three orthogonal pairs of counter-propagating, red-detuned beams, each pair independently damping velocity along its axis ([[Doppler Cooling]]); a MOT adds a magnetic field gradient on top. The field makes detuning position-dependent the same way atomic velocity makes it velocity-dependent, so the beams that damp velocity automatically also restore position, for free, once polarization is correlated with local field direction.

# Reference

**Combined force** (molasses damping + magnetic restoring — both linearizations of the same scattering-rate formula):
$$
F(z,v) \approx -\beta v - \kappa z, \qquad
\kappa = \frac{\mu'\,(dB/dz)}{\hbar k}\,\beta
$$
$\beta$ = the velocity-damping coefficient from [[Doppler Cooling]]; $\kappa$ isn't independent — it's $\beta$ with the substitution $kv \to \mu' B(z)/\hbar$, because Doppler shift and Zeeman shift enter the detuning identically. One detuning, one set of beams, buys both.

**Quadrupole field** (anti-Helmholtz coil pair):
$$
\mathbf B(\mathbf r) \approx A\,(x,\,y,\,-2z)
$$
axial gradient is $2\times$ the radial gradient — the same asymmetry that makes a tweezer cigar-shaped shows up here as a MOT stiffer along the coil axis.

**Capture velocity** (order of magnitude — decelerating over beam radius $r$ at the scattering-limited max $a_{max}=\hbar k\Gamma/2m$):
$$
v_c \sim \sqrt{\frac{\hbar k \Gamma\, r}{m}}
$$
sets which atoms in a thermal vapor or slowed beam actually get caught.

**Doppler temperature floor** (from [[Doppler Cooling]]):
$$
T_D = \frac{\hbar\Gamma}{2k_B}
$$
a MOT alone bottoms out here; polarization-gradient (sub-Doppler) cooling goes lower once atoms are cold enough for multilevel structure to matter.

# Experimental Considerations

**Typical point:** detuning $\delta\sim-1$ to $-3\,\Gamma$, a few $I_{sat}$ per beam, gradient $\sim10$–$20$ G/cm — traded off between capture volume/velocity and final temperature/density.

**Density is capped, and not by the trap:** past $\sim10^{10}$–$10^{11}\,\mathrm{cm^{-3}}$, photons scattered by one atom get reabsorbed by a neighbor before escaping (radiation trapping) — an effective repulsion between atoms that grows with density and cloud size, balancing confinement regardless of atom number or trap depth. More atoms buys a bigger cloud, not a denser one.

**Dark SPOT:** hollowing out the repump beam at the center leaves atoms in a dark hyperfine state where density is highest, suppressing exactly the scattering that drives radiation trapping — a direct fix for the mechanism above, at the cost of some cooling/imaging light.

**Loading balance:** $\dot N = R_{load} - N/\tau - \beta_2\!\int\! n^2\,dV$ — background-gas collisions set $\tau$, light-assisted collisions set $\beta_2$. Steady-state $N$ is a balance point, not a ceiling you load up to and stop.

> [!question]- If more power means more scattering force, why doesn't a stronger MOT just give a denser cloud?
> Confinement scales with $\beta,\kappa$ — laser power, detuning, gradient. But the density ceiling comes from an atom–atom effect (reabsorbed photons) set by the cloud's optical density, not by trap stiffness. Push confinement harder and the cloud shrinks toward that ceiling, then further pushing just adds atoms at the edges — bigger $N$, same density. It's why loading a tweezer or lattice from a MOT usually adds a compression/molasses stage rather than just cranking up MOT power.

# Connections
- [[Doppler Cooling]] — the velocity-dependent half of the force; $\beta$ and $T_D$ both live there
- [[Zeeman Effect (Atlas)]] — the position-dependent detuning the field creates
- [[Optical Pumping]] — repump light, dark states, why Dark SPOT works
- [[Two-Level Systems]] — the underlying scattering-rate formula both $\beta$ and $\kappa$ derive from
- [[Optical Tweezers]] — the MOT is usually the atom source loaded into the trap
- [[Photodetection and Shot Noise]] — fluorescence imaging of MOT number/density