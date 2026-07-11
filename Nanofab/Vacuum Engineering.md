#AMO #nanofab

**A vacuum system is a current divider for gas: sources (outgassing, leaks, permeation) inject a gas load $Q$, pumps remove it at speed $S$, and the pressure is just their ratio, $P = Q/S$.** Thinking like a vacuum engineer means doing this accounting — identifying which source dominates, whether the pump or the plumbing is the bottleneck, and which physics regime the gas is in. The pressure gauge reads the *balance*, not the quality of your pump.

# Reference

**Units:** SI is the pascal, but practice is a mess: $1\ \text{mbar} = 100\ \text{Pa}$; $1\ \text{Torr} = 1.333\ \text{mbar}$ (1 mm Hg; US gauges); atmosphere $= 1013$ mbar $= 760$ Torr. Gas load $Q$ is in mbar·L/s (pressure × volume flow — proportional to molecules/s via $PV = Nk_BT$), pumping speed $S$ in L/s, conductance $C$ in L/s. Mbar·L/s and Torr·L/s differ by the 1.333; watch which a spec sheet uses.

**Regimes are set by the mean free path**, via the Knudsen number $\mathrm{Kn} = \lambda_{\text{mfp}}/d$ (chamber/pipe dimension $d$):

- **Viscous flow** ($\mathrm{Kn} \ll 1$, rough vacuum): molecules collide with each other; gas moves as a fluid; pumps push it.
- **Molecular flow** ($\mathrm{Kn} \gg 1$, below $\sim 10^{-3}$ mbar): molecules fly wall-to-wall, never meeting. There is no "flow" to push and no "sucking": **a pump is a hole that molecules occasionally wander into and don't come back out of.** All UHV intuition follows from this picture.

At $10^{-6}$ mbar $\lambda \sim 60$ m; at $10^{-10}$ mbar, tens of km. The other regime-setting number: **monolayer formation time** — at $10^{-6}$ mbar every surface is re-coated with background gas in ~1 s; at $10^{-10}$ mbar you get hours. That, not the pressure itself, is why surface science and clean deposition demand UHV.

## The Ohm's-law analogy (this is the actual working method)

Pressure ↔ voltage, throughput $Q$ ↔ current, conductance $C$ ↔ 1/resistance:

$$Q = C\,(P_1 - P_2), \qquad \frac{1}{C_{\text{series}}} = \sum_i \frac{1}{C_i}, \qquad P = \frac{Q}{S_{\text{eff}}}, \qquad \frac{1}{S_{\text{eff}}} = \frac{1}{S_{\text{pump}}} + \frac{1}{C}.$$

In molecular flow, conductance is a purely geometric constant (no pressure dependence): an aperture passes $C \approx 11.6\,A$ L/s (A in cm², air), a tube $C \approx 12.1\, d^3/L$ L/s (cm). The cubic $d$-dependence is the design lesson: **plumbing dominates**. A 500 L/s turbo behind a 25 cm × 2 cm tube ($C \approx 39$ L/s) is a 36 L/s system — you bought the wrong thing. Short and fat beats big pump every time; this is why UHV chambers hang the pump directly on a large flange.

## Where the gas comes from (the source hierarchy)

Pump-down has phases, each with its own dominant source:

1. **Bulk gas** — leaves in minutes; $P(t) \sim e^{-St/V}$. Irrelevant to the final pressure.
2. **Surface desorption, mostly water** — the enemy from $10^{-5}$ to $10^{-9}$ mbar. Water hydrogen-bonds to every steel/glass surface in multilayers and leaves excruciatingly slowly ($Q_{\text{outgas}} \propto t^{-1}$: pumping for 10× longer gains you 10×). The **bakeout** (120–250 °C, days, whole system under vacuum) works because desorption is Arrhenius — heating shifts days-at-25°C to minutes — so you *pay the water debt fast*, then cool into a clean state.
3. **Diffusion from the bulk** — after bakeout, **hydrogen dissolved in the steel itself** diffuses out and dominates; this is the $\sim 10^{-12}$ mbar·L/s/cm² floor of ordinary stainless (reduced by vacuum-firing the material or lining with a barrier).
4. **Permeation and real leaks** — helium through Viton O-rings, a scratched knife-edge. Distinguish leak from outgassing by a **rate-of-rise test**: valve off the pump and watch $P(t)$ — a leak rises *linearly* forever (constant $Q$); outgassing rises then *flattens* as surfaces re-equilibrate. He leak-checking = spray helium, watch a mass spectrometer on the foreline.

