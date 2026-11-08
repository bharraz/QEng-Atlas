#math

**An asymptotic series gets more accurate as the parameter gets more extreme and worse as you keep more terms — and dominant balance is the method of guessing which two terms in an equation are the large ones and checking afterwards.**

# Reference

$$f(x) \sim \sum_{n=0}^{N} a_n x^{n} \quad (x\to 0) \qquad\text{means}\qquad \left| f(x) - \sum_{n=0}^{N} a_n x^n \right| = O(x^{N+1})$$

**Picture:** a sequence of approximations that first homes in on the answer and then wanders off; the best place to stop is near the smallest term, and the more extreme the parameter, the closer it gets before turning away.

**The limit taken is in $x$, not in $N$.** A convergent series improves as you add terms at fixed $x$; an asymptotic series improves as $x\to 0$ at fixed $N$. Most asymptotic series *diverge* for every $x$, and are still the more useful object.

| | Convergent | Asymptotic |
|---|---|---|
| Improve by | adding terms | making the parameter more extreme |
| Terms $\to\infty$ | converges to $f$ | diverges |
| Best accuracy | exact | **optimal truncation** |

**Optimal truncation.** Terms shrink, reach a minimum, then grow. Stop at the smallest term; the error is roughly the size of the first omitted term. For a series whose terms go like $n!\,x^n$ the minimum is near $N \approx 1/x$, and the accuracy floor is $\sim e^{-1/x}$ — **exponentially small but not zero**. That floor is where the physics you dropped lives: tunneling amplitudes, Stokes phenomena, and above-barrier reflection are all $e^{-1/\hbar}$-type effects invisible to every order of the series ([[WKB Approximation]]).

Perturbation theory in QED, QCD, and quantum mechanics is asymptotic, not convergent. "Higher order" stops helping past a point, and the practical question is always *where the minimum term is*, not how many orders you can compute.

## Dominant balance

The standard method for equations with no closed-form solution. The procedure:

1. **Guess** which two (occasionally more) terms are the largest.
2. **Solve** the reduced equation keeping only those.
3. **Check** the discarded terms are genuinely smaller under that solution. If not, the guess was wrong — try a different pair.

There are only a few pairings to try, so this is a short search rather than an art. Worked instance, $\epsilon y'' + y' + y = 0$ with $\epsilon \to 0$:

| Balance | Reduced equation | Solution | Verdict |
|---|---|---|---|
| $y' \sim -y$ | $y' + y = 0$ | $y \sim e^{-x}$ | consistent where $y''$ stays small — the **outer** solution |
| $\epsilon y'' \sim -y'$ | $\epsilon y'' + y' = 0$ | $y \sim e^{-x/\epsilon}$ | varies on scale $\epsilon$ — the **inner** (boundary-layer) solution |

**Regular vs. singular perturbation** is exactly whether setting $\epsilon = 0$ changes the *character* of the problem:

- **Regular** — expand $y = y_0 + \epsilon y_1 + \cdots$ and it works. The $\epsilon\to 0$ solution is close to the $\epsilon$ solution everywhere.
- **Singular** — setting $\epsilon = 0$ lowers the order of the ODE (or removes the highest derivative), so a solution is lost and the expansion fails in a thin region. The lost solution reappears on a **rescaled** variable.

**The rescaling is the method.** Set $X = x/\delta(\epsilon)$ and choose $\delta$ so that a new balance becomes possible — here $\delta = \epsilon$, giving the boundary layer of thickness $\epsilon$. Then **match**: the outer limit of the inner solution must equal the inner limit of the outer solution, which fixes the constants and glues them into a uniform approximation. This is *matched asymptotic expansions*.

Physical instances of the same structure: viscous boundary layers, the [[WKB Approximation]] near turning points, and any problem with a small parameter multiplying the highest derivative — including $\hbar$ in the Schrödinger equation.

## Where the small parameter comes from

Non-dimensionalize first; the small parameter should be a **ratio of scales**, not a dimensional quantity, or "small" is not a statement ([[Units and Dimensional Analysis]]). Rydberg's $\Gamma/\Delta$, the Lamb–Dicke $\eta$, $\hbar\omega/k_BT$, and the Magnus convergence ratio are all of this kind.

> [!question]- You compute three more orders of perturbation theory and the answer gets worse. Is the calculation wrong?
> Probably not — the series is asymptotic and you have passed the smallest term. Beyond optimal truncation the terms grow and accuracy degrades. The remaining error is exponentially small in the parameter, so no further order will reach it: it is non-perturbative, and needs a different method.

# Connections

- [[Taylor Expansion]] — the convergent case, and the contrast that defines this one
- [[WKB Approximation]] — an asymptotic expansion in $\hbar$, with turning points as its boundary layers
- [[Stationary Phase and Steepest Descent]] — how the coefficients of these series are generated
- [[Magnus Expansion]] — a series with a genuine convergence radius, unlike Dyson
- [[Units and Dimensional Analysis]] — non-dimensionalizing to find what is small
- [[(Guide) Thinking Mathematically]] — dominant balance as a specialize-then-check move
- [[Time-Independent Perturbation Theory]] — the physics series that is asymptotic in practice

---
Source: Bender & Orszag, *Advanced Mathematical Methods for Scientists and Engineers*, Ch. 3, 7, 9–10; Hinch, *Perturbation Methods*, Ch. 1–5
