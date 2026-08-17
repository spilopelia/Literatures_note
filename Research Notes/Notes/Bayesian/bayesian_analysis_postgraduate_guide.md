# A Practical Bayesian Analysis Guide for a New Postgraduate Researcher

## Purpose

This note is a compact framework for reading, understanding, and summarizing Bayesian methods in research papers without trying to memorize every derivation.

The main principle is:

> **Do not memorize Bayesian analysis as a collection of equations. Memorize the generative story and learn how to reconstruct the equations from it.**

For almost any new Bayesian problem, begin with five questions:

1. **What is unknown?**
2. **How do the unknowns generate the data?**
3. **What is the noise model?**
4. **What is the prior?**
5. **What posterior quantity do I want to infer?**

A useful mental chain is:

$$
\text{unknown parameters}
\rightarrow
\text{forward model}
\rightarrow
\text{predicted data}
\rightarrow
\text{noise}
\rightarrow
\text{observed data}.
$$

Bayesian inference works in the reverse direction:

$$
\text{observed data}
\rightarrow
\text{what can I learn about the unknown parameters?}
$$

---

# 1. The Four Probability Objects to Recognize Immediately

## 1.1 Prior

The prior is:

$$
p(\theta).
$$

Interpretation:

> What values of the unknown parameter were plausible before using the current data?

The prior can encode physical knowledge, previous measurements, mathematical constraints, smoothness assumptions, or deliberately broad uncertainty.

---

## 1.2 Likelihood

The likelihood is:

$$
p(d\mid\theta).
$$

Interpretation:

> If a particular parameter value were true, how plausible would the observed data be?

The likelihood comes from the **forward model plus the assumed measurement noise**.

---

## 1.3 Posterior

The posterior is:

$$
p(\theta\mid d).
$$

Interpretation:

> After seeing the data, what parameter values remain plausible?

This is usually the main object Bayesian inference is trying to determine.

---

## 1.4 Evidence / Marginal Likelihood

The Bayesian evidence is:

$$
p(d).
$$

If the model contains hyperparameters or belongs to a larger family, it is often written conditionally:

$$
p(d\mid\eta).
$$

Interpretation:

> Averaging over all parameter values allowed by the model or prior, how naturally does this model explain the observed data?

Evidence is therefore different from the likelihood at the single best-fitting parameter value.

---

# 2. Bayes' Rule

Bayes' theorem is:

$$
p(\theta\mid d)
=
\frac{
p(d\mid\theta)\,p(\theta)
}{
p(d)
}.
$$

The most useful verbal form is:

$$
\text{posterior}
=
\frac{
\text{likelihood}\times\text{prior}
}{
\text{evidence}
}.
$$

Or:

> **belief after seeing the data = compatibility with the data × belief before seeing the data, followed by normalization.**

The denominator is obtained by averaging over every possible value of the unknown parameter:

$$
p(d)
=
\int
p(d\mid\theta)\,p(\theta)\,d\theta.
$$

This equation is worth remembering conceptually as:

> **Evidence = average likelihood over everything the prior says is possible.**

---

# 3. Why Bayes' Rule Is True

The joint probability of the parameter and data can be written in two equivalent ways:

$$
p(\theta,d)
=
p(d\mid\theta)p(\theta),
$$

and

$$
p(\theta,d)
=
p(\theta\mid d)p(d).
$$

Because both expressions describe the same joint probability,

$$
p(d\mid\theta)p(\theta)
=
p(\theta\mid d)p(d).
$$

Rearranging gives Bayes' theorem:

$$
p(\theta\mid d)
=
\frac{
p(d\mid\theta)p(\theta)
}{
p(d)
}.
$$

---

# 4. A Reusable Gaussian Inference Pattern

A large fraction of astronomical inference problems can be locally or exactly written as:

$$
d=A\theta+n,
$$

where:

