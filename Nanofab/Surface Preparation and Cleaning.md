#nanofab

**Every interface in a device was once an exposed surface, and it froze in whatever was on it at that moment — so cleaning isn't janitorial, it's interface engineering. The contaminants have a hierarchy (organics, metals, native oxide, adsorbed water), each with its own removal chemistry, and the order of operations matters because some cleans deposit what others remove.** This is also where device physics meets fab: surface states, two-level systems, and electric-field noise are all chemistry that didn't get cleaned.

# Reference

**The contaminant taxonomy and its removal map:**

- **Organics** (resist residue, pump oil, skin, ambient hydrocarbons — a surface left in room air grows a monolayer of adventitious carbon in minutes): solvents (acetone → IPA → water; acetone *last* leaves residue — always chase it), **piranha** (H₂SO₄:H₂O₂, oxidizes everything organic; violent, self-heating), or **O₂ plasma ashing** (dry, gentle, the standard post-develop "descum" — also the fix when [[Packaging and Interconnects|wirebonds]] won't stick).
- **Metallic ions** (Na⁺, K⁺, transition metals — mobile charge that drifts in oxides and shifts thresholds): acidic peroxide chemistry; this is why the CMOS world runs **RCA**: SC-1 (NH₄OH:H₂O₂ — particles and organics, but *deposits* trace metals) then SC-2 (HCl:H₂O₂ — strips the metals SC-1 left). The ordering is the lesson: each clean has a residue profile, and sequences are designed so the next step removes the previous step's byproduct.
- **Native oxide** (Si grows ~1–2 nm of SiO₂ in air within hours — an unavoidable, low-quality dielectric): dilute **HF dip**, which also leaves Si **H-terminated** — hydrophobic (water beads: the classic pass/fail test) and passivated for minutes-to-hours, the window in which epitaxy, junction deposition, or bonding must happen. "HF-last" timing is a real process parameter. (Al's native oxide, by contrast, is self-limiting at ~2–3 nm and *is the tunnel barrier* in every AlOₓ Josephson junction — the same chemistry, harnessed instead of fought.)
- **Particles**: megasonic baths, CO₂ snow, spin-rinse; in practice, mostly *prevention* — laminar flow, never letting a wet surface dry uncontrolled (drying watermarks are dissolved residue).

**Resist stripping deserves its own line** because it's the most common failure: hard-baked or ion-hardened resist (post-RIE, post-implant) laughs at acetone — the crosslinked crust needs O₂ plasma, NMP-type strippers hot, or piranha (if no metals present). "It measured fine before I stripped resist" usually means the strip attacked the device, not that stripping was optional.

**Anneals — cleaning's high-temperature sibling**, fixing what chemistry can't reach: **forming gas** (H₂/N₂, 350–450 °C) passivates Si/SiO₂ interface dangling bonds with hydrogen (10–100× interface-trap reduction — the standard last step of CMOS and a routine resurrection for misbehaving oxide devices); UHV anneals desorb water and hydrocarbons ([[Vacuum Engineering|bakeout]] logic applied to a chip); high-T anneals in controlled atmosphere heal implant damage and activate dopants — and for NV centers, the 400–1200 °C anneal sequence after implantation is what mobilizes vacancies to form the centers and repairs the lattice around them, followed by tri-acid cleaning and O₂ anneal to set an oxygen termination.

**Why the device physics cares** (the payoff section):

- **Surface Fermi-level pinning:** unpassivated dangling bonds are mid-gap states dense enough to pin the surface potential regardless of gating — the reason GaAs surfaces are hostile, why Si won (its oxide passivates), and a chunk of why shallow [[Quantum Dots|dots]] and shallow NVs underperform bulk ones.
- **Two-level systems (TLS):** amorphous oxides and adsorbed contamination host tunneling defects that absorb microwave energy — the dominant loss and noise mechanism in superconducting resonators and qubits at mK. The literature's Q improvements are substantially *surface-chemistry* papers (substrate HF treatment, interface-participation engineering).
- **Electric-field noise over surfaces:** patch potentials and adsorbate dynamics on trap electrodes drive anomalous heating of trapped ions ($\propto d^{-4}$ in ion-electrode distance); in-situ ion milling or plasma treatment of trap surfaces measurably lowers it. Same story for NV dephasing from surface spins ([[Magnetism in Solids]]).

The unifying claim: **a "materials-limited" coherence number is usually an interface-limited number**, and the interface is set by the last thing that touched the surface and the first thing deposited on it.

> [!question]- Two nominally identical Josephson-junction runs differ 3× in resistance. Same deposition, same oxidation recipe. Where do you look first?
> Upstream, at the surface the barrier grew on. Junction resistance is exponential in barrier thickness ([[Evanescent Waves|tunneling]]), so ~1 Å of difference is a factor of ~2–3 — far below any deposition monitor's visibility. Resist residue or adsorbed water on the base electrode changes the effective oxidation (thickness *and* barrier height); time-in-air between base layer and oxidation, chamber water background, and the descum step's consistency are the usual suspects. The tell that it's surface chemistry rather than the oxidation recipe: the spread *within* a wafer (local cleanliness) versus *between* runs (ambient/timing). Junction fabs obsess over descum recipes and queue times for exactly this reason.

# Connections

- [[Etching]] — wet chemistry's other job; HF and piranha reappear here as cleans
- [[Thin-Film Deposition]] — adhesion and film quality start at the prepared surface
- [[Vacuum Engineering]] — adsorbed water and monolayer time; bakeout as a clean
- [[Packaging and Interconnects]] — bondability is surface cleanliness
- [[NV Centers (atlas)]] — implantation anneals and surface termination as coherence engineering
- [[Superconducting Qubits]] — TLS loss as interface chemistry
- [[Paul Traps]] — anomalous heating and electrode surface treatment

---
Source: Kern, "The evolution of silicon wafer cleaning technology," *J. Electrochem. Soc.* 137, 1887 (1990); Reinhold, *Handbook of Silicon Wafer Cleaning Technology*; Müller, Cappellaro et al. reviews on NV surface engineering; Hite et al., *Phys. Rev. Lett.* 109, 103001 (2012) (ion-trap surface treatment)
