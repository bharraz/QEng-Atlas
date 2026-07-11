#labwork #reference

**Every lab fluid system — water cooling loop, N₂ line, compressed air — is the same problem as a circuit: a pressure source drives flow through series resistances, and the design questions are always "how much flow do I need," "what pressure drop does my plumbing cost," and "will the connections hold."** This page is the working reference: the flow physics at estimation level, then the fittings zoo, then the failure modes.

# Reference

## The flow physics you actually use

**How much flow do you need?** For cooling, flow is set by the heat and the temperature rise you'll tolerate:

$$\dot{Q} = \dot{m}\, c_p\, \Delta T \quad\Longrightarrow\quad \text{water: } 1\ \text{L/min carries } \sim 70\ \text{W per °C of rise}.$$

So a 1 kW load at ΔT = 5 °C needs ~3 L/min. This is the first calculation of every cooling design, and usually the only sizing calculation that matters. (Water's $c_p$ = 4.18 J/g·K is enormous — that's why it's water. A 50/50 glycol mix costs you ~20% of it.)

**Which regime is the flow in?** The Reynolds number:

$$\mathrm{Re} = \frac{\rho v d}{\mu} \approx \frac{v\,[\text{m/s}] \cdot d\,[\text{mm}]}{10^{-3}} \;\;(\text{water})$$

Laminar below ~2300, turbulent above ~4000. Lab water loops (m/s in cm tubes) are almost always **turbulent** — which you want: heat transfer to the tube wall is several-fold better because turbulence stirs fluid across the tube instead of letting a stagnant boundary layer insulate the wall. Only microchannels and oil lines are laminar.

**What does the plumbing cost in pressure?** Pressure drop along a pipe:

$$\Delta P = f\,\frac{L}{d}\,\frac{\rho v^2}{2},$$

with friction factor $f \approx 64/\mathrm{Re}$ (laminar) or $f \approx 0.02$–0.04 (turbulent, smooth pipe). The two scalings to internalize:

- Turbulent: $\Delta P \propto v^2 \propto \dot{V}^2$, and at fixed flow rate $\Delta P \propto 1/d^5$. **Diameter is everything** — going up one tube size is worth more than any pump upgrade, the same lesson as vacuum conductance ($d^3$ there, $d^5$ here).
- Fittings count as equivalent pipe length: a 90° elbow ≈ 30–60 diameters of pipe, a ball valve ≈ few diameters (open), a needle valve ≈ enormous (that's its job). A run with ten elbows can be mostly elbows.

**Matching pump to system.** A pump delivers less flow the more pressure it must push against (its **pump curve**, from max-flow-at-zero-head down to max-head-at-zero-flow); the plumbing demands more pressure the more flow you force (the **system curve**, $\Delta P \propto \dot{V}^2$). The loop runs where the curves cross. Sizing = check the crossing sits at your required flow. Centrifugal pumps are gentle and tolerate dead-heading briefly; positive-displacement (gear, diaphragm) pumps deliver fixed flow *regardless* of back-pressure and will burst something if valved off — they require a relief valve, full stop.

**Bernoulli, for intuition only:** $P + \tfrac12 \rho v^2 + \rho g h = \text{const}$ along a streamline (no friction). Use it for statics — every meter of height is 0.1 bar of water head your pump must lift once (in a closed loop, rising and falling legs cancel; only the *fill* and the *highest point vs pressure rating* care about height) — and for why a constriction reads lower pressure. For everything else, friction dominates and Darcy above is the tool.

## Gas lines vs liquid lines — the one deep difference

Gas is compressible: it stores energy. A liquid line at 5 bar holds almost none (water barely compresses); a gas line at 5 bar is a spring, and a burst fitting whips the line and launches parts. This single fact drives gas-side practice: regulators rather than valves for pressure control, relief valves sized for the full source, secure every line end, and never use quick-fit push connections rated for water on high-pressure gas. A full N₂ cylinder is 200 bar ≈ 9 m³ of expanded gas — treat the cylinder as the energy source it is (chained upright, cap on when unregulated).

**Regulators:** single-stage output droops as the cylinder empties (the poppet balance shifts with inlet pressure); **two-stage** regulators cascade two drops and hold the outlet steady to the end — required for anything needing stable pressure (flow controllers, instruments), overkill for purging. Delivery-side rule: set pressure *rising* toward the setpoint (regulators have hysteresis). Flow control is a separate job from pressure control: needle valve or rotameter or MFC downstream of the regulator.

**Nitrogen-specific:** boil-off N₂ from a dewar is clean and dry (dew point ≲ −70 °C); house N₂ may not be. Drying matters because the dew point is the temperature at which line moisture condenses — purging an optical enclosure or a load-lock with gas wetter than the enclosure's coldest surface accomplishes nothing. Asphyxiation is the real N₂ hazard: it displaces O₂ silently; big boil-off consumers in small rooms need O₂ monitors.

## The fittings zoo — what seals how

The organizing question: **what actually deforms to make the seal?** Metal ferrule, tapered thread, elastomer O-ring, or crushed gasket — everything follows from that.

- **Compression / Swagelok** (the lab standard for metal tube, gas or liquid): two ferrules swage onto the tube as the nut drives them into a taper — the *ferrule-to-tube* bite is the seal, permanent on the tube. Install: finger-tight, then **1¼ turns** (hard tube; ¾ turn for small/soft). Re-make: snug + slight turn only — the ferrules are already swaged, re-torquing full turns damages them. Rules that prevent most failures: tube bottomed in the fitting before swaging; never mix brands (Swagelok/Parker ferrule geometries differ subtly and cross-mating leaks at pressure — pick one ecosystem per system); never use on glass-hard or badly scratched tube; brass fittings on copper tube, SS on SS (a hard ferrule won't bite a harder tube).
- **Tapered pipe thread — NPT** (the threaded ports on pumps, gauges, manifolds): the *threads themselves* wedge and seal, and they always leak a little spiral path unless filled — hence **PTFE tape** (2–3 wraps, clockwise viewed from the end so tightening doesn't peel it) or anaerobic pipe dope. Each re-make cuts deeper; NPT joints have a finite number of lives. Beware **BSP** (British parallel/tapered): nearly identical at a glance, 55° vs 60° flank angle, mates just well enough to leak forever. Metric-world equipment (European chillers!) often ships BSP.
- **O-ring fittings** (quick-connects, push-to-connect, KF, most chiller ports): an elastomer ring compressed ~25% in a gland does the sealing; threads or latches only provide the force. Gentle, re-makeable forever, and limited by the elastomer: temperature, chemical compatibility (EPDM for water — Buna swells; Viton for chemicals/vacuum — but Viton *degrades in hot water*), and permeation (relevant on the [[Vacuum Engineering|vacuum page]]).
    - **Quick-connects/disconnects (QDs):** choose **double-shutoff** (both halves valve closed on disconnect) for liquid loops — non-shutoff QDs dump the loop on your optical table. Every QD has a poppet: a real flow restriction (check its Cv) and the most common leak point in a water loop as the poppet spring and seal age.
    - **Push-to-connect** (John Guest style, for nylon/PU tube): a collet grips, an O-ring seals; fine for low-pressure water and air; the tube must be cut *square* — an angled or scored cut is the standard slow leak.
- **Barb + clamp** (soft tubing: Tygon, silicone): the barb stretches the tube; the clamp (worm-gear, or better, constant-tension spring or Oetiker ear clamp — they follow the tubing's cold flow) maintains the squeeze. Soft tubing *creeps*: every barbed joint loosens over months, which is why the spring-loaded clamp exists.
- **Face-seal / VCR** (gas purity applications): a metal gasket crushed between two polished glands — no elastomer, no permeation, no trapped volume; single-use gasket per make. The step up when a Swagelok's tiny leak or outgassing matters.

**Tubing materials, one line each:** copper — the default for fixed water/gas runs, bendable, solderable; stainless — high pressure, corrosive, or clean gas; nylon/PU — push-to-connect air and N₂ (rated pressure drops sharply with temperature); PTFE/PFA — chemicals and anything needing purity, but cold-flows in compression fittings (use inserts); Tygon/silicone — flexible water connections, permeable to gas (silicone breathtakingly so — never for gas purity).

## Failure modes worth predicting

- **Galvanic corrosion:** mixed metals in one water loop (aluminum cold plate + copper fitting) form a battery; the more anodic metal (Al) dissolves. Keep loops single-metal-family, or use inhibited coolant and isolate with dielectric fittings. Aluminum + plain water is a corrosion project even alone — inhibitors always.
- **Biological growth:** a warm, dark, stagnant DI-water loop grows slime that clogs microchannels. Additive (inhibitor/biocide), some flow always, and avoid dead legs.
- **Condensation:** running coolant below the room's dew point sweats every exposed surface — onto your electronics. Either stay above dew point (~12–16 °C in typical labs) or insulate *everything* and manage the drips. Check dew point before setting a chiller below 15 °C.
- **Water hammer:** slamming a valve on a moving water column converts its momentum to a pressure spike ($\Delta P = \rho c \Delta v$, ~15 bar per m/s of stopped flow — acoustic, instant). Slow-acting valves in liquid lines; this is what cracks rotameters and pops QDs.
- **Erosion & noise:** keep water below ~2 m/s in copper (erosion-corrosion strips the protective oxide above that) — another vote for fatter tube.
- **Freeze:** water expands 9% freezing; any loop that might see < 0 °C (shipping, a failed HVAC weekend) needs glycol or draining.

**Leak-finding, in order of dignity:** soapy water on gas fittings (bubbles), paper towel + flashlight under water fittings, pressure-decay test (charge, valve off, watch the gauge — the plumbing version of the vacuum rate-of-rise test), He sniffing for the desperate.

> [!question]- Your new cold plate barely cools even though the chiller is powerful. The loop uses 6 mm tube, four QDs, and ten elbows. Where did the performance go?
> Run the circuit: the chiller's pump curve crosses the system curve where $\Delta P_{\text{loop}} = \Delta P_{\text{pump}}$, and this loop is nearly all series resistance — $1/d^5$ on skinny tube, four poppeted QDs each worth meters of pipe, elbows worth another few meters. The crossing lands at a fraction of rated flow; with $\dot Q = \dot m c_p \Delta T$ fixed by the load, low $\dot m$ shows up directly as high $\Delta T$. Fixes in effectiveness order: fatter tube (the $d^5$), fewer/full-bore QDs, then a stronger pump last — same triage as the vacuum page: reduce the resistance before buying a bigger source.

# Connections

- [[Vacuum Engineering]] — the same series-conductance triage one regime over; KF/Viton and permeation live there
- [[Complex Impedance]] — the source-and-series-resistance circuit picture, in its native domain
- [[PID Control]] — chillers are thermal control loops; flow is inside their plant
- [[Grounding and Shielding Practice]] — water loops crossing an optical table are also ground-loop and vibration paths

---
Source: White, *Fluid Mechanics*, Ch. 6; Swagelok *Tube Fitter's Manual*; Crane TP-410, *Flow of Fluids Through Valves, Fittings, and Pipe*
