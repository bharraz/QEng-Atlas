#labwork #cryo

**Getting cold is a budget problem: heat leaks in by conduction, radiation, wiring, and dissipation; each stage removes it at a temperature-dependent cooling power; base temperature is where load meets lift.** The same accounting discipline as [[Vacuum Engineering]], with $T$-dependent coefficients.

# Reference

**The ladder**: 77 K (LN₂ — shields, precooling), 4 K (LHe / pulse tube — superconductors alive, GHz still thermal), 1 K (pumped ⁴He), 300 mK (³He), ~10 mK (dilution — $k_BT/h$ = 208 MHz < qubit frequencies).

## Dilution refrigerator

Below 0.87 K a ³He/⁴He mixture phase-separates; ³He crossing into the dilute phase absorbs heat like an evaporation whose "vapor pressure" never vanishes (dilute phase holds 6.6% ³He at $T \to 0$). Circulating ³He at $\dot n_3$ mol/s:

$$\dot{Q}_{\text{MC}} \approx 84\, \dot{n}_3\, T^2\ \mathrm{[W]},$$

with $\dot n_3$ the ³He circulation rate in mol/s (~100 µmol/s in a standard fridge) and $T$ the mixing-chamber temperature in K — the cooling power *you can spend* at that stage. The $T^2$ comes from the heat capacity of the degenerate ³He: colder liquid carries less entropy per atom across the phase boundary. Numerically: µW at 100 mK collapses to ~10 nW at 10 mK — every stray nW costs base temperature, and the craft is load management.

## Heat-load accounting (per stage)

- **Conduction**: $\dot Q = \frac{A}{L}\int_{T_1}^{T_2}\kappa(T)\,dT$ — use integrated-conductivity tables ($\kappa$ varies orders of magnitude). Isolation: stainless, CuNi, G-10; thermalization links: annealed OFHC Cu. Wiring dominates real budgets: $N$ coax × (conduction + attenuator dissipation) limits channel count.
- **Radiation**: $\dot Q = \sigma A\,\epsilon_{\text{eff}}(T_h^4 - T_c^4)$ — 300 K radiates ~460 W/m²; 77 K, ~0.5 W/m². The $T^4$ means the question is always *what temperature does this surface see*: nested shields per stage, MLI in the vacuum space (each floating layer roughly halves the flow), no line of sight from warm to cold.
- **Microwave lines**: attenuators distributed across stages (e.g. 20 dB at 4 K + 20 dB at 100 mK + ...) so the noise temperature reaching the sample is that of the last cold attenuator, not 300 K ([[Johnson-Nyquist Noise]]); each attenuator dissipates onto its stage. DC lines: RC/copper-powder filters; superconducting NbTi carries signal with negligible $\kappa$.
- **On-stage dissipation**: HEMTs at 4 K burn mW; resistive joints and eddy currents count against the nW-scale mixing-chamber budget.

## Thermalization is not proximity

Bolted joints conduct through microscopic asperities: gold-plate, torque properly. Below ~1 K electrons and phonons decouple,

$$\dot Q_{e\text{-}ph} = \Sigma V (T_e^5 - T_{ph}^5),$$

with $T_e, T_{ph}$ the electron and lattice temperatures, $V$ the metal volume, and $\Sigma \sim 10^9\ \mathrm{W\,m^{-3}K^{-5}}$ a material constant — the only thermal link between a chip's electrons and its lattice. The $T^5$ makes the link collapse at mK: dissipate a fixed power in a small metal volume and $T_e$ floats far above $T_{ph}$. Electrons then cool mainly *along the wiring* (electronic conduction), so a device's electrons can sit far above the plate if the wiring is not itself thermalized — anchor the wiring, not just the substrate. The plate thermometer is not the device temperature; the device's own noise or residual excited-state population is the honest thermometer. Thermometry: calibrated RuO₂/Cernox (watch self-heating against the local budget); noise thermometry at the bottom.

**Cryocoolers**: pulse tubes give ~1 W at 4 K with 1–2 Hz vibration — soft thermal links and isolated sample mounts for cryo-optics; wet systems trade vibration for He logistics.

> [!question]- The qubit's thermal population implies 60 mK; the mixing-chamber thermometer reads 12 mK. Where is the discrepancy?
> The qubit thermalizes to its electromagnetic environment: under-attenuated or poorly thermalized coax delivers a photon occupation at the qubit frequency far above the plate temperature; IR leaks through non-hermetic sample boxes break the budget the same way (hence light-tight cans and Eccosorb filters); on-chip dissipation rides the $T^5$ electron-phonon bottleneck. The fix is attenuator placement, filtering, and shielding — not a colder fridge.

# Connections

- [[Vacuum Engineering]] — the same load-vs-lift methodology; cryopumping
- [[Johnson-Nyquist Noise]] — noise temperature and distributed cold attenuation
- [[Thermal States]] — $\bar n(\omega, T)$, the quantity attenuation chains manage
- [[Superconducting Qubits]] / [[Quantum Dots]] — the tenants whose requirements set the design
- [[Packaging and Interconnects]] — CTE mismatch and light-tightness at the sample

---
Source: Pobell, *Matter and Methods at Low Temperatures*; Krinner et al., *EPJ Quantum Technology* 6, 2 (2019)