- the observed data are represented by the vector $d$;
- the unknown parameters are represented by the vector $\theta$;
- the forward operator is represented by the matrix $A$;
- the measurement noise is represented by $n$.

Assume Gaussian noise:

$$
n\sim\mathcal{N}(0,C_N).
$$

Then:

$$
d-A\theta=n.
$$

The corresponding likelihood is:

$$
p(d\mid\theta)
=
\frac{1}
{(2\pi)^{N_d/2}|C_N|^{1/2}}
\exp
\left[
-\frac{1}{2}
(d-A\theta)^T
C_N^{-1}
(d-A\theta)
\right].
$$

The quadratic quantity

$$
\chi^2
=
(d-A\theta)^T
C_N^{-1}
(d-A\theta)
$$

measures the disagreement between prediction and data in units set by the noise.

Therefore:

$$
p(d\mid\theta)
\propto
\exp\left(-\frac{\chi^2}{2}\right).
$$

A smaller chi-square generally means a larger likelihood.

---

# 5. Variance, Covariance, and Precision

## 5.1 Variance

Variance measures how widely one quantity can fluctuate around its mean:

$$
\mathrm{Var}(x)
=
\mathbb{E}
\left[
(x-\mathbb{E}[x])^2
\right].
$$

Large variance means more uncertainty or freedom.

Small variance means the quantity is more tightly constrained.

The standard deviation is:

$$
\sigma
=
\sqrt{\mathrm{Var}(x)}.
$$

---

## 5.2 Covariance

Covariance measures whether two quantities tend to vary together:

$$
\mathrm{Cov}(x,y)
=
\mathbb{E}
\left[
(x-\mathbb{E}[x])
(y-\mathbb{E}[y])
\right].
$$

Positive covariance means they tend to increase and decrease together.

Negative covariance means one tends to increase when the other decreases.

Covariance near zero means there is little linear tendency for them to move together.

---

## 5.3 Covariance Matrix

For a vector of unknown quantities,

$$
\theta
=
\begin{pmatrix}
\theta_1\\
\theta_2\\
\vdots\\
\theta_N
\end{pmatrix},
$$

the covariance matrix is:

$$
C
=
\begin{pmatrix}
\mathrm{Var}(\theta_1) &
\mathrm{Cov}(\theta_1,\theta_2) &
\cdots\\
\mathrm{Cov}(\theta_2,\theta_1) &
\mathrm{Var}(\theta_2) &
\cdots\\
\vdots &
\vdots &
\ddots
\end{pmatrix}.
$$

The diagonal tells us how much each parameter can vary.

The off-diagonal entries tell us how parameters vary together.

---

## 5.4 Precision Matrix

The inverse covariance matrix is called the precision matrix:

$$
R=C^{-1}.
$$

A useful intuition is:

- covariance describes **allowed freedom**;
- precision describes **how strongly departures are constrained**.

---

# 6. Regularization as a Bayesian Prior

Suppose a pixelized reconstruction is represented by $\theta$.

A quadratic regularizer has the form:

$$
E_{\mathrm{reg}}
=
\frac{1}{2}
\theta^T R\theta.
$$

A Gaussian prior can be written as:

$$
p(\theta)
=
\frac{|R|^{1/2}}
{(2\pi)^{N/2}}
\exp
\left[
-\frac{1}{2}\theta^TR\theta
\right].
$$

Therefore:

$$
\boxed{
\text{quadratic regularization}
\Longleftrightarrow
\text{Gaussian prior}.
}
$$

This is an important connection.

Regularization is not necessarily an extra non-Bayesian ingredient. When it corresponds to a normalized prior distribution, it is part of the Bayesian model.

---

# 7. Posterior = Data Constraint + Prior Constraint

Using the Gaussian likelihood and Gaussian prior,

$$
p(\theta\mid d)
\propto
p(d\mid\theta)p(\theta).
$$

Taking the negative logarithm gives:

