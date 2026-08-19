#numerics #reference

**Overview of what each technique actually does — supervised learning is curve fitting with enough capacity to overfit, so the whole discipline is loss, regularization, and honest validation.**

# Reference

Every supervised method is the same three choices: a **function family**, a **loss** to minimize on training data, and a **check on data not used for fitting** ([[Objective Functions and Constraints]]). The novelty relative to ordinary fitting is capacity — enough flexibility to memorize noise — which is why validation is not optional.

| Setting | You have | You want |
|---|---|---|
| **Supervised** | inputs $x$ with labels $y$ | predict $y$ for new $x$ |
| **Unsupervised** | inputs only | structure — groups, low-dimensional coordinates |
| **Reinforcement** | an environment and a reward | a policy that acts |

## Supervised: regression and classification

| Method | What it does | Reach for it when |
|---|---|---|
| **Linear / logistic regression** | fits a hyperplane (or its log-odds) | interpretability matters; the baseline you must beat |
| **Ridge / lasso** | linear plus L2 / L1 penalty | many correlated features; lasso when you want a sparse subset selected |
| **k-nearest neighbors** | predicts from nearby training points | small, low-dimensional data; no training step |
| **SVM (with kernels)** | maximum-margin separator, implicitly in a high-dimensional feature space | medium data, clear margin; the kernel encodes your notion of similarity |
| **Decision tree** | recursive axis-aligned splits | interpretable rules; alone, weak and unstable |
| **Random forest** | many trees on resampled data, averaged | strong default, few knobs, resists overfitting |
| **Gradient boosting** (XGBoost, LightGBM) | trees fit sequentially to residuals | **the workhorse for tabular data** — usually beats neural nets there |
| **Gaussian process** | distribution over functions; kernel sets smoothness | small data, and you want **calibrated uncertainty** — the engine behind Bayesian optimization ([[Optimization and Curve Fitting]]) |
| **Neural network (MLP)** | stacked linear maps with nonlinearities | large data, unknown functional form |

**Neural architectures**, in one line each — the architecture encodes an assumption about the data's structure:

| Architecture | Assumption baked in |
|---|---|
| **CNN** | translation invariance and locality — images, spectra, spatial fields |
| **RNN / LSTM** | sequential order with a running state — time series |
| **Transformer** | any element may attend to any other; order supplied explicitly rather than assumed |
| **Autoencoder** | a low-dimensional latent explains the data — compression, denoising, anomaly detection |
| **Graph network** | irregular connectivity — molecules, lattices, spin networks |

## Unsupervised

| Method | Does | Note |
|---|---|---|
| **PCA** | orthogonal directions of maximum variance | it is the SVD ([[Singular Value Decomposition]]) — linear, deterministic, interpretable |
| **t-SNE / UMAP** | 2D layouts preserving local neighborhoods | **visualization only** — distances and cluster sizes in the plot are not meaningful |
| **k-means** | $k$ spherical clusters | must choose $k$; assumes isotropic, similar-sized clusters |
| **Gaussian mixture** | soft clustering with covariances | k-means with shapes and probabilities |
| **DBSCAN** | density-based clusters | finds arbitrary shapes, labels outliers, needs no $k$ |

## The discipline, which is where results are actually won or lost

- **Split before you look.** Train / validation / test. The test set is touched once. Tuning against the test set turns it into a training set and your reported number becomes fiction.
- **Cross-validation** for small data: $k$-fold, average the score. For time series, split *forward in time* only — shuffling leaks the future.
- **Bias–variance.** Underfit = both errors high; overfit = train error low, validation high. The cure for overfitting is more data, fewer parameters, or stronger regularization, in that order of preference.
- **Data leakage** is the most common silent failure: any information in the training set that would not be available at prediction time. Normalizing using statistics from the whole dataset is the classic instance.
- **Class imbalance.** With 99% negatives, accuracy 99% is achieved by predicting nothing. Use precision/recall, ROC-AUC, or reweight the loss.
- **Baselines.** Compare against linear regression and against predicting the mean. A model that does not beat those has told you something.

## When it is the right tool for a physicist

**Use a model if you have one.** A three-parameter fit to a known functional form beats a neural network on the same data, is interpretable, and yields error bars ([[Optimization and Curve Fitting]]). ML earns its place when the input–output map is genuinely unknown or too high-dimensional to write down.

| Physics use | Why ML fits |
|---|---|
| **Surrogate models** | replace an expensive simulation with a fast interpolator |
| **Experiment tune-up** | Bayesian optimization over gate or trap parameters, where each evaluation is a real measurement |
| **Classification of data** | phase identification, state discrimination beyond a threshold ([[Binomial Errors in State Detection]]) |
| **Tomography reconstruction** | high-dimensional inverse problems with a regularizing prior ([[Quantum State Tomography (Atlas)]]) |
| **Denoising and anomaly detection** | autoencoders on signals where the noise model is unknown |
| **Learning representations** | tensor-network and neural quantum states as variational wavefunctions ([[Tensor Networks and MPS]]) |

> [!question]- A model scores 0.98 on validation and fails in the lab. What is the first thing to check?
> Leakage — some quantity in the training data would not exist at prediction time, or preprocessing used statistics computed over the whole dataset including validation. The second check is distribution shift: lab data drawn under different conditions than the training set. Both produce excellent validation scores and useless models, and neither is a modelling failure.

# Connections

- [[Objective Functions and Constraints]] — loss and regularizer, the two choices that define a model
- [[Optimization and Curve Fitting]] — the optimizers doing the training; Bayesian optimization
- [[Singular Value Decomposition]] — PCA is this, and nothing more
- [[Least Squares and Chi-Squared Fitting]] — linear regression's statistical version
- [[Bootstrap Resampling]] — resampling, the idea behind random forests
- [[Central Limit Theorem]] — why validation scores have error bars too
- [[Tensor Networks and MPS]] — variational function families from physics rather than ML
- [[Monte Carlo Methods]] — sampling as the other route to high-dimensional problems

---
Source: Hastie, Tibshirani & Friedman, *The Elements of Statistical Learning*, Ch. 2–3, 7; Mehta et al., "A high-bias, low-variance introduction to machine learning for physicists," *Phys. Rep.* 810, 1 (2019)
