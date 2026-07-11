#circuits #electronics

**Send the signal as the difference between two symmetric wires: interference hits both wires equally, lands common-mode, and the receiver's subtraction erases it.** The trick isn't the two wires — it's the symmetry that guarantees pickup is common to both.

# Reference

Pair carries $\pm V/2$; receiver forms $V_+ - V_-$. Rejection requires the pair to be **balanced**: equal impedances from each wire to ground, equal exposure to noise sources.

**Why twisting works:** successive twists reverse the loop polarity, so inductive pickup cancels twist-by-twist; and both wires sit (on average) equidistant from any capacitive aggressor, so what leaks in leaks in equally — i.e. common-mode. Twisted pair kills the inductive row of the coupling table and CM-ifies the capacitive row.

**Bonus — emissions cancel too:** equal and opposite currents form a tiny magnetic dipole. Quiet in, quiet out.

**Practical notes:**
- Rejection ends where symmetry ends: a filter cap on one line, one wire routed near a chassis, unequal drive impedances → CM→DM conversion.
- The pair still needs a DC common-mode path (receiver bias); fully floating one side breaks the balance.
- This is why LVDS (~350 mV swings at GHz rates), CAN, RS-485, Ethernet, and XLR audio all survive cabling environments that would bury a single-ended signal.

> [!question]- Why does twisted pair defeat magnetic pickup that a foil-shielded straight pair does not?
> Foil is an electrostatic shield — nearly useless against low-frequency B fields. Twisting cancels magnetic pickup geometrically: alternating loop polarity sums to ≈0, no shield required.

# Connections

- [[Common-Mode and Differential-Mode Signals]] — the decomposition this scheme is built on
- [[Noise Coupling Mechanisms]] — twisting attacks the inductive row; symmetry converts the rest to CM
- [[Instrumentation Amplifier]] — the receiving end for precision/low-frequency versions
- [[Ground Loops]] — differential links tolerate the ground offsets that single-ended runs turn into signal

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 4
