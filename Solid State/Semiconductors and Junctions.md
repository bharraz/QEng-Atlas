#solid-state

**Doping sets the carrier density, and joining p to n creates a built-in field over a depletion region — the one structure behind diodes, photodiodes, solar cells, and the gated interfaces that host quantum dots.** Exponential carrier statistics make all of it strongly bias- and temperature-dependent.

# Reference

**Carrier statistics.** Intrinsic density from thermal activation across the gap:

$$n_i \propto T^{3/2}\, e^{-E_g/2k_BT}, \qquad np = n_i^2 \;(\text{mass action, in equilibrium}).$$

Si at 300 K: $n_i \approx 10^{10}\ \mathrm{cm^{-3}}$ — negligible against any doping. **Donors** (P in Si) donate electrons, $n \approx N_D$; **acceptors** (B) create holes, $p \approx N_A$; typical $10^{15}$–$10^{19}\ \mathrm{cm^{-3}}$. The dopant levels sit meV from the band edges (hydrogenic binding scaled by $m^*/\epsilon_r^2$), fully ionized at 300 K, frozen out at cryogenic temperatures — why bulk CMOS dies below ~40 K ([[Integrated Circuits]]).

**The p–n junction.** Carriers diffuse across, leaving ionized dopants; the resulting **depletion region** and built-in potential self-limit the diffusion:

$$V_{bi} = \frac{k_BT}{e}\ln\frac{N_A N_D}{n_i^2} \;(\approx 0.6\text{–}0.7\ \mathrm{V, Si}), \qquad W = \sqrt{\frac{2\epsilon\, (V_{bi} - V)}{e}\left(\frac{1}{N_A} + \frac{1}{N_D}\right)}.$$

Reverse bias ($V < 0$) widens $W$ and reduces the junction capacitance $C = \epsilon A/W$. Current-voltage:

$$I = I_0\left(e^{eV/k_BT} - 1\right)$$

— forward current grows a decade per 60 mV at 300 K ($k_BT/e = 25.9$ mV); reverse current saturates at $I_0 \propto n_i^2$, the origin of dark current and its exponential temperature dependence.

**Photodiode operation** ([[Photodiode Circuits]]): a photon with $h\nu > E_g$ absorbed in the depletion region creates a pair that the built-in field separates — one electron per photon, responsivity $R = \eta e/h\nu$ ($\approx 0.5$ A/W at 800 nm, $\eta \approx 0.8$). Reverse bias is applied not for gain but for speed: wider $W$ means lower $C$ (faster $RC$), shorter drift time, and more absorption happening in the field region. Large reverse bias → impact ionization → **avalanche** gain (APD; above breakdown, Geiger-mode SPAD — the single-photon detector). Direct-gap materials (GaAs, InGaAs) absorb and emit efficiently; indirect Si needs phonon assistance to emit — why detectors are Si but diode lasers are III-V.

**MOS structure** — metal / oxide / semiconductor, the field-effect element: gate voltage sweeps the surface through **accumulation → depletion → inversion**, where a thin (~nm) layer of minority carriers forms at the interface — a **2DEG**. This is the transistor channel, and at cryogenic temperatures in clean material (Si/SiGe, GaAs/AlGaAs heterostructures — junction-free band-offset versions of the same confinement) it is the electron sea that gate-defined [[Quantum Dots]] are carved from.

> [!question]- Why does cooling a photodiode reduce dark current so dramatically but leave the photocurrent almost unchanged?
> Dark current comes from thermally generated pairs, $I_0 \propto n_i^2 \propto e^{-E_g/k_BT}$ — a Si detector's dark current drops roughly 2× per 8–10 °C. Photocurrent counts absorbed photons, which requires only $h\nu > E_g$; the gap shifts by mere meV over tens of K. Cooling therefore buys SNR exponentially until the readout amplifier, not the diode, sets the floor.

# Connections

- [[Bloch's Theorem and Band Structure]] — the gap, effective mass, and filling this page builds on
- [[Photodiode Circuits]] — the junction as a detector, from the circuit side
- [[Quantum Dots]] — gate-defined dots as depleted 2DEGs
- [[Integrated Circuits]] — the MOSFET; carrier freeze-out at cryo
- [[Electronic Transport]] — mobility and Hall characterization of the doped material

---
Source: Sze & Ng, *Physics of Semiconductor Devices*, Ch. 1–2, 13; Ashcroft & Mermin, *Solid State Physics*, Ch. 28–29
