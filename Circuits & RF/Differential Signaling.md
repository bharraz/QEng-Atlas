#circuits #electronics

**Send the signal as the difference between two symmetric wires routed side by side, so that interference reaching one reaches the other equally: it lands in the [[Common-Mode and Differential-Mode Signals|common mode]] (CM, the pair's shared voltage, as opposed to the differential mode, DM, between the wires), and the receiver's subtraction erases it.** Two wires alone are not enough; what makes it work is the symmetry, which guarantees that pickup is common to both wires.

# Reference

The pair carries $\pm V/2$; the receiver forms $V_+ - V_-$. Rejection requires the pair to be **balanced**: equal impedances from each wire to ground, equal exposure to noise sources.

**Picture:** two wires that pick up the same noise and carry opposite copies of the signal; subtracting them keeps the signal and cancels what they picked up in common.

**Why twisting works:** successive twists reverse the orientation (polarity) of the loop between the two wires, so magnetic (inductive) pickup cancels twist-by-twist; and both wires sit (on average) equidistant from any capacitive aggressor — a nearby conductor whose changing voltage couples in through stray capacitance — so what leaks in leaks in equally, i.e. common-mode. In the coupling-mechanism table on [[Noise Coupling Mechanisms]], twisted pair removes the inductive row and turns the capacitive row into common mode.

**Emissions cancel too:** equal and opposite currents form a tiny magnetic dipole. Quiet in, quiet out.

**Practical notes:**
- Rejection ends where symmetry ends: a filter cap on one line, one wire routed near a chassis, unequal drive impedances → CM→DM conversion.
- The pair still needs a DC common-mode path (receiver bias): something must hold the pair's average voltage inside the receiver's input range, such as a bias network or the driver's own reference. With the pair fully floating, leakage and stray capacitance set that average instead, and because they differ between the two wires, the balance breaks.
- This is why LVDS (low-voltage differential signaling, ~350 mV swings at GHz rates), CAN (the automotive controller-area-network bus), RS-485 (industrial serial links), Ethernet, and XLR audio (balanced microphone cables) all survive cabling environments that would bury a single-ended signal (one wire measured against ground).

> [!question]- Why does twisted pair defeat magnetic pickup that a foil-shielded straight pair does not?
> Foil is an electrostatic shield — nearly useless against low-frequency B fields. Twisting cancels magnetic pickup geometrically: alternating loop polarity sums to ≈0, no shield required.

# Connections

- [[Common-Mode and Differential-Mode Signals]] — the decomposition this scheme is built on
- [[Noise Coupling Mechanisms]] — twisting attacks the inductive row; symmetry converts the rest to CM
- [[Instrumentation Amplifier]] — the receiving end for precision/low-frequency versions
- [[Ground Loops]] — differential links tolerate the ground offsets that single-ended runs turn into signal

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 4
