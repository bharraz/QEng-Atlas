#EnM

**An antenna is an impedance transformer between a circuit and free space** — a conductor sized so that its currents radiate efficiently, which happens when its length is a decent fraction of λ. Nothing decides whether a conductor is an antenna except its length in wavelengths; your cables qualify constantly.

# Reference

**Resonant dipoles:** a center-fed wire resonates when each arm is ~λ/4 (total **λ/2 dipole**: radiation resistance 73 Ω, the reason 50/75 Ω coax exists). A **λ/4 monopole** over a ground plane is half of one — 36 Ω, the whip antenna. Short dipoles ($\ell \ll \lambda$) radiate with $R_{rad} \approx 20\pi^2(\ell/\lambda)^2$ Ω — tiny, hence inefficient but not zero.

**Receiving = transmitting, always:** reciprocity guarantees the same pattern, gain, and impedance both ways. Two working one-liners:
- **Effective length**: $V_{oc} = \ell_{eff}E$ — a λ/2 dipole develops $\ell_{eff} = \lambda/\pi$.
- **Effective aperture**: $P_{rec} = A_{eff}\,S$ with $A_{eff} = G\lambda^2/4\pi$ — even a bare dipole "collects" from an area ~λ²/8, far bigger than the wire.

Gain = directivity × efficiency; a λ/2 dipole has 2.15 dBi with the donut pattern of [[Dipole Radiation]].

**Every cable is an accidental antenna.** A 1 m cable is a fine λ/4 monopole at 75 MHz and resonates again at odd multiples; common-mode current on a shield radiates (and receives) just like a driven wire — the differential signal inside is irrelevant. This is why EMC problems cluster where cable lengths hit λ/4 and λ/2, why a "ground" wire at RF is an antenna and not a ground, and why the fix is choking the common-mode current (ferrite) or filtering at the enclosure boundary rather than "better shielding" of the intended signal.

> [!question]- Your enclosure passes emissions until you attach a 1 m ground strap, then fails around 70–80 MHz. Why that frequency?
> The strap is a λ/4 monopole against the chassis near 75 MHz — resonant, so common-mode noise current drives it efficiently. Shorten it, widen it (lower inductance), or choke the CM current with a ferrite.

# Connections

- [[Dipole Radiation]] — the pattern and ω⁴ physics an antenna is built to exploit
- [[Near and Far Field]] — antenna gain/aperture language only applies in the far zone
- [[Noise Coupling Mechanisms]] — the "radiated" row: cables at λ-scale are the ports
- [[Impedance Matching]] — feeding an antenna is matching Z_ant to the line; mismatched antennas just reflect
- [[Ferrites and Common-Mode Chokes]] — the standard way to de-antenna a cable

---
Source: Pozar, *Microwave Engineering*, Ch. 14 (antennas & receiver front ends); depth: Balanis, *Antenna Theory*
