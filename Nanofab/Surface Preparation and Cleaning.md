#nanofab

**Every interface in a device was once an exposed surface and froze in whatever was on it. Each contaminant class has its own removal chemistry, cleans are sequenced so each removes the previous one's residue — and most "materials-limited" coherence numbers are interface numbers set by the last thing that touched the surface.**

# Reference

## Contaminants and their removal

| contaminant | source | removal | note |
|---|---|---|---|
| organics | resist residue, pump oil, ambient (monolayer of adventitious C in minutes) | acetone → IPA → H₂O; piranha (H₂SO₄:H₂O₂); O₂ plasma ash | ash = standard post-develop descum; also fixes non-bonding pads |
| metallic ions | Na⁺, K⁺, transition metals (mobile oxide charge) | RCA: SC-1 (NH₄OH:H₂O₂) then SC-2 (HCl:H₂O₂) | SC-1 removes particles/organics but *deposits* trace metals; SC-2 removes them — ordering is the design |
| native oxide | Si grows 1–2 nm SiO₂ in hours | dilute HF dip | leaves H-terminated, hydrophobic Si (water beads = pass); passivation window minutes–hours — "HF-last" timing is a process parameter |
| particles | handling, drying | megasonic, CO₂ snow, spin-rinse | mostly prevention; uncontrolled drying = watermarks |

Hardened resist (post-RIE, post-implant) resists solvents: O₂ plasma, hot NMP strippers, or piranha (no metals present). Al's native oxide is the counterexample of harnessed surface chemistry: self-limiting 2–3 nm AlOₓ *is* the Josephson tunnel barrier.

## Anneals

- **Forming gas** (H₂/N₂, 350–450 °C): hydrogen passivates Si/SiO₂ dangling bonds — 10–100× interface-trap reduction; the standard last step of CMOS and the routine resurrection of misbehaving oxide devices.
- **UHV anneal**: desorbs water/hydrocarbons — [[Vacuum Engineering|bakeout]] applied to a chip.
- **Activation/repair anneals**: heal implant damage, activate dopants. NV formation: implant, then 800–1200 °C (vacancies mobilize and pair with N), then tri-acid clean + O₂ anneal for oxygen termination.

Desorption and diffusion are Arrhenius, $r \propto e^{-E_a/k_BT}$ with $E_a$ the activation barrier (~0.5–1 eV for physisorbed water, higher for chemisorbed species): at 300 K, $k_BT = 25$ meV sits far below the barrier, so rates are exponentially slow; at 200 °C the same barrier is crossed $10^3$–$10^5\times$ faster. Annealing trades days at 25 °C for minutes hot — and the barrier hierarchy is why a bake removes water but not carbon, and plasma or piranha must handle what heat cannot.

## Why device physics cares

- **Fermi-level pinning**: unpassivated dangling bonds are mid-gap states dense enough to pin the surface potential against any gate — why GaAs surfaces are hostile, why Si (whose oxide passivates) won, and part of why shallow [[Quantum Dots|dots]] and shallow NVs underperform bulk.
- **Two-level systems**: amorphous oxides and adsorbates host tunneling defects that absorb microwave power — the dominant loss/noise mechanism in superconducting resonators at mK; Q improvements in the literature are substantially surface-chemistry results (HF-last substrates, interface-participation engineering).
- **Electric-field noise over electrodes**: adsorbate and patch-potential dynamics drive trapped-ion anomalous heating ($\propto d^{-4}$; [[Noise Spectra and Coupling to Systems]]); in-situ Ar⁺ milling of trap electrodes measurably lowers it. Surface electron spins dephase shallow NVs the same way ([[Magnetism in Solids]]).

> [!question]- Two nominally identical junction runs differ 3× in resistance; same deposition, same oxidation recipe. Where to look first?
> The surface the barrier grew on. Tunneling resistance is exponential in barrier thickness ([[Evanescent Waves]]), so ~1 Å — invisible to any monitor — is a factor 2–3. Residue or adsorbed water on the base electrode changes the effective oxidation; queue time in air, chamber water background, and descum consistency are the suspects. Spread *within* a wafer implicates local cleanliness; spread *between* runs implicates ambient and timing.

# Connections

- [[Etching]] — HF and piranha in their subtractive role
- [[Thin-Film Deposition]] — adhesion and film quality start at the prepared surface
- [[Vacuum Engineering]] — adsorbed water, monolayer time, bakeout
- [[Packaging and Interconnects]] — bondability = cleanliness
- [[NV Centers (atlas)]] — implantation anneals and termination as coherence engineering
- [[Superconducting Qubits]] — TLS loss as interface chemistry
- [[Noise Spectra and Coupling to Systems]] — surface fluctuators as a noise source class

---
Source: Kern, *J. Electrochem. Soc.* 137, 1887 (1990); Reinhold, *Handbook of Silicon Wafer Cleaning Technology*; Hite et al., *Phys. Rev. Lett.* 109, 103001 (2012)
