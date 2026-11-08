#numerics #statistics #math

**Choosing what to minimize is a modelling decision, not a given — and the choice of loss is exactly the choice of a noise model, while the choice of regularizer is exactly the choice of a prior.**

The algorithms that do the minimizing are on [[Optimization and Curve Fitting]]; choosing what to minimize comes first.

# Reference

## Loss: choosing it chooses a noise model

Minimizing a loss is maximizing a likelihood. For residuals $r_i$, $\;\min\sum \rho(r_i) \iff \max \prod e^{-\rho(r_i)}$, so **each loss is a statement about how errors are distributed**:

| Loss $\rho(r)$ | Implied noise | Behaviour | Use when |
|---|---|---|---|
| $r^2$ (L2, least squares) | Gaussian | smooth; a single outlier can dominate, since it enters squared | errors genuinely Gaussian ([[Least Squares and Chi-Squared Fitting]]) |
| $\lvert r\rvert$ (L1) | Laplacian | robust to outliers; kinked at 0, so gradient methods struggle | heavy tails, occasional bad points |
| Huber: $r^2$ small, $\lvert r\rvert$ large | Gaussian core, heavy tails | smooth **and** robust | the practical default when outliers exist |
| $-\log p$ (cross-entropy) | categorical | the likelihood for classification | discrete outcomes |
| Poisson deviance | counting | correct weighting when variance $=$ mean | photon counts, low count rates ([[Poisson Distribution]]) |

**Picture:** the loss as the shape of the valley the fit settles into: squared error assumes Gaussian noise, absolute error tolerates outliers, and a regularizer tilts the valley toward simpler answers.

**The most common error is using L2 on non-Gaussian data.** Counting data at low rates is Poissonian, and weighting by $1/\sigma_i^2 = 1/N_i$ with $N_i$ the *observed* count biases the fit — use the model's predicted variance, or a Poisson likelihood.

Weighting is part of the loss: $\chi^2 = \sum (r_i/\sigma_i)^2$ says loud points matter less. Getting $\sigma_i$ wrong silently reweights the fit and shows up as $\chi^2/\text{dof} \neq 1$ ([[(Map) Statistics]]).

## Regularization: choosing it chooses a prior

Add a penalty on the parameters themselves, $\;\min\; \text{loss} + \lambda R(\boldsymbol\theta)$:

| $R$ | Name | Effect | Bayesian reading |
|---|---|---|---|
| $\lVert\theta\rVert_2^2$ | ridge / Tikhonov | shrinks all parameters smoothly; fixes ill-conditioning | Gaussian prior |
| $\lVert\theta\rVert_1$ | lasso | drives parameters to **exactly zero** — selects a sparse subset | Laplacian prior |
| $\lVert\nabla\theta\rVert^2$ | smoothness | penalizes roughness | smooth-function prior |
| $\lVert\theta - \theta_0\rVert^2$ | anchoring | pulls toward prior knowledge | prior centred at $\theta_0$ |

$\lambda$ trades fit against regularity, so it needs setting from data (cross-validation) or from the noise level, never by taste. Truncating small singular values is the hard-cutoff version of Tikhonov's smooth filter — the same regularization idea, expressed spectrally ([[Pseudo-Inverse]], [[Singular Value Decomposition]]).

**Why regularize at all:** if the data do not constrain some parameter combination, the objective has a flat direction and the optimizer wanders it. A penalty makes the minimum unique. The diagnosis is the same degeneracy that produces $\pm10^6$ error bars — regularizing hides it, so understand it first.

## Constraints

**Equality constraints** $g(\boldsymbol\theta)=0$: form the Lagrangian $\mathcal L = f + \lambda g$ and solve $\nabla f = -\lambda\nabla g$ — at the optimum the objective's gradient is parallel to the constraint's, so no motion along the constraint improves $f$.

**The multiplier is not bookkeeping.** $\lambda = \partial f^*/\partial c$ for a constraint $g = c$: it is the **shadow price**, the rate at which the optimum improves as you relax the constraint. In thermodynamics this is exactly how $T$, $P$, $\mu$ appear as multipliers enforcing energy, volume and number ([[Legendre Transform]]).

**Inequality constraints** $g \le 0$ give the KKT conditions, whose content is *complementary slackness*: either the constraint is inactive ($g<0$) and $\lambda=0$, or it is active ($g=0$) and $\lambda \ge 0$. Practically: only the binding constraints matter, and the solver's job is finding which ones bind.

**Prefer reparametrization to explicit constraints** whenever it is available — it removes the constraint rather than enforcing it:

| Constraint | Reparametrize |
|---|---|
| $\theta > 0$ | $\theta = e^\phi$, fit $\phi$ |
| $0 < \theta < 1$ | $\theta = \tfrac12(1+\tanh\phi)$ |
| weights on a simplex | softmax |
| unit vector | normalize inside the model |

This also fixes scaling: fitting $\log\tau$ rather than $\tau$ gives positivity and a well-conditioned parameter in one move.

## Multi-objective

Competing goals are scalarized, $f = f_1 + w f_2$, and **the weight $w$ is a unit conversion** — non-dimensionalize both terms first or the weight is meaningless ([[Units and Dimensional Analysis]]). Sweeping $w$ traces the **Pareto front**: the set of solutions where improving one objective necessarily worsens the other. Report the front, not a single point, when the trade is the actual result.

**What makes an objective well-posed**, worth checking before blaming the optimizer:

- **Bounded below** — otherwise there is no minimum to find.
- **Smooth** if you want gradient methods; kinks (L1, $\max$, absolute values) demand subgradient or proximal methods.
- **Well-scaled** — parameters of comparable magnitude, or the quadratic model's geometry is wrecked.
- **Identifiable** — a unique minimum. If two parameters only appear as a product, fit the product.
- **Convex** if you can arrange it: any local minimum is global, and duality applies ([[Legendre Transform]]).

> [!question]- Your fit is dominated by three bad points and you are told to "use robust fitting." What are you changing, and what are you asserting?
> You are changing the loss from $r^2$ to something growing more slowly — Huber or L1 — which is asserting the noise has heavier tails than Gaussian. That is a claim about the measurement, not a numerical trick: it says large residuals are more probable than a Gaussian allows, so they should not dominate. If the outliers are real physics rather than noise, this hides them.

# Connections

- [[Optimization and Curve Fitting]] — the algorithms that minimize whatever you define here
- [[Least Squares and Chi-Squared Fitting]] — the L2/Gaussian case and its goodness-of-fit test
- [[Maximum Likelihood Estimation]] — the likelihood every loss is the log of
- [[Legendre Transform]] — multipliers as shadow prices; convex duality
- [[Pseudo-Inverse]] / [[Singular Value Decomposition]] — truncation as spectral regularization
- [[Machine Learning Methods]] — loss, regularizer and validation as the same three choices
- [[Units and Dimensional Analysis]] — why multi-objective weights need non-dimensionalizing
- [[(Map) Statistics]] — error bars, $\chi^2/\text{dof}$, and what the weights mean

---
Source: Boyd & Vandenberghe, *Convex Optimization*, Ch. 4–5; Nocedal & Wright, *Numerical Optimization*, Ch. 12, 17
