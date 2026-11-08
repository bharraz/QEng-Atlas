#numerics

**A neural network is a function built by stacking one simple step: multiply the input vector by a matrix, add a vector, and apply a fixed nonlinear function to each entry — then feed the result into the next step.** The matrices and vectors are the parameters, and with enough of them the result can approximate any continuous function; training adjusts them to fit data ([[Gradient Descent and Backpropagation]]).

# Reference

**One layer:**

$$
\mathbf h = \sigma(W\mathbf x + \mathbf b)
$$

- $\mathbf x$ — input vector
- $W$ — weight matrix (outputs × inputs) and $\mathbf b$ — bias vector: the trainable parameters, $n_\text{in}n_\text{out} + n_\text{out}$ per layer
- $\sigma$ — activation function, applied to each entry: ReLU $\max(0,z)$, $\tanh z$, or sigmoid $1/(1+e^{-z})$
- $\mathbf h$ — the layer's output, which is the next layer's input

A network is $f(\mathbf x) = W_L\,\sigma(\cdots\sigma(W_1\mathbf x + \mathbf b_1)\cdots) + \mathbf b_L$; the number of layers is its depth and the length of each $\mathbf h$ its width.

**Why the nonlinearity is essential:** without $\sigma$ the layers collapse, since $W_2(W_1\mathbf x) = (W_2W_1)\mathbf x$ is one matrix, and the network is a linear model however deep it is.

**Picture:** a ReLU unit is a hinge — zero on one side of a hyperplane in input space and rising linearly on the other. The network adds and composes hinges into a piecewise-linear surface, with the hinge positions learned from data, much as a [[Fourier Series]] builds a function from fixed sinusoids.

**Universal approximation:** one hidden layer with enough units can approximate any continuous function on a bounded region to any accuracy. The theorem says nothing about how many units that takes or whether training will find them; in practice depth reaches a given accuracy with far fewer parameters than width.

**The standard pieces:**

| Piece | Role |
|---|---|
| ReLU activation | the default for hidden layers; cheap, and its gradient does not vanish for positive inputs |
| sigmoid or softmax output | turns outputs into probabilities, for classification |
| mean-squared-error loss | regression; equivalent to assuming Gaussian noise ([[Least Squares and Chi-Squared Fitting]]) |
| cross-entropy loss | classification: the negative log-likelihood of the correct label |
| weight decay, dropout, early stopping | limit the effective flexibility, to curb overfitting ([[Objective Functions and Constraints]]) |
| architecture (CNN, RNN, transformer) | constrains the matrices to encode a structural assumption about the data ([[Machine Learning Methods]]) |

**When to use one:** large data and an unknown functional form. If a physical model exists, fitting its few parameters beats a network on the same data and gives interpretable error bars.

> [!question]- Why does a 100-layer network with no activation functions do no better than linear regression?
> A composition of linear maps is a linear map: the 100 weight matrices multiply into one, so the entire network computes $W\mathbf x + \mathbf b$ for some $W$ and $\mathbf b$ — exactly a linear regression model, with many redundant parameters.

# Connections

- [[Gradient Descent and Backpropagation]] — how the parameters are fitted
- [[Machine Learning Methods]] — where networks sit among other methods, and the validation discipline
- [[Objective Functions and Constraints]] — the loss is a noise model and the regularizer a prior
- [[Least Squares and Chi-Squared Fitting]] — mean-squared-error training is least squares with a flexible model
- [[Fourier Series]] — the fixed-basis expansion a network generalizes with learned basis functions
- [[Tensor Networks and MPS]] — the other variational function family used for quantum states

---
Source: Goodfellow, Bengio & Courville, *Deep Learning* (MIT Press, 2016), Ch. 6; Mehta et al., "A high-bias, low-variance introduction to machine learning for physicists," *Phys. Rep.* 810, 1 (2019)