$$
-\log p(\theta\mid d)
=
\frac{1}{2}
(d-A\theta)^T
C_N^{-1}
(d-A\theta)
+
\frac{1}{2}
\theta^TR\theta
+
\mathrm{constant}.
$$

This can be read as:

$$
\text{negative log posterior}
=
\text{data mismatch}
+
\text{prior penalty}
+
\text{constant}.
$$

Thus minimizing a regularized objective can be equivalent to maximizing a Bayesian posterior.

---

# 8. MAP: The Best Single Posterior Point

The maximum-a-posteriori estimate is:

$$
\theta_{\mathrm{MAP}}
=
\underset{\theta}{\operatorname{argmax}}
\,
p(\theta\mid d).
$$

Equivalently:

$$
\theta_{\mathrm{MAP}}
=
\underset{\theta}{\operatorname{argmin}}
\,
\left[
-\log p(\theta\mid d)
\right].
$$

For the linear Gaussian problem, differentiating the negative log posterior and setting the derivative to zero gives:

$$
\left(
A^TC_N^{-1}A+R
\right)
\theta_{\mathrm{MAP}}
=
A^TC_N^{-1}d.
$$

Therefore:

$$
\theta_{\mathrm{MAP}}
=
\left(
A^TC_N^{-1}A+R
\right)^{-1}
A^TC_N^{-1}d.
$$

Do not initially memorize this matrix formula.

Instead remember:

> **MAP = minimize the negative log posterior.**

Then the formula can be re-derived when needed.

---

# 9. Posterior Covariance

For the linear Gaussian case, the posterior is also Gaussian.

Its covariance is:

$$
\Sigma_{\mathrm{post}}
=
\left(
A^TC_N^{-1}A+R
\right)^{-1}.
$$

Its precision is therefore:

$$
\Sigma_{\mathrm{post}}^{-1}
=
A^TC_N^{-1}A+R.
$$

This has a useful interpretation:

$$
\boxed{
\text{posterior information}
=
\text{information from data}
+
\text{information from prior}.
}
$$

---

# 10. Marginalization

Marginalization means averaging over parameters that are not the main quantity of interest.

Suppose the model has parameters $\theta$ and nuisance parameters $\phi$.

Then:

$$
p(\theta\mid d)
=
\int
p(\theta,\phi\mid d)
\,d\phi.
$$

Interpretation:

> For each value of the parameter I care about, add up all possible values of the nuisance parameter, weighted by their probabilities.

"Integrating out" a parameter means the same thing.

---

# 11. Bayesian Evidence

Evidence is obtained by marginalizing the likelihood over the prior:

$$
p(d)
=
\int
p(d\mid\theta)
p(\theta)
\,d\theta.
$$

The important distinction is:

- maximum likelihood asks whether **one particular parameter value** fits very well;
- evidence asks whether the **whole allowed parameter family** explains the data naturally.

A highly flexible model can achieve an excellent maximum likelihood but low evidence if only a tiny fraction of its allowed parameter space gives a good fit.

This is the origin of the Bayesian Occam effect.

---

# 12. Occam Effect

Suppose two models can both reproduce the data.

One model allows an enormous number of possible behaviours, most of which do not resemble the observed data.

The second model allows fewer possibilities, many of which resemble the observed data.

Evidence can prefer the second model even if the first model has a slightly better best-fitting point.

This preference is not an arbitrary extra penalty. It appears naturally because evidence integrates over the full prior volume.

---

# 13. Hyperparameters and Hierarchical Bayes

A parameter controls the physical or latent model.

A hyperparameter controls the probability distribution of those parameters.

For example, suppose:

$$
\theta
\sim
\mathcal{N}
\left(
0,
C(\eta)
\right).
$$

Then $\eta$ is a hyperparameter.

The first Bayesian level is:

$$
p(\theta\mid d,\eta)
\propto
p(d\mid\theta)
p(\theta\mid\eta).
$$

