#reference #math

**Mathematical problem-solving is a procedure, not an inspiration.** Pólya's four phases and Mason–Burton–Stacey's Entry/Attack/Review are the same procedure at different resolutions; the nine moves below are stated with instances from this vault.

The two frameworks, for orientation: Pólya = *understand → plan → carry out → look back*. Mason–Burton–Stacey = *Entry (know/want/introduce) → Attack (conjecture/justify) → Review (check/reflect/extend)*, with **specializing** and **generalizing** as the two engines and **STUCK!** treated as a normal state rather than a failure.

# Reference

## 1. Entry: what do I KNOW, what do I WANT, what can I INTRODUCE?

Write all three down explicitly before manipulating anything. Most failed attempts are attempts on the wrong question.

- **KNOW** — the given data, and the *conditions* linking them. A condition you have not written down is a condition you will forget to use.
- **WANT** — the unknown, stated as an object with a type: a number, a function, a bound, a proof, a counterexample. "Show that…" and "find all…" demand different work.
- **INTRODUCE** — notation, a figure, an auxiliary object. Bad notation is the most common self-inflicted obstacle; index conventions and factor-of-two conventions especially ([[Conventions and Factor-of-Two Traps]]).
- Restate the problem in your own words. If you cannot, you have not understood it yet.

## 2. Specialize

**The single most reliable move when stuck.** Replace the general problem with the smallest instance that is still interesting, solve that, and look at what made it work.

- Set $n = 0, 1, 2$. One mode before $n$ modes; two ions before a chain; $\mathfrak{su}(2)$ before a general semisimple algebra ([[Cartan Subalgebras, Roots, and Weights]]).
- Take a limit where a parameter vanishes or diverges: $\hbar \to 0$, $\omega \to \infty$, zero detuning, zero temperature.
- Try extreme or degenerate cases — they are where a wrong general claim breaks first.
- Specialize *randomly* as a check, *systematically* to see a pattern. Both are useful and they are different activities.

## 3. Generalize

Ask what the special case depended on, and drop everything it did not.

- **The inventor's paradox** (Pólya): the more ambitious problem is sometimes easier, because the general structure is visible where the special case looks like a coincidence. [[Sturm-Liouville Theory]] is the standard demonstration — proving orthogonality once for self-adjoint operators is easier than proving it separately for Legendre, Hermite, Laguerre and Bessel.
- Generalizing is how you tell a *coincidence* from a *mechanism*. If a result survives dropping a hypothesis, that hypothesis was decoration.
- Watch for over-generalization: check the new claim against the old special case before trusting it.
- The vault is full of this move already performed: [[Bilinear Forms and Preserved Structures]] generalizes $O(n)$, $U(n)$ and $Sp(2n)$ to "preserve a form"; [[Operators and Superoperators]] generalizes matrices to linear maps at any rung.

## 4. Conjecture, then attack your own conjecture

Say what you think is true, in a sentence sharp enough to be wrong.

- Formulate → test on cases → **try to break it** → repair or replace. The cycle is the work; a conjecture you have not tried to falsify is not evidence.
- Keep a written record of conjectures with their status. Vague memory of "I think I checked that" is how errors survive.
- **Three levels of conviction** (Mason–Burton–Stacey): convince *yourself*, convince a *friend*, convince a *skeptic*. Only the third is a proof, and knowing which level you are at prevents both sloppiness and paralysis.
- Ask "**but why?**" at each step until the answer is a reason rather than a manipulation.

## 5. Audit necessary vs. sufficient

The most common silent error is proving one direction and using the other.

- $A \Rightarrow B$: $A$ is **sufficient** for $B$; $B$ is **necessary** for $A$.
- The **contrapositive** $\neg B \Rightarrow \neg A$ is equivalent. The **converse** $B \Rightarrow A$ is not — assuming it is, is the error.
- One counterexample destroys a universal claim; one example establishes an existential one. Know which you have.
- **Quantifier order is not decoration:** $\forall \epsilon\, \exists N$ (pointwise) and $\exists N\, \forall \epsilon$ (uniform) are different theorems, and the gap between them is where convergence proofs live.
- Beware **vacuous truth** — a statement about an empty set is true and tells you nothing.

Instances worth having straight, all from this vault:

