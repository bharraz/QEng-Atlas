#labwork #cryo

**Getting cold is a budget problem, like vacuum: heat leaks in (conduction, radiation, wiring, RF dissipation), each stage removes it at a temperature-dependent cooling power, and the base temperature is where load meets lift.** Thinking cryogenically = accounting heat flows per stage and knowing which physics dominates at each decade of temperature.

# Reference

**The temperature ladder** and what turns off along it: 77 K (LN₂ — cheap precooling, IR shields), 4 K (liquid He / pulse-tube — superconductors come alive, thermal microwave photons at GHz still abundant), 1 K (pumped ⁴He), 300 mK (pumped ³He), ~10 mK (dilution refrigerator — $k_BT$ = 208 MHz < qubit frequencies: the quantum regime for GHz circuits).

**How a dilution refrigerator works** (the only continuous route below ~300 mK): below 0.87 K a ³He/⁴He mixture phase-separates; ³He crossing from the concentrated into the dilute phase absorbs "latent heat" like an evaporation — but the dilute phase holds 6.6% ³He even at $T \to 0$, so the "evaporation" never runs out. Circulate ³He (pump it from the still at ~0.7 K, purify, recondense) and the mixing chamber cools continuously with power

$$\dot{Q}_{\text{MC}} \approx 84\, \dot{n}_3\, T^2 \quad [\text{W, mol/s, K}]$$

— the $T^2$ is the design fact: ~µW-scale at 100 mK collapses to ~10 nW at 10 mK. Every microwatt of load costs base temperature; the entire craft is load management.

**The heat-load bookkeeping** (per stage, always):

- **Conduction:** $\dot Q = (A/L)\int_{T_1}^{T_2} \kappa(T)\, dT$ — use integrated conductivity tables, since κ varies wildly with T. Material choice is the knob: stainless and CuNi conduct ~100× less than copper; G-10 and Kevlar less still (supports); annealed OFHC copper is for *thermalization* links, not isolation. Wiring is the big offender: N coax lines × (conduction + attenuator dissipation) is the budget item that limits qubit count in fridges.
- **Radiation:** $\dot Q = \sigma A\, \epsilon_{\text{eff}}\,(T_h^4 - T_c^4)$ — the $T^4$ means the 300 K view is everything: 0.5 W/m² even from 77 K, ~500 W/m² from 300 K. Hence nested shields anchored to each stage and multilayer insulation (each floating layer roughly halves the flow) in the vacuum space. A 1 cm² line-of-sight hole from 300 K to the mixing chamber is a disaster; a hole from 4 K is survivable — always ask *what temperature does this surface see*.
- **Wiring and RF:** every line is a conduction path *and* a Johnson-noise/thermal-photon conduit. Microwave lines carry attenuators distributed over the stages (20 dB at 4 K, 20 at 100 mK, ...) so the *noise temperature* reaching the qubit is that of the last cold attenuator, not 300 K ([[Johnson-Nyquist Noise]] made spatial). The attenuators dissipate — their heat lands on the stage budget. DC lines get RC/copper-powder filters; superconducting NbTi carries signals with negligible thermal conduction.
- **Dissipation on-stage:** amplifiers (HEMTs at 4 K burn mW), resistive joints, eddy currents from pulsed fields — measured against that nW-scale mixing-chamber budget.

**Thermalization is not proximity.** Bolted joints conduct poorly at mK (contact area is microscopic asperities): gold-plate the mating faces, torque properly, add indium or Apiezon-N only where appropriate. And below ~1 K the **electron and phonon baths decouple** ($\dot Q_{e\text{-}ph} \propto T^5$): a chip's electrons can sit at 100 mK in a 10 mK fridge if heat can't leave through the electrons' own wiring — thermalize the *wiring*, not just the substrate. "The thermometer on the plate reads 10 mK" is not the same claim as "the device is at 10 mK"; the device's own noise or population (e.g. residual qubit excited-state population) is the honest thermometer.

**Cryocooler practicalia:** pulse tubes deliver ~1 W at 4 K with ~1–2 Hz vibration (the reason for soft thermal links and vibration-isolated sample mounts in cryo-optics); wet systems trade vibration for He logistics. Thermometry: calibrated RuO₂/Cernox resistors (mind self-heating: excitation power must stay below the local budget), noise thermometry at the bottom end.

> [!question]- Your qubit's measured thermal population implies 60 mK while the mixing-chamber thermometer says 12 mK. Where does the discrepancy usually live?
> The qubit thermalizes to its *electromagnetic environment*, not the copper plate: residual thermal photons coming down insufficiently attenuated (or poorly thermalized) coax set an effective temperature at the qubit frequency — 40 dB of total attenuation anchored at too-warm stages leaves a photon occupation far above the plate temperature. Second suspects: electron-phonon decoupling on chip heated by its own dissipation, and IR leakage (non-hermetic sample box; hence the light-tight cans and Eccosorb filters). The fix is electromagnetic-environment engineering — attenuator placement and thermalization, filtering, shielding — not a colder fridge.

# Connections

- [[Vacuum Engineering]] — the same budget methodology (load vs lift); cryostats are also vacuum systems, and cold surfaces cryopump
- [[Johnson-Nyquist Noise]] — noise temperature and why attenuators are distributed cold
- [[Superconducting Qubits]] — the tenant whose requirements set fridge design
- [[Thermal States]] — photon occupation $\bar n(\omega, T)$: the quantity attenuation chains manage
- [[Quantum Dots]] — the other mK platform, same wiring physics
- [[Grounding and Shielding Practice]] — ground loops and RF hygiene are worse with 3 m of coax per line

---
Source: Pobell, *Matter and Methods at Low Temperatures*; Krinner et al., *EPJ Quantum Technology* 6, 2 (2019) (wiring a dilution fridge for qubits)