Budget arithmetic: final pressure = (total outgassing area × specific rate) / $S_{\text{eff}}$. A 1000 cm² unbaked chamber at $10^{-8}$ mbar·L/s/cm² into 100 L/s effective sits at $10^{-7}$ mbar — *no pump upgrade fixes this*; a bake ($100\times$ lower rate) does. This one calculation is most of vacuum engineering.

## Pumps and gauges, by mechanism

- **Momentum-transfer** (turbomolecular: blades at ~km/s rim speed hit molecules downward): compression ratio scales exponentially with $\sqrt{m}$ — enormous for N₂, poor (~10³) for H₂. So a turbo's UHV limit *is* hydrogen, and it needs a good backing pump because it compresses, not swallows.
- **Capture** (ion pumps: ionize and bury in Ti; NEG/Ti-sublimation: reactive fresh-metal surface that chemisorbs; cryopumps: freeze onto 10–80 K surfaces): no moving parts, no vibration, no backing line — the UHV workhorses. Finite capacity (they fill up), and each has blind spots: NEG doesn't pump noble gases or methane; ion pumps struggle with He and Ar; cryopumps release everything if warmed.
- **Gauges by regime:** Pirani (thermal conductivity of gas, rough–$10^{-3}$); Bayard–Alpert ionization gauge (ion current from electron impact, HV/UHV; gas-species-dependent calibration, and its hot filament outgasses — the gauge perturbs the measurement); residual gas analyzer (mass spectrometer — not just "how much" but *what*: H₂O vs H₂ vs He tells you which regime of the source hierarchy you are in).

**Materials discipline is source control:** stainless and OFHC copper (low outgassing, bakeable), CF flanges with copper gaskets (bakeable, He-tight) for UHV vs KF/Viton (fast, permeates, ≲$10^{-8}$ mbar); no plastics, no trapped volumes (virtual leaks: a screw hole full of air with no path out vents slowly forever — hence vented screws), no fingerprints (skin oils outgas for weeks).

> [!question]- Your chamber sits at 5×10⁻⁸ mbar and you want 1×10⁻¹⁰. The turbo is only at half its rated speed due to the plumbing. Do you fix the plumbing?
> Run the budget first. If the RGA shows the residual gas is water, conductance is not the problem — an unbaked system's water load holds you at ~10⁻⁸ regardless of speed, since both $Q$ and $S$ enter $P = Q/S$ and $Q_{\text{water}}$ is 100× too high: bake. If after bakeout you sit H₂-dominated, more turbo speed barely helps either (poor H₂ compression) — add a capture pump (NEG/ion) sized for hydrogen. Fixing conductance is the answer only when the gas load is already irreducible. Source control first, then plumbing, then pumps.

# Connections

- [[Paul Traps]] — ion lifetime = collision interval with background gas; the UHV requirement
- [[Doppler Cooling]] — cold-atom experiments live inside this accounting
- [[Thin-Film Deposition]] — mean free path and monolayer time are the process parameters
- [[Superconducting Qubits]] — cryostats are cryopumps; everything condenses at 10 mK
- [[NV Centers (atlas)]] — the exception that needs no vacuum

---
Source: O'Hanlon, *A User's Guide to Vacuum Technology*, Ch. 3–8, 19; Chambers, *Modern Vacuum Physics*, Ch. 4–6; Jousten (ed.), *Handbook of Vacuum Technology*
