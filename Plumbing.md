#labwork #reference

**A lab fluid system — water cooling loop, N₂ line, compressed air — is the same problem as a circuit: a pressure source (a pump or a pressurized cylinder) drives flow through series resistances (tube, fittings, valves), and the design questions are always "how much flow do I need," "what pressure drop does my plumbing cost," and "will the connections hold."** Pressure plays the role of voltage, flow rate of current, and every tube and fitting is a resistor.

# Reference

## Flow: how much, which regime, what it costs

**How much flow do you need?** For cooling, flow is set by the heat and the temperature rise you'll tolerate:

$$\dot{Q} = \dot{m}\, c_p\, \Delta T \quad\Longrightarrow\quad \text{water: } 1\ \text{L/min carries } \sim 70\ \text{W per °C of rise}.$$

- $\dot Q$ — heat load (W)
- $\dot m$ — mass flow rate (kg/s)
- $c_p$ — specific heat of the coolant (J/g·K): 4.18 for water, among the highest of liquids; 50/50 glycol ~20% less
- $\Delta T$ — coolant temperature rise across the load (°C)

So a 1 kW load at ΔT = 5 °C needs ~3 L/min. This is the first calculation of every cooling design, and usually the only sizing calculation that matters.

**Picture:** the pump curve as a battery with a large internal resistance: the more flow you demand, the less pressure it delivers, and the operating point is where that curve meets your loop's resistance.

**Which regime is the flow in?** The Reynolds number compares inertia to viscosity:

$$\mathrm{Re} = \frac{\rho v d}{\mu} \approx \frac{v\,[\text{m/s}] \cdot d\,[\text{mm}]}{10^{-3}} \;\;(\text{water})$$

- $\rho$ — fluid density; $\mu$ — viscosity
- $v$ — mean flow speed; $d$ — tube inner diameter

Laminar below ~2300, turbulent above ~4000. Lab water loops (m/s in cm tubes) are almost always **turbulent** — which you want: heat transfer to the tube wall is several-fold better because turbulence stirs fluid across the tube instead of letting a stagnant boundary layer insulate the wall. Only microchannels and oil lines are laminar.

**What does the plumbing cost in pressure?** Pressure drop along a pipe (Darcy):

$$\Delta P = f\,\frac{L}{d}\,\frac{\rho v^2}{2},$$

- $L$ — pipe length
- $f$ — friction factor: $64/\mathrm{Re}$ laminar; 0.02–0.04 turbulent, smooth pipe

The two scalings to internalize:
- Turbulent: $\Delta P \propto v^2 \propto \dot{V}^2$, and at fixed flow rate $\Delta P \propto 1/d^5$. **Diameter is everything** — going up one tube size is worth more than any pump upgrade, the same lesson as vacuum conductance ($d^3$ there, $d^5$ here).
- Fittings count as equivalent pipe length, so a run with ten elbows can be mostly elbows:

| Element | Equivalent straight pipe |
|---|---|
| 90° elbow | 30–60 diameters |
| ball valve, open | a few diameters |
| quick-disconnect (its internal poppet valve) | meters of pipe — check its flow coefficient $C_v$ |
| needle valve | enormous — restricting flow is its job |

**Matching pump to system.** A pump delivers less flow the more pressure it must push against (its **pump curve**, from max-flow-at-zero-head down to max-head-at-zero-flow); the plumbing demands more pressure the more flow you force (the **system curve**, $\Delta P \propto \dot{V}^2$). The loop runs where the curves cross; sizing means checking that the crossing sits at your required flow.

| Pump type | Behaviour against back-pressure | Consequence |
|---|---|---|
| **Centrifugal** | flow falls smoothly as pressure rises | gentle; tolerates being briefly run against a closed valve (dead-heading) |
| **Positive-displacement** (gear, diaphragm) | delivers fixed flow *regardless* of back-pressure | will burst something if valved off — always needs a relief valve |

**Bernoulli, for intuition only:** $P + \tfrac12 \rho v^2 + \rho g h = \text{const}$ along a streamline (no friction). Use it for statics — every meter of height is 0.1 bar of water head your pump must lift once (in a closed loop, rising and falling legs cancel; only the *fill* and the *highest point vs pressure rating* care about height) — and for why a constriction reads lower pressure. For everything else, friction dominates and the Darcy relation above is the tool.