| Claim | Status | The trap |
|---|---|---|
| Dimensional consistency ⇒ correct | **necessary, not sufficient** | passes dimensions, wrong by a factor ([[Units and Dimensional Analysis]]) |
| Eigenvalues in the left half-plane ⇒ stable | necessary and sufficient for *asymptotic* decay | **not** sufficient for bounded transients when non-normal ([[Matrix Decompositions in Practice]]) |
| Hermitian ⇒ valid observable | **necessary, not sufficient** | self-adjointness also needs matching domains ([[Operators and Superoperators]]) |
| $[A,B] = 0$ ⇒ common eigenbasis | necessary **and** sufficient (normal operators) | a genuine iff — use it in both directions ([[Simultaneous Diagonalization]]) |
| Subalgebra ⇒ quotient exists | **necessary, not sufficient** | needs an ideal ([[Subalgebras, Ideals, and Quotients]]) |
| Nilpotent ⇒ solvable | true; converse **false** | solvable buys quadratures, only nilpotent buys termination |
| Finite variance ⇒ CLT applies | **necessary** | Lorentzian tails have none, and averaging fails ([[Central Limit Theorem]]) |
| Algebra closes ⇒ exactly solvable | **sufficient, not necessary** | a conserved quantity can rescue a non-closing case ([[Universal Enveloping Algebra and PBW Basis]]) |

## 6. Work backwards, and vary the problem

If forward progress stalls, start from the goal and ask what would suffice to reach it.

- **Work backwards:** assume the result; what would immediately give it? Then treat *that* as the new target. Standard in existence proofs and in control design ("assume the algebra closes — what must the generators be?").
- **Drop a condition** and see which conclusion survives; the discarded condition's role becomes visible.
- **Vary the problem** — Pólya's list, still the best inventory:

| Move | Question |
|---|---|
| Analogy | What problem with a similar *structure* have I solved? |
| Auxiliary element | What can I add — a term, a mode, a dimension, a $0 = x - x$? |
| Decompose | Can I split it into parts and recombine? |
| Restate | Can I say it in a different language — matrix, operator, geometric, probabilistic? |
| Related problem | Have I seen the same *unknown* before, in another setting? |
| Reverse | Can I solve the inverse problem instead? |

- Changing representation is often the whole solution: to an eigenbasis, to the frequency domain, to a rotating frame, to phase space ([[Fourier Transform]], [[Conjugation]]).

## 7. Get stuck productively

Being stuck is a state to be recorded, not an emotion to be pushed through.

- **Write "STUCK!" and finish the sentence:** *I am stuck because I don't know how to…* / *because I can't see why…* / *because I don't know what X means.* Naming the obstacle usually converts it into a smaller answerable question.
- Distinguish the three causes: a missing **fact**, a missing **technique**, or a misunderstood **question**. They have different remedies, and the third is the most common.
- Go back to move 2 and specialize harder. Almost always available.
- **AHA!** deserves the same treatment — write down the insight *and what triggered it* before continuing, because you will need the trigger again more than the insight.

## 8. Review: check by other means

Do not accept a result that you have only derived once.

- **Dimensions** first, always ([[Units and Dimensional Analysis]]).
- **Limits and special cases:** does it reduce to the known answer at $n=0$, $t=0$, zero coupling, high temperature?
- **Symmetry:** is the answer as symmetric as the problem? A result less symmetric than its inputs is usually wrong.
- **Order of magnitude:** put in real numbers and see whether the size is physical.
- **Signs and factors of two** — the most frequent errors, and the least interesting ([[Conventions and Factor-of-Two Traps]]).
- **Derive it a second way.** Two independent routes agreeing is worth more than either route checked twice.

## 9. Extend: keep the method, not just the answer

Pólya's fourth phase, and the one that compounds.

- Ask what *else* the method solves. A technique is worth more than a result, which is the reason [[Sturm-Liouville Theory]] and [[Bilinear Forms and Preserved Structures]] are single pages covering many families.
- Ask what happens if you change a hypothesis — the next problem is usually adjacent.
- Record the *move* that worked, not only the outcome. "Specializing to one mode exposed the structure" is reusable; the final formula often is not.

> [!question]- You have a general result you cannot verify and no obvious way in. Which moves, in what order?
> Specialize (2) to the smallest interesting case and check the result there — this both tests it and often reveals the mechanism. Then run the review battery (8): dimensions, limits, symmetry, magnitude. If it survives, audit necessary vs. sufficient (5) to confirm you proved the direction you are using. If it fails, the failing special case is your counterexample.

# Connections

- [[(Guide) Debugging Method]] — the same procedural stance applied to apparatus rather than arguments
- [[Units and Dimensional Analysis]] — move 8's first check, and move 5's canonical necessary-not-sufficient case
- [[Conventions and Factor-of-Two Traps]] — move 1's notation discipline and move 8's most common error
- [[Sturm-Liouville Theory]] — the inventor's paradox in finished form: generalize once, apply to every family
- [[Bilinear Forms and Preserved Structures]] — generalization as a page: one construction, all the classical groups
- [[Subalgebras, Ideals, and Quotients]] — necessary vs. sufficient with real consequences for truncation
- [[Central Limit Theorem]] — a necessary hypothesis (finite variance) whose failure is easy to miss
- [[Taylor Expansion]] — specializing to leading order, the most-used instance of move 2

---
Source: G. Pólya, *How to Solve It* (Princeton, 1945); J. Mason, L. Burton & K. Stacey, *Thinking Mathematically*, 2nd ed. (Pearson, 2010)
