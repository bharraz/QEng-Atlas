#quantum-info

**Read out an eigenvalue phase digit-by-digit: controlled powers of $U$ kick binary multiples of the phase onto an ancilla register, and the inverse QFT converts them to a readable bit string.** This is the primitive under Shor and quantum chemistry.

# Reference

Given $U|u\rangle = e^{2\pi i \varphi}|u\rangle$, estimate $\varphi$ to $t$ bits:

1. $t$ ancillas in $|+\rangle^{\otimes t}$; system in $|u\rangle$.
2. Controlled-$U^{2^k}$ from ancilla $k$: phase kickback writes $e^{2\pi i \varphi 2^k}$ onto each — the register now holds $\frac{1}{\sqrt{2^t}}\sum_j e^{2\pi i \varphi j}|j\rangle$, a Fourier mode at frequency $\varphi$.
3. Inverse QFT → measure → the binary expansion $\varphi \approx 0.\varphi_1\varphi_2\dots\varphi_t$.

**Precision**: $t$ ancillas → error $2^{-t}$, i.e. precision scales *exponentially* in ancilla count but *linearly* in total $U$-applications ($2^t$ of them — Heisenberg-limited in runtime). Non-dyadic $\varphi$ succeeds with prob $\ge 4/\pi^2$; pad a few extra ancillas to boost.

**Superposition input**: feeding $\sum_u c_u|u\rangle$ samples eigenvalue $\varphi_u$ with probability $|c_u|^2$ *and projects the register onto that eigenstate* — this is how chemistry ground-state energy estimation works (prepare a decent ansatz, measure, get $E_0$ with prob $|\langle u_0|\psi\rangle|^2$). Shor is QPE on modular multiplication, where $\varphi$ encodes the period.

**Practical catch**: you need controlled-$U^{2^k}$ efficiently — fine for modular arithmetic, expensive for $e^{-iHt}$ (Trotter error and depth eat the precision budget).

> [!question]- Why does measuring the *ancillas* leave the *system* in an eigenstate?
> The kickback correlates ancilla frequency with eigenvalue: the joint state is $\sum_u c_u |\text{freq } \varphi_u\rangle|u\rangle$. Reading the frequency register is a projective measurement in the eigenbasis, executed without ever measuring the system directly.

# Connections

- [[Quantum Fourier Transform]] — the readout stage
- [[Phase Kickback]] — the write stage
- [[Canonical Quantum Algorithms]] — Shor is this plus classical number theory
- [[Trotterization]] — how $U = e^{-iHt}$ gets implemented for chemistry

---
Source: Nielsen & Chuang, Ch. 5.2