## Gas lines vs liquid lines

**Gas is compressible, so it stores energy.** A liquid line at 5 bar holds almost none (water barely compresses); a gas line at 5 bar is a spring, and a burst fitting whips the line and launches parts. This single fact drives gas-side practice:
- regulators rather than valves for pressure control
- relief valves sized for the full source
- every line end secured
- never quick-fit push connections rated for water on high-pressure gas
- a full N₂ cylinder is 200 bar ≈ 9 m³ of expanded gas: treat the cylinder as the energy source it is (chained upright, cap on when unregulated)

**Regulators:**

| Type | Behaviour | Use |
|---|---|---|
| Single-stage | output droops as the cylinder empties (the poppet balance shifts with inlet pressure) | purging |
| **Two-stage** | cascades two pressure drops and holds the outlet steady to the end | anything needing stable pressure (flow controllers, instruments) |

Set pressure *rising* toward the setpoint, since regulators have hysteresis. Flow control is a separate job from pressure control: a needle valve, rotameter, or mass flow controller (MFC) goes downstream of the regulator.

**Nitrogen-specific:** boil-off N₂ from a dewar is clean and dry (dew point ≲ −70 °C); house N₂ may not be. Drying matters because the dew point is the temperature at which line moisture condenses — purging an optical enclosure or a load-lock with gas wetter than the enclosure's coldest surface accomplishes nothing. Asphyxiation is the real N₂ hazard: it displaces O₂ silently; big boil-off consumers in small rooms need O₂ monitors.

## Fittings: what deforms to make the seal

The organizing question: **what deforms to make the seal?** Metal ferrule, tapered thread, elastomer O-ring, or crushed gasket — everything follows from that.

| Fitting | What seals | Typical use | Re-makeable? |
|---|---|---|---|
| **Compression** (Swagelok) | two metal ferrules swaged onto the tube — the ferrule-to-tube bite | the lab standard for metal tube, gas or liquid | yes, with care (ferrules stay on the tube permanently) |
| **Tapered pipe thread** (NPT) | the threads themselves wedge, filled by PTFE tape or pipe dope | threaded ports on pumps, gauges, manifolds | a finite number of times |
| **O-ring fittings** (quick-connects, push-to-connect, KF vacuum flanges, most chiller ports) | an elastomer ring compressed ~25% in a gland; threads or latches only provide the force | anywhere gentle, frequent re-making is wanted | forever, within the elastomer's limits |
| **Barb + clamp** | the soft tube stretched over a barb, held by a clamp | soft tubing (Tygon, silicone) | yes, but joints loosen as the tube creeps |
| **Face-seal** (VCR) | a metal gasket crushed between two polished glands — no elastomer, no permeation, no trapped volume | gas-purity applications; the step up when a Swagelok's tiny leak or outgassing matters | new gasket every make |

