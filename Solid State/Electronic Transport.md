#solid-state

**Conductivity is carrier density times mobility, $\sigma = ne\mu$; the Hall effect separates the two, and a magnetic field strong enough to close cyclotron orbits reorganizes transport entirely into Landau levels and the quantum Hall effect.** Transport measurements are how carrier density, mobility, and eventually topology are read out of a material.

# Reference

**Drude relations** (scattering time $\tau$, effective mass $m^*$):

$$\sigma = \frac{n e^2 \tau}{m^*} = n e \mu, \qquad \mu = \frac{e\tau}{m^*}, \qquad l = v_F \tau.$$

$\sigma$ = conductivity (S/m); $n$ = carrier density (m⁻³, or m⁻² in 2D); $\tau$ = mean time between momentum-randomizing scattering events (s); $m^*$ = effective mass (kg) from the band curvature; $\mu$ = mobility (m²/V·s), the drift velocity per unit field — the *quality* factor of the material, independent of how many carriers it has; $v_F$ = Fermi velocity (m/s); $l$ = mean free path (m).

The factorization $\sigma = ne\mu$ is the useful one: conductivity confuses two independent things, and only the Hall effect separates them — a doped semiconductor and a clean semimetal can share $\sigma$ with $n$ and $\mu$ differing by orders of magnitude in opposite directions.

Scattering rates add (**Matthiessen**): $1/\tau = 1/\tau_{\text{phonon}} + 1/\tau_{\text{impurity}} + \dots$ Phonon scattering grows with $T$ (metals: $\rho \propto T$ above $\sim\Theta_D/3$); impurity scattering is temperature-independent — the low-$T$ plateau is the **residual resistivity**, and the residual-resistivity ratio RRR $= \rho_{300\mathrm{K}}/\rho_{4\mathrm{K}}$ is the standard purity metric. Semiconductors invert the metallic trend: $n(T)$ is exponential ([[Semiconductors and Junctions]]), so conductivity *rises* with temperature until doping saturates.

**Hall effect** — current $I$ along $x$, field $B$ along $z$; the Lorentz force builds a transverse voltage until it balances:

$$R_H = \frac{E_y}{j_x B} = -\frac{1}{ne}, \qquad n = \frac{IB}{e\, t\, V_H}.$$

$R_H$ = Hall coefficient (m³/C); $E_y$ = transverse field (V/m); $j_x$ = current density (A/m²); $B$ = applied field (T); $V_H$ = measured Hall voltage (V); $I$ = current (A); $t$ = sample thickness along $B$ (m). Note what is *absent* from $R_H$: no $\tau$, no $m^*$ — the transverse field balances the Lorentz force on carriers regardless of how they scatter, so Hall measures pure carrier density and sign, which is exactly why it complements $\sigma$ (which mixes $n$ and $\mu$).

One measurement gives carrier density *and sign* (holes give $+$ — direct evidence that band-top carriers act positively); combined with $\sigma$, it gives $\mu$. Hall + resistivity (van der Pauw geometry on an arbitrary-shaped film) is the default characterization of any new material or 2DEG wafer.

**Transport regimes**, set by comparing sample size $L$ to the length scales: diffusive ($l \ll L$, Drude applies), ballistic ($l > L$ — conduction quantized in units of $G_0 = 2e^2/h$ per mode, the quantum point contact staircase), localized (phase-coherent backscattering at low $T$ wins; $l_\phi$, the phase-coherence length, marks where interference corrections and mesoscopic physics live).

**Landau levels.** When carriers complete cyclotron orbits between scatterings ($\omega_c \tau \gg 1$, $\omega_c = eB/m^*$), the 2D spectrum collapses to

$$E_n = \hbar\omega_c\left(n + \tfrac12\right), \qquad \text{degeneracy } \frac{eB}{h} \text{ per unit area per level}, \qquad \nu = \frac{n_{2D}\, h}{eB}\ (\text{filling factor}).$$

Oscillations of $\rho_{xx}$ as levels sweep through the Fermi energy (**Shubnikov–de Haas**) are periodic in $1/B$ and measure $n_{2D}$ and $m^*$.

**Quantum Hall effect**: at integer $\nu$ the bulk is gapped, current flows in dissipationless chiral edge states, and

$$\sigma_{xy} = \nu\, \frac{e^2}{h}, \qquad \rho_{xx} = 0,$$

quantized to $10^{-9}$ regardless of sample dirt — because $\nu$ is the Chern number of the filled Landau bands, a topological integer ([[Berry Phase and Geometric Phases]]). This is the resistance standard ($h/e^2 = 25\,812.807\ \Omega$) and the prototype of every topologically protected transport phenomenon; fractional $\nu$ signals interaction-driven states beyond the single-particle picture.

> [!question]- A 2DEG wafer datasheet quotes $n = 2\times10^{11}\ \mathrm{cm^{-2}}$ and $\mu = 10^6\ \mathrm{cm^2/Vs}$. What do these imply before any device is made?
> Mean free path: $v_F = \hbar k_F/m^* = \hbar\sqrt{2\pi n}/m^*$ gives $v_F \approx 2\times10^5$ m/s (GaAs, $m^* = 0.067m_e$), and $\tau = \mu m^*/e \approx 38$ ps, so $l = v_F\tau \approx 8\ \mu$m — devices smaller than this are ballistic, and quantum point contacts and clean dot transport are available. It also sets the field scale for quantum Hall physics: $\nu = 2$ at $B = n h/2e \approx 4$ T. Two numbers on the datasheet fix the entire transport regime of anything fabricated on the wafer.

# Connections

- [[Bloch's Theorem and Band Structure]] — $m^*$, $v_F$, and the semiclassical equations transport runs on
- [[Semiconductors and Junctions]] — where $n$ comes from; the 2DEG this page characterizes
- [[Berry Phase and Geometric Phases]] — $\sigma_{xy} = \nu e^2/h$ as a Chern number
- [[Phonons]] — the $T$-dependent scattering channel
- [[Quantum Dots]] — Coulomb blockade as transport in the ultimate small-$L$ limit
- [[Plasma Frequency and Drude Model]] — the AC face of the same Drude parameters

---
Source: Ashcroft & Mermin, *Solid State Physics*, Ch. 1–3, 12–13; Datta, *Electronic Transport in Mesoscopic Systems*, Ch. 1–2; von Klitzing, *Rev. Mod. Phys.* 58, 519 (1986)