Marginalize over $\theta$:

$$
p(d\mid\eta)
=
\int
p(d\mid\theta)
p(\theta\mid\eta)
\,d\theta.
$$

Now apply Bayes again:

$$
p(\eta\mid d)
\propto
p(d\mid\eta)
p(\eta).
$$

The key phrase to remember is:

> **Evidence at one level becomes the likelihood at the next hierarchical level.**

---

# 14. Matérn Regularization

A Matérn covariance is a flexible rule describing how strongly values at two spatial positions should be correlated as a function of their separation.

A common form is:

$$
C_{ij}(\rho,\nu)
=
\frac{2^{1-\nu}}{\Gamma(\nu)}
\left(
\sqrt{2\nu}
\frac{d_{ij}}{\rho}
\right)^\nu
K_\nu
\left(
\sqrt{2\nu}
\frac{d_{ij}}{\rho}
\right).
$$

The important quantities are:

### Correlation scale

$$
\rho
$$

controls how far correlations extend spatially.

A larger value usually permits broader correlated structures.

A smaller value allows correlations to decay over shorter distances.

### Smoothness

$$
\nu
$$

controls the differentiability and roughness of the random field.

### Overall regularization strength

A common precision matrix is:

$$
R
=
\lambda C^{-1}(\rho,\nu).
$$

Then:

$$
\mathrm{Cov}(\theta)
=
R^{-1}
=
\frac{1}{\lambda}
C(\rho,\nu).
$$

Therefore:

$$
\lambda\uparrow
\Rightarrow
\mathrm{Cov}(\theta)\downarrow
\Rightarrow
\text{less freedom}
\Rightarrow
\text{stronger regularization}.
$$

And:

$$
\lambda\downarrow
\Rightarrow
\mathrm{Cov}(\theta)\uparrow
\Rightarrow
\text{more freedom}
\Rightarrow
\text{weaker regularization}.
$$

---

# 15. Why a Regularization Weight Cannot Always Be Naively Sampled

Suppose an optimization objective contains:

$$
\chi^2+\lambda R(\theta).
$$

It is tempting to put $\lambda$ into an MCMC sampler and call it Bayesian inference.

That is not automatically valid.

If the regularizer defines a Gaussian prior, the properly normalized prior includes:

$$
p(\theta\mid\lambda)
=
\frac{|R(\lambda)|^{1/2}}
{(2\pi)^{N/2}}
\exp
\left[
-\frac{1}{2}
\theta^TR(\lambda)\theta
\right].
$$

When $\lambda$ is fixed, normalization terms independent of $\theta$ can often be ignored for parameter optimization.

When $\lambda$ is being inferred, the normalization depends on $\lambda$ and **cannot be discarded**.

Therefore a numerical regularizer becomes a Bayesian hyperparameter only when its full probability distribution, including normalization or partition function, is properly defined or handled.

---

# 16. Three Things Not to Confuse

## Optimization

Optimization finds one best point:

$$
\theta_{\mathrm{best}}.
$$

Examples include maximum likelihood and MAP estimation.

## Sampling

Sampling approximates a whole probability distribution:

$$
p(\theta\mid d).
$$

Examples include MCMC and nested sampling posterior samples.

## Evidence

Evidence averages over parameter space:

$$
p(d\mid M)
=
\int
p(d\mid\theta,M)
p(\theta\mid M)
\,d\theta.
$$

A model with the best-fitting point does not necessarily have the highest evidence.

---

# 17. A Five-Line Summary for Every New Bayesian Paper

Before studying detailed derivations, write:

## Unknowns

$$
\theta = \; ?
$$

## Forward model

$$
d_{\mathrm{model}}
=
f(\theta).
$$

## Likelihood / noise

$$
p(d\mid\theta)
=
\; ?
$$

## Prior

$$
p(\theta)
=
\; ?
$$

## Desired posterior

$$
p(\theta\mid d)
=
\; ?
$$