**Compression fittings:** install finger-tight, then **1¼ turns** (hard tube; ¾ turn for small/soft). Re-make: snug + slight turn only — the ferrules are already swaged, and re-torquing full turns damages them. The rules that prevent most failures:
- tube bottomed in the fitting before swaging
- never mix brands — Swagelok and Parker ferrule geometries differ subtly and cross-mated joints leak at pressure; pick one ecosystem per system
- never use on glass-hard or badly scratched tube
- brass fittings on copper tube, stainless on stainless (a hard ferrule won't bite a harder tube)

**Tapered thread (NPT):** the threads always leak a little spiral path unless filled — hence **PTFE tape** (2–3 wraps, clockwise viewed from the end so tightening doesn't peel it) or anaerobic pipe dope. Each re-make cuts deeper, so an NPT joint can be remade only a limited number of times. Beware **BSP** (British Standard Pipe, parallel or tapered): nearly identical at a glance, 55° vs 60° flank angle, it mates well enough to seem sealed but never seals. Metric-world equipment (European chillers, for example) often ships BSP.

**O-ring fittings:** limited by the elastomer — temperature, chemical compatibility (EPDM for water — Buna swells; Viton for chemicals/vacuum — but Viton *degrades in hot water*), and permeation (relevant on the [[Vacuum Engineering|vacuum page]]).
- **Quick-disconnects (QDs):** choose **double-shutoff** (both halves valve closed on disconnect) for liquid loops — non-shutoff QDs dump the loop on your optical table. Every QD has a poppet: a real flow restriction (check its $C_v$) and the most common leak point in a water loop as the poppet spring and seal age.
- **Push-to-connect** (John Guest style, for nylon/PU tube): a collet grips, an O-ring seals; fine for low-pressure water and air; the tube must be cut *square* — an angled or scored cut is the standard slow leak.

**Barb + clamp:** the clamp maintains the squeeze — a worm-gear clamp, or better a constant-tension spring or Oetiker ear clamp, which follow the tubing's cold flow. Soft tubing *creeps*: every barbed joint loosens over months, which is why the spring-loaded clamp exists.

**Tubing materials:**

| Material | Use | Watch out for |
|---|---|---|
| Copper | the default for fixed water/gas runs; bendable, solderable | erosion above ~2 m/s (below) |
| Stainless | high pressure, corrosive, or clean gas | — |
| Nylon / polyurethane (PU) | push-to-connect air and N₂ | rated pressure drops sharply with temperature |
| PTFE / PFA (fluoropolymers) | chemicals and anything needing purity | cold-flows in compression fittings — use inserts |
| Tygon / silicone | flexible water connections | permeable to gas, silicone extremely so — never for gas purity |

## Failure modes worth predicting

| Failure | Cause | Prevention |
|---|---|---|
| **Galvanic corrosion** | mixed metals in one water loop (aluminum cold plate + copper fitting) form a battery; the more anodic metal (Al) dissolves | keep loops single-metal-family, or use inhibited coolant and isolate with dielectric fittings; aluminum + plain water is a corrosion problem even alone — inhibitors always |
| **Biological growth** | a warm, dark, stagnant deionized (DI) water loop grows slime that clogs microchannels | additive (inhibitor/biocide), some flow always, no dead legs |
| **Condensation** | coolant below the room's dew point sweats every exposed surface — onto your electronics | stay above dew point (~12–16 °C in typical labs) or insulate *everything* and manage the drips; check dew point before setting a chiller below 15 °C |
| **Water hammer** | slamming a valve on a moving water column converts its momentum to a pressure spike, $\Delta P = \rho c \Delta v$ ($c$ the speed of sound in water: ~15 bar per m/s of stopped flow, acoustic and instant) | slow-acting valves in liquid lines; this is what cracks rotameters and pops QDs |
| **Erosion and noise** | water above ~2 m/s in copper strips the protective oxide (erosion-corrosion) | keep flow speed down — another vote for fatter tube |
| **Freeze** | water expands 9% on freezing | any loop that might see < 0 °C (shipping, a failed HVAC weekend) needs glycol or draining |

**Finding leaks, from cheapest to most sensitive:**
1. soapy water on gas fittings (bubbles)
2. paper towel + flashlight under water fittings
3. pressure-decay test: charge, valve off, watch the gauge — the plumbing version of the vacuum rate-of-rise test
4. helium sniffing, when nothing else finds it

> [!question]- Your new cold plate barely cools even though the chiller is powerful. The loop uses 6 mm tube, four QDs, and ten elbows. Where did the performance go?
> Find where the chiller's pump curve crosses the system curve, $\Delta P_{\text{loop}} = \Delta P_{\text{pump}}$. This loop is nearly all series resistance: $1/d^5$ on narrow tube, four poppeted quick-disconnects (QDs) each worth meters of pipe, plus the elbows. The crossing lands at a fraction of rated flow, and with $\dot Q = \dot m c_p \Delta T$ fixed by the load, low $\dot m$ appears directly as high $\Delta T$. Fixes in order of effect: wider tube (the $d^5$), fewer or full-bore QDs, then a stronger pump. As with vacuum conductance, reduce resistance before buying a bigger source.

# Connections

- [[Vacuum Engineering]] — the same series-conductance triage one regime over; KF/Viton and permeation live there
- [[Complex Impedance]] — the source-and-series-resistance circuit picture, in its native domain
- [[PID Control]] — chillers are thermal control loops; flow is inside their plant
- [[Grounding and Shielding Practice]] — water loops crossing an optical table are also ground-loop and vibration paths

---
Source: White, *Fluid Mechanics*, Ch. 6; Swagelok *Tube Fitter's Manual*; Crane TP-410, *Flow of Fluids Through Valves, Fittings, and Pipe*
