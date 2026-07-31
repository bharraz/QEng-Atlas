#AMO #nanofab

**A vacuum system is a current divider for gas: sources inject a load $Q$, pumps remove at speed $S$, and $P = Q/S_{\text{eff}}$. The gauge reads the balance, not the pump.** Vacuum engineering is this accounting: identify the dominant source, find whether pump or plumbing is the bottleneck, and know which flow regime the gas is in.

# Reference

**Units:** 1 mbar = 100 Pa; 1 Torr = 1.333 mbar; 1 atm = 1013 mbar. Load $Q$ in mbar·L/s ($\propto$ molecules/s via $PV = Nk_BT$); speed $S$ and conductance $C$ in L/s.

**Regimes** via Knudsen number $\mathrm{Kn} = \lambda_{\text{mfp}}/d$: viscous ($\mathrm{Kn} \ll 1$, gas moves as fluid) vs **molecular** ($\mathrm{Kn} \gg 1$, below ~$10^{-3}$ mbar): molecules fly wall to wall independently — a pump is a hole molecules wander into and do not return from. $\lambda \approx 6.6\ \mathrm{cm} \times 10^{-3}\ \mathrm{mbar}/P$. Monolayer formation time ~1 s at $10^{-6}$ mbar, $\propto 1/P$ — the reason surface work needs UHV, independent of collision arguments.

## The circuit formalism

$$Q = C(P_1 - P_2), \qquad \frac{1}{C_{\text{series}}} = \sum_i \frac{1}{C_i}, \qquad P = \frac{Q}{S_{\text{eff}}}, \qquad \frac{1}{S_{\text{eff}}} = \frac{1}{S_{\text{pump}}} + \frac{1}{C}.$$

The dictionary: $Q$ = gas throughput (how much gas flows, mbar·L/s) ↔ current; $P$ = pressure ↔ voltage; $C$ = **conductance** of a tube or aperture — the flow it passes per unit pressure difference, i.e. how easily gas gets through it — ↔ $1/R$; $S$ = pumping speed (volume of gas removed per second at the pump inlet) — a pump is a conductance to a place of zero return. Series conductances add reciprocally like series resistors, and the pump + its plumbing combine the same way: $S_{\text{eff}}$ is always *less* than both.

In molecular flow, $C$ depends only on geometry, not on pressure: molecules travel independently, so doubling $P$ doubles the flow and the flow-per-pressure-difference ratio stays fixed. For air at 300 K: aperture of area $A$, $C \approx 11.6\,A$ ($A$ in cm², $C$ in L/s); **long** tube of diameter $d$ and length $L$, $C \approx 12.1\, d^3/L$ (cm, L/s). The tube formula assumes $L \gg d$; for short tubes it overestimates, and the fix is to put the tube's conductance in series with the entrance aperture's (equivalently, apply the Clausing transmission factor) — sources quoting $11.6\,d^3/L$ differ by exactly this choice — $d^3$ because the aperture area gives $d^2$ and the probability of traversing the tube without being bounced back gives another $d/L$. The $d^3$ is the design rule: a 500 L/s turbo behind a 25 cm × 2 cm tube ($C \approx 39$ L/s) is a 36 L/s system. Short and fat beats a bigger pump; UHV pumps hang directly on large flanges.

## Sources (the pump-down sequence)

1. **Bulk gas** — $P(t) \sim e^{-St/V}$, gone in minutes.
2. **Surface water** — dominates $10^{-5}$–$10^{-9}$ mbar; multilayer hydrogen-bonded, desorbs with $Q \propto t^{-1}$ (10× longer pumping → 10× lower). **Bakeout** (120–250 °C, days) works because desorption is Arrhenius: pay the water debt fast, cool into a clean state.
3. **Hydrogen from the steel bulk** — the post-bake floor, ~$10^{-12}$ mbar·L/s/cm² (reduced by vacuum-firing).
4. **Leaks and permeation** — He through Viton; scratched knife-edges. Distinguish by **rate-of-rise**: valve off the pump; a leak rises linearly forever (constant $Q$), outgassing flattens as surfaces equilibrate.

Budget: $P_{\text{final}} = (\text{area} \times q_{\text{outgas}})/S_{\text{eff}}$. Example: 1000 cm² unbaked ($10^{-8}$ mbar·L/s/cm²) into 100 L/s → $10^{-7}$ mbar; no pump fixes this, a bake (100× lower $q$) does.

## Pumps and gauges

- **Turbomolecular**: momentum transfer from ~km/s blades; compression ratio $\propto e^{\sqrt{m}}$ — enormous for N₂, ~$10^3$ for H₂. The UHV limit of a turbo *is* hydrogen; needs a backing pump.
- **Capture** (ion pumps, NEG/Ti-sublimation, cryopumps): no moving parts, no backing line; finite capacity; blind spots (NEG: noble gases, CH₄; ion pumps: He, Ar; cryo: releases all on warming).
- **Gauges**: Pirani (thermal conductivity, rough–$10^{-3}$); Bayard–Alpert ionization (HV/UHV; gas-species-dependent, hot filament outgasses); **RGA** — a mass spectrum tells *which* source regime you are in (H₂O vs H₂ vs He).
- **Materials**: stainless/OFHC, CF + copper gaskets for UHV; KF/Viton ≲ $10^{-8}$ mbar (permeation); no trapped volumes (vented screws); no fingerprints.

> [!question]- Chamber at 5×10⁻⁸ mbar, target 10⁻¹⁰; the turbo is throttled to half speed by plumbing. Fix the plumbing?
> Run the budget first. RGA shows water → the unbaked load holds $P$ regardless of $S$ ($Q$ is 100× too high): bake. Post-bake H₂-dominated → turbo speed barely helps (poor H₂ compression): add a capture pump sized for hydrogen. Conductance is the answer only when the load is already irreducible. Source control, then plumbing, then pumps.

# Connections

- [[Paul Traps]] — trap lifetime = background-collision interval
- [[Thin-Film Deposition]] — mean free path and monolayer time as process parameters
- [[Plumbing]] — the same series-conductance triage at positive pressure
- [[Cryogenics]] — cryostats are vacuum systems; cold surfaces cryopump
- [[Surface Preparation and Cleaning]] — adsorbed water from the surface side

---
Source: O'Hanlon, *A User's Guide to Vacuum Technology*, Ch. 3–8, 19; Jousten (ed.), *Handbook of Vacuum Technology*
