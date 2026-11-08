#labwork #reference

**Most lab hardware is damaged by handling rather than by use: a fingerprint on a mirror coating absorbs light and burns, a static spark from a sleeve destroys a laser diode, a speck of dust on a fiber connector melts into the core, a cable bent once too sharply changes its impedance for good.** Each of these has a specific mechanism, so each precaution follows from it rather than from habit.

# Reference

**Optics** (mirrors, lenses, waveplates, crystals):

| Precaution | Mechanism it prevents |
|---|---|
| hold by the edges, with gloves | skin oil and salt leave absorbing, scattering films; on high-reflectivity coatings the absorbed spot heats and damages the coating |
| never wipe a dry optic | dust grains are harder than many coatings and scratch when dragged; blow off loose dust first, then clean wet ([[Chemical Cleaning]]) |
| clean only when contamination is visible or measured | every cleaning risks a scratch or a residue streak |
| never touch gratings or pellicles | grating grooves are a fragile replicated layer; pellicles are micrometre-thin membranes — blow them off only |
| tighten mounts only until the optic does not move | clamping stress adds birefringence ([[Birefringence]]) and distorts mirror surfaces |
| keep hygroscopic crystals dry (BBO, KDP, some fluorides) | they absorb water and fog or crack |
| treat bare metal mirrors (gold, silver, aluminium without overcoat) as unwipeable | the metal is soft and scratches at the first touch |

**Picture:** the most delicate part of an optical or electronic component is a surface or junction a few micrometres thick, and handling is the main thing that reaches it.

**Fibers:** the light travels in a core a few micrometres across, so a particle the size of the core blocks the mode, and at high power it absorbs and burns into the end face. Keep connectors capped, inspect the end face with a fiber microscope before mating, and clean only with the methods made for connectors. Never mate an angled (APC) connector to a flat (PC) one: the air gap costs most of the light and can chip both faces ([[Optical Fibers and Fiber Coupling]]). Bends tighter than the specified radius leak light, and in polarization-maintaining fiber they also degrade the polarization.

**Laser diodes and tapered amplifiers:** a diode junction is destroyed by a reverse voltage of a few volts or by a current spike lasting nanoseconds — exactly what a static discharge from a person (kilovolts) or a hot-plugged cable delivers.

- Keep the leads shorted until the diode is installed, and wear a grounded wrist strap.
- Set the current to zero before connecting or disconnecting anything, and use drivers with a slow start and a shorting relay.
- Never run a tapered amplifier without its seed beam ([[Laser Sources]]).

**Detectors:** a photomultiplier left biased in room light, or an avalanche photodiode hit by a bright pulse, is damaged or permanently degraded; switch off or shutter them before opening an enclosure ([[Photon Detectors]]).

**RF and electronics:**

| Precaution | Mechanism |
|---|---|
| check the maximum input power of spectrum analyzers and 50 Ω scope inputs; add attenuators | their input mixers and terminations burn out at levels a lab amplifier easily exceeds |
| connect the load before turning on an RF amplifier | an open or shorted output reflects the power back into the amplifier |
| tighten SMA connectors to their specified torque | over-tightening deforms the centre pin and dielectric; under-tightening makes an intermittent, lossy joint ([[Cable Care and Connectors]]) |
| discharge high-voltage supplies before touching | PMT supplies, ion-pump controllers (kV), piezo and EOM drivers (hundreds of V) store charge |

**Vacuum parts:** fingerprints and skin oils outgas hydrocarbons and water and survive a bakeout, so everything that goes inside a vacuum system is handled with clean, powder-free gloves and wrapped in oil-free foil ([[Vacuum Engineering]]). The knife edges of CF (ConFlat) flanges make the seal by cutting into a copper gasket, so a scratched edge leaks: cap flanges whenever they are open, and use a new gasket every time. Viewports and other glass-to-metal joints crack under fast temperature changes, so bakes are ramped slowly.

**Lasers — safety notes:**

- Keep beams horizontal and below eye level, and never bring your eye to beam height.
- Terminate every beam and every stray reflection with a beam block. The rejected port of a polarizer, an AOM's zeroth order, and the reflection from a tilted window are the ones that get missed.
- Remove reflective watches and rings before aligning.
- Infrared and ultraviolet beams are invisible: find them with viewer cards or cameras.
- Wear eyewear rated for the wavelength and power whenever beams are open, and align at reduced power.

**Cryogens and magnets — safety notes:**

- Liquid nitrogen and helium boil into large volumes of gas, which displaces oxygen in small rooms ([[Plumbing]]) and bursts sealed containers. Never close a dewar that has no pressure relief.
- Splashes cause cold burns: wear a face shield when pouring.
- Isolator and ion-pump magnets pull steel tools from a distance, and their fields shift nearby Zeeman levels and PMT gain.

**What each check tells you:**

| Check | What it tells you |
|---|---|
| fiber end face under a fiber microscope | dirt, scratches, or burn pits in the core region, before mating spreads them |
| optic under a bright light at grazing incidence (dark-field) | dust, scratches, and residue films invisible face-on |
| power before and after an optic | its actual loss, compared with the specification |
| cavity ring-down or finesse over time | contamination of high-reflectivity mirrors, which shows here long before it is visible |
| diode laser threshold current over time | degradation: a rising threshold means the diode is ageing or was damaged |

> [!question]- Why does a fingerprint matter far more on a high-reflectivity cavity mirror than on a lens?
> A lens loses the absorbed or scattered fraction once. In a cavity the light passes the mirror on every round trip, and finesse is set by the total loss per round trip, $\mathcal F \approx \pi/(1-R)$ ([[Fabry-Perot Cavity]]). A film adding 100 ppm of loss to a mirror whose transmission is 10 ppm cuts the finesse about tenfold, and the circulating power, enhanced by $\sim\mathcal F/\pi$, heats the contaminated spot until the coating is damaged.

# Connections

- [[Chemical Cleaning]] — what the solvents and acids do when an optic or part must be cleaned
- [[Cable Care and Connectors]] — coax and connector handling in detail
- [[Optical Fibers and Fiber Coupling]] — connectors, bend loss, and coupling
- [[Laser Sources]] — what each laser and amplifier type tolerates
- [[Photon Detectors]] — light damage in detectors
- [[Vacuum Engineering]] — why handling sets the base pressure
- [[Cryogenics]] — cryogen handling and thermal cycling
- [[Plumbing]] — gas lines and the nitrogen asphyxiation hazard
- [[Birefringence]] — the stress birefringence that overtightened mounts create
- [[Fabry-Perot Cavity]] — why mirror loss and finesse are tied together
- [[Magnetic Field Coils and Shielding]] — handling and degaussing magnetic shields

---
Source: J. H. Moore, C. C. Davis & M. A. Coplan, *Building Scientific Apparatus*, 4th ed. (Cambridge, 2009); ANSI Z136.1, *Safe Use of Lasers*