If hyperparameters exist, add:

## Hyperparameters

$$
\eta=\;?
$$

and ask how:

$$
p(d\mid\eta)
$$

is evaluated.

---

# 18. How to Read a Difficult Equation

For every unfamiliar equation, ask:

1. **What type of object is this?**  
   Scalar, vector, matrix, probability density, covariance, or objective function?

2. **Where did it come from?**  
   Forward physics, probability rule, Gaussian assumption, derivative, approximation, or numerical method?

3. **Which part comes from the data?**

4. **Which part comes from the prior or modelling assumption?**

5. **What happens in limiting cases?**

For example, if:

$$
\mathrm{Cov}(\theta)
=
\frac{1}{\lambda}C,
$$

then checking:

$$
\lambda\rightarrow\infty
$$

immediately shows that the allowed variance goes to zero, so regularization becomes extremely strong.

Limiting-case reasoning is generally more reliable than memorizing verbal definitions.

---

# 19. Recommended Research-Notebook Template

For every statistical method or paper, summarize it under these headings:

## Problem
What scientific quantity is being inferred?

## Generative model
How would nature produce the observed data?

## Data
What is measured?

## Parameters
What is unknown?

## Likelihood
What noise assumptions convert predictions into probabilities?

## Prior
What assumptions are imposed before using the data?

## Posterior
What quantity is actually sampled or optimized?

## Hyperparameters
What controls the prior or model complexity?

## Nuisance parameters
What is marginalized out?

## Computation
Analytic solution, MCMC, nested sampling, variational inference, optimization, or something else?

## Diagnostics
How is convergence, calibration, or model adequacy checked?

## Failure modes
Which assumptions could bias the result?

## Scientific interpretation
Which conclusion follows from the data, and which conclusion depends strongly on prior/model assumptions?

---

# 20. Minimal Equation Set Worth Memorizing

### Bayes' theorem

$$
p(\theta\mid d)
=
\frac{
p(d\mid\theta)p(\theta)
}{
p(d)
}.
$$

### Evidence

$$
p(d)
=
\int
p(d\mid\theta)p(\theta)
\,d\theta.
$$

### Gaussian likelihood

$$
p(d\mid\theta)
\propto
\exp
\left(
-\frac{\chi^2}{2}
\right).
$$

### Prior expressed as an energy or regularizer

$$
p(\theta)
\propto
\exp
\left[
-E_{\mathrm{prior}}(\theta)
\right].
$$

### Negative log posterior

$$
-\log p(\theta\mid d)
=
-\log p(d\mid\theta)
-\log p(\theta)
+
\mathrm{constant}.
$$

### Hierarchical inference

$$
p(\eta\mid d)
\propto
p(d\mid\eta)p(\eta).
$$

Everything else should initially be something you know how to **derive or look up**, rather than something you force yourself to memorize.

---

# 21. Suggested Learning Strategy

For the first few months of postgraduate Bayesian work:

1. Start every problem by writing the generative model.
2. Explicitly identify data, parameters, noise, likelihood, and priors.
3. Translate every probability expression into an English sentence.
4. Derive simple Gaussian examples by hand.
5. Use limiting cases to check your understanding.
6. Keep optimization, posterior sampling, and evidence conceptually separate.
7. For every regularizer, ask whether it is a genuine normalized prior or merely an optimization penalty.
8. Learn marginalization conceptually before focusing on integration techniques.
9. Compare methods across papers using the same notebook template.
10. Memorize only equations you repeatedly use.

The most useful overall chain is:

$$
\boxed{
\text{generative model}
\rightarrow
\text{likelihood}
\rightarrow
\text{prior}
\rightarrow
\text{posterior}
\rightarrow
\text{marginalization}
\rightarrow
\text{evidence}.
}
$$

Once this chain becomes automatic, most Bayesian papers become variations of a familiar structure rather than collections of unrelated statistical terminology.
