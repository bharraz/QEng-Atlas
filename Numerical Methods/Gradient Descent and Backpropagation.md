#numerics

**Training a model means lowering a loss that measures how wrong it is on the data: find the direction in parameter space along which the loss falls fastest (minus the gradient), take a small step that way, and repeat.** Backpropagation is the chain rule organized so that this gradient, for every parameter at once, costs only a few times as much as evaluating the model.

# Reference

$$
\theta \leftarrow \theta - \eta\,\nabla_\theta L(\theta)
$$

- $\theta$ — all the parameters (every weight and bias), as one long vector
- $L$ — the loss, averaged over training examples
- $\nabla_\theta L$ — its [[Gradient]]: the direction of steepest increase
- $\eta$ — the learning rate (step size)

**Learning rate:** too large and the loss oscillates or diverges, overshooting across a valley; too small and progress is slow. For a quadratic bowl with curvatures $\lambda_i$, the iteration is stable only for $\eta < 2/\lambda_\text{max}$, and the flattest direction then needs $\sim \lambda_\text{max}/\lambda_\text{min}$ steps — the [[Condition Number]] of the curvature sets the cost of plain gradient descent.

**Variants:**

| Method | Change | Effect |
|---|---|---|
| **Stochastic gradient descent (SGD)** | average the gradient over a random mini-batch of $B$ examples instead of all the data | an unbiased estimate with noise $\propto 1/\sqrt B$ ([[Monte Carlo Methods]]); far cheaper per step, and the noise helps escape poor regions |
| **Momentum** | step along a running average of past gradients | a heavy ball rolling downhill: damps oscillation across narrow valleys, speeds travel along them |
| **Adam** | momentum plus a per-parameter step scaled by a running estimate of that parameter's gradient size | the common default; much less sensitive to badly scaled parameters |
| Newton, Levenberg–Marquardt | use curvature (second derivatives) | far fewer steps for small, smooth problems ([[Optimization and Curve Fitting]]); too costly for millions of parameters |

**Backpropagation.** A network is a chain of layers, $f = f_L \circ \cdots \circ f_1$, and the chain rule gives each layer's gradient as a product of local derivatives:

$$
\frac{\partial L}{\partial \theta_l} = \frac{\partial L}{\partial h_L}\,\frac{\partial h_L}{\partial h_{L-1}}\cdots\frac{\partial h_{l+1}}{\partial h_l}\,\frac{\partial h_l}{\partial \theta_l}
$$

- $h_l$ — the output of layer $l$
- $\theta_l$ — the parameters of layer $l$

Evaluating the product starting from the loss end lets every earlier layer reuse the partial products already computed, so one backward sweep yields the entire gradient for a cost of a few forward passes. Perturbing each parameter in turn would instead cost one forward pass per parameter — millions. This is reverse-mode automatic differentiation, done automatically by libraries such as PyTorch and JAX.

**Picture:** errors flow backward. Each layer receives "how much would the loss change if my output changed," multiplies it by its own local derivative, and passes the result down to the layer below — like tracing a signal backward through a chain of amplifiers by multiplying their gains.

**Failure modes:**

| Symptom | Cause | Remedy |
|---|---|---|
| loss explodes or becomes NaN | learning rate too large; exploding gradients | lower $\eta$; clip gradients |
| loss stalls early | vanishing gradients: saturating activations (sigmoid, tanh) multiply many small factors | ReLU, normalization layers, residual connections |
| training loss falls while validation loss rises | overfitting | early stopping, regularization, more data ([[Machine Learning Methods]]) |
| progress very slow along some directions | ill-conditioned loss surface | momentum or Adam; rescale the inputs |

**The same machinery in physics:** gradient-based pulse design (GRAPE, gradient ascent pulse engineering, differentiates a gate fidelity with respect to every control amplitude), variational quantum algorithms such as VQE and QAOA, whose gradients are measured with the parameter-shift rule ([[Variational Quantum Algorithms]]), and fitting any differentiable model with automatic differentiation.

> [!question]- The loss falls for a while, then starts oscillating wildly and blows up. What do you change first?
> The learning rate. Once the step exceeds $2/\lambda$ along the steepest direction of the loss surface, each step overshoots further than the last. Lower $\eta$ or use a decaying schedule, and clip gradients if occasional huge steps come from rare batches.

# Connections

- [[Neural Networks]] — the model whose parameters this trains
- [[Gradient]] — the steepest-ascent direction the update follows downhill
- [[Optimization and Curve Fitting]] — second-order methods for small, smooth problems
- [[Condition Number]] — why badly scaled problems converge slowly
- [[Monte Carlo Methods]] — the $1/\sqrt B$ noise of mini-batch gradients
- [[Machine Learning Methods]] — validation, overfitting, and where training fits in the workflow
- [[Variational Quantum Algorithms]] — VQE and QAOA, a variational loop driven by the same idea
- [[Pulse Shaping and Optimal Control]] — GRAPE, gradient-based design of control pulses

---
Source: Goodfellow, Bengio & Courville, *Deep Learning* (MIT Press, 2016), Ch. 6.5 and 8; Rumelhart, Hinton & Williams, "Learning representations by back-propagating errors," *Nature* 323, 533 (1986)
