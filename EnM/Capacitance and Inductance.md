#EnM

**C stores energy in E fields between conductors, L stores it in B fields around currents — and every physical structure has both, whether you put them there or not.** The parasitic values are what bite: about 1 pF per cm of proximity and 1 nH per mm of wire.

# Reference

$$
U_C = \tfrac{1}{2}CV^2, \qquad U_L = \tfrac{1}{2}LI^2
$$

**Geometry lookup:**

| Structure | C | L |
|---|---|---|
| Parallel plate, area $A$, gap $d$ | $\varepsilon_0\varepsilon_r A/d$ | — |
| Coax, radii $a<b$, per length | $\dfrac{2\pi\varepsilon}{\ln(b/a)}$ | $\dfrac{\mu_0}{2\pi}\ln(b/a)$ |
| Solenoid, $n$ turns/m, area $A$, length $\ell$ | — | $\mu_0 n^2 A\ell$ |

Coax sanity check: $\sqrt{L'/C'}=Z_0$ and $1/\sqrt{L'C'}=c/\sqrt{\varepsilon_r}$ — RG-58 is ~100 pF/m and ~250 nH/m.

**Parasitic rules of thumb (the debugging numbers):**
- **~1 pF/cm** between any wire and nearby ground; ~0.5 pF/cm² facing PCB planes; scope probe 10–15 pF; adjacent DIP pins ~0.5 pF
- **~1 nH/mm** of any wire or trace (weak log dependence on thickness); a via ~1 nH; a TO-92 lead ~7 nH
- Consequences: 10 cm of "just a wire" = 100 nH → 63 Ω at 100 MHz — not a short. 1 pF at 1 GHz = 160 Ω — not open. **Every component self-resonates**: a 100 nF cap with 5 nH of lead/via is series-resonant at ~7 MHz and *inductive* above.

Reciprocal geometry: structures with high C per length have low L per length and vice versa — you trade one for the other, which is exactly the $Z_0=\sqrt{L/C}$ knob in [[Transmission Lines]].

> [!question]- Why does a bypass capacitor stop bypassing above a few MHz, and what do you do about it?
> Its lead + via inductance (~few nH) series-resonates with C; above $f=1/2\pi\sqrt{LC}$ the part is an inductor with rising $|Z|$. Fix by minimizing loop inductance (short fat connections, via-in-pad) — not by "bigger capacitor," which resonates *lower*.

# Connections

- [[Transmission Lines]] — distributed L′ and C′ per length are the whole model
- [[Decoupling and Bypassing]] — where the parasitic-inductance fight is fought
- [[LC Resonators]] — intentional L and C; parasitics make unintentional ones everywhere
- [[Complex Impedance]] — the ω-dependence that turns pF and nH into real ohms
- [[Method of Images]] — how wire-over-plane capacitance actually gets computed

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 2.5 & 7.2; parasitics: Ott, *EMC Engineering*
