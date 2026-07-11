#optics

**Split one beam, send it two ways, recombine: output power maps path-length difference to a cosine** — Michelson folds the two paths back on one beamsplitter, Mach-Zehnder uses two beamsplitters and keeps the paths separate.

# Reference

**Michelson:** one beamsplitter, two mirrors, light double-passes each arm.
$$
I_{\rm out} = \frac{I_0}{2}\left[1 + V\cos(2k\,\Delta L)\right]
$$
The 2 in $2k\Delta L$: **one fringe per λ/2 of mirror motion** — fringe counting is displacement metrology (HeNe: 316 nm per fringe). The complementary output goes back toward the source (feedback hazard — isolate the laser).

**Mach-Zehnder:** two beamsplitters, paths recombine once; two accessible output ports with complementary fringes ($I_A + I_B = $ const — energy conservation, and the reason balanced detection works). One fringe per λ of path change. Paths are separate, so you can put a sample, modulator, or atom in one arm without double-passing it.

**Where each is used:** Michelson — FTIR spectrometers (scan arm, FT the interferogram), gravitational-wave detectors, displacement/vibration metrology, white-light zero-path-finding. Mach-Zehnder — EOM-based intensity modulators, phase measurement of samples, the template for atom and photon interferometry.

**Practical:** align for the "flat fringe" (one broad fringe across the output = wavefronts parallel); piezo one mirror and lock mid-fringe for a linear phase→intensity transducer; acoustic/thermal path noise sets the floor — enclose the paths.

> [!question]- Why does a balanced Mach-Zehnder's second output port show fringes exactly complementary to the first?
> Energy conservation plus beamsplitter unitarity: each 50:50 splitter imposes a 90° relative phase between reflection and transmission, so the two ports get $\cos^2$ and $\sin^2$ of the half path phase. Whatever leaves port A missing shows up in port B — subtracting the two doubles signal and cancels common intensity noise.

# Connections

- [[Interference]] — the visibility, coherence, and polarization conditions for any of this to work
- [[Heterodyne Detection]] — offset one arm's frequency (AOM) and the fringe becomes a clean RF beat, immune to slow drift
- [[Beamsplitter Transformation]] — the quantum version: the same port relations applied to mode operators
- [[Electro-Optic Modulator]] — an MZ with an EOM in one arm is the standard integrated intensity modulator

---
Source: Hecht, *Optics*, Ch. 9
