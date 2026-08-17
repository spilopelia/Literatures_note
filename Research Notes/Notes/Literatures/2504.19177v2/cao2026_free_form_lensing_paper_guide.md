# Paper Guide: Free-Form Strong-Lens Potential Reconstruction with Matérn Regularization

## Paper

**Cao et al. — _Probing Dark Matter Substructures with Free-Form Modelling: A Case Study of the 'Jackpot' Strong Lens_**

arXiv:2504.19177v2, revised 10 February 2026.

Source: https://arxiv.org/abs/2504.19177

---

# 1. What Problem Is the Paper Trying to Solve?

Strong gravitational lenses produce arcs and multiple images whose detailed shapes depend on the gravitational potential of the foreground lens.

Small dark-matter subhalos can slightly distort these arcs.

A common approach is to assume a particular parametric subhalo profile, such as an NFW halo, and ask whether adding it improves the fit.

The problem is that other kinds of mass structure can also create residuals:

- inaccurate ellipticity or slope of the main lens;
- external shear;
- higher-order angular structure;
- line-of-sight halos;
- more general departures from the assumed macro lens profile.

A parametric subhalo can therefore sometimes absorb errors that actually belong to the main lens model.

The paper asks:

> **Can we reconstruct whatever perturbation the data require without first assuming that the perturbation must have a particular subhalo profile?**

The proposed solution is a **pixelized correction to the lensing potential**, regularized by a Matérn covariance and fitted within a Bayesian framework.

---

# 2. Central Scientific Idea

Write the total potential schematically as:

$$
\psi_{\mathrm{true}}
=
\psi_{\mathrm{macro}}
+
\delta\psi.
$$

Here:

- $\psi_{\mathrm{macro}}$ is a conventional smooth parametric lens model;
- $\delta\psi$ is a free-form pixelized correction.

Instead of saying:

$$
\delta\psi
=
\psi_{\mathrm{NFW}}(M,c,x,y),
$$

the method allows:

$$
\delta\psi
=
\begin{pmatrix}
\delta\psi_1\\
\delta\psi_2\\
\vdots\\
\delta\psi_{N_p}
\end{pmatrix}.
$$

This gives much more freedom.

But unconstrained pixel values can fit noise, so the reconstruction needs a prior or regularizer.

That role is played by the Matérn covariance.

---

# 3. Why Potential Corrections Affect the Image

The lens equation is:

$$
\boldsymbol{\beta}
=
\boldsymbol{\theta}
-
\nabla\psi(\boldsymbol{\theta}),
$$

where:

- $\boldsymbol{\theta}$ is an image-plane position;
- $\boldsymbol{\beta}$ is the corresponding source-plane position;
- $\psi$ is the lensing potential.

A perturbation to the potential changes the deflection:

$$
\delta\boldsymbol{\alpha}
=
\nabla\delta\psi.
$$

That changes where an image-plane pixel maps into the source plane.

If the source brightness varies spatially, shifting the source-plane position changes the predicted image brightness.

For sufficiently small perturbations, this relation can be linearized.

The paper writes the image residuals and potential corrections as a linear mapping:

$$
\delta\boldsymbol{d}
=
\mathbf{L}_{\delta\psi}
\boldsymbol{\delta\psi}
+
\boldsymbol{n}.
$$

This is the key equation enabling the semi-linear solution.

---

# 4. What the Symbols Mean

## Image residual vector

$$
\delta\boldsymbol{d}
$$

contains the residual image brightness left after the macro lens model.

## Potential correction vector

$$
\boldsymbol{\delta\psi}
$$

contains the unknown correction at every potential-grid pixel.

## Linear response matrix

$$
\mathbf{L}_{\delta\psi}
$$

encodes how changing a potential pixel changes the predicted image.

The paper builds it from:

- source brightness gradients;
- gradients of the potential pixels;
- interpolation between the potential and image grids;
- PSF convolution.

Schematically:

$$
\mathbf{L}_{\delta\psi}
=
-
\mathbf{B}
\mathbf{D}_{s}
\mathbf{C}_{f}
\mathbf{D}_{\psi}.
$$

## Noise

$$
\boldsymbol{n}
\sim
\mathcal{N}
\left(
0,
\mathbf{C}_{D}
\right).
$$

The noise covariance matrix is:

$$
\mathbf{C}_{D}.
$$

---

# 5. The Likelihood

Because the image noise is modeled as Gaussian,

$$
P
\left(
\delta\boldsymbol{d}
\mid
\boldsymbol{\delta\psi},
\mathbf{L}_{\delta\psi}
\right)
=
\frac{
\exp
\left[
-
E_D
\right]
}{
Z_D
}.
$$

The data energy is:

$$
E_D
=
\frac{1}{2}
\left(
\mathbf{L}_{\delta\psi}
\boldsymbol{\delta\psi}
-
\delta\boldsymbol{d}
\right)^T
\mathbf{C}_{D}^{-1}
\left(
\mathbf{L}_{\delta\psi}
\boldsymbol{\delta\psi}
-
\delta\boldsymbol{d}
\right).
$$

This is:

$$
E_D
=
\frac{1}{2}\chi^2.
$$

The normalization is:

$$
Z_D
=
(2\pi)^{N_d/2}
\left(
\det\mathbf{C}_D
\right)^{1/2}.
$$

Therefore:

$$
P
\left(
\delta\boldsymbol{d}
\mid
\boldsymbol{\delta\psi}
\right)
\propto
\exp
\left(
-\frac{\chi^2}{2}
\right).
$$

---

# 6. Why Maximum Likelihood Alone Is Not Enough

If the method minimizes only image residuals, a large number of free potential pixels can fit noise.

The unregularized maximum-likelihood solution is:

$$
\boldsymbol{\delta\psi}_{\mathrm{ML}}
=
\left(
\mathbf{L}_{\delta\psi}^{T}
\mathbf{C}_{D}^{-1}
\mathbf{L}_{\delta\psi}
\right)^{-1}
\mathbf{L}_{\delta\psi}^{T}
\mathbf{C}_{D}^{-1}
\delta\boldsymbol{d}.
$$

The authors note that this inversion is generally noisy and ill-posed.

The solution therefore requires a prior.

---

# 7. The Matérn Prior

For potential pixels $i$ and $j$ separated by distance $d_{ij}$, the Matérn correlation is:

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

This gives the covariance matrix:

$$
\mathbf{C}_{\delta\psi}.
$$

The precision or regularization matrix is:

$$
\mathbf{R}_{\delta\psi}
\left(
\lambda^{\delta\psi},
\rho,
\nu
\right)
=
\lambda^{\delta\psi}
\mathbf{C}_{\delta\psi}^{-1}
(\rho,\nu).
$$

The three important hyperparameters are:

### Overall strength

$$
\lambda^{\delta\psi}
$$

controls the total strength of regularization.

Larger values impose stronger restrictions on the potential field.

### Correlation scale

$$
\rho
$$

controls the characteristic spatial scale over which pixels are correlated.

### Smoothness

$$
\nu
$$

controls the differentiability or roughness of the reconstructed field.

The paper notes that the field is approximately:

$$
\left\lceil\nu\right\rceil-1
$$

times differentiable.

Special cases include the exponential kernel at:

$$
\nu=0.5,
$$

and the Gaussian limit as:

$$
\nu\rightarrow\infty.
$$

---

# 8. Covariance of the Potential Correction

Because:

$$
\mathbf{R}_{\delta\psi}
=
\lambda^{\delta\psi}
\mathbf{C}_{\delta\psi}^{-1},
$$

the prior covariance is:

$$
\mathrm{Cov}
\left(
\boldsymbol{\delta\psi}
\right)
=
\mathbf{R}_{\delta\psi}^{-1}
=
\frac{1}{\lambda^{\delta\psi}}
\mathbf{C}_{\delta\psi}.
$$

Interpretation:

> Before seeing the data, how much is every potential pixel allowed to vary, and how strongly should different pixels vary together?

Therefore:

$$
\lambda^{\delta\psi}\uparrow
\Rightarrow
\mathrm{Cov}(\boldsymbol{\delta\psi})\downarrow
\Rightarrow
\text{less freedom}
\Rightarrow
\text{stronger regularization}.
$$

---

# 9. Regularization as a Bayesian Prior

The prior is written as:

$$
P
\left(
\delta\boldsymbol{\psi}
\mid
\boldsymbol{\xi}_{\delta\psi},
\boldsymbol{g}_{\delta\psi}
\right)
=
\frac{
\exp
\left[
-
E_{\delta\psi}
\right]
}{
Z_{\delta\psi}
}.
$$

For quadratic regularization:

$$
E_{\delta\psi}
=
\frac{1}{2}
\delta\boldsymbol{\psi}^T
\mathbf{R}_{\delta\psi}
\delta\boldsymbol{\psi}.
$$

Therefore the potential correction has a multivariate Gaussian prior.

This is why the regularizer can be incorporated consistently into Bayesian inference.

---

# 10. Applying Bayes' Rule

Bayes' theorem gives:

$$
P
\left(
\delta\boldsymbol{\psi}
\mid
\delta\boldsymbol{d},
\mathbf{L}_{\delta\psi},
\boldsymbol{\xi}_{\delta\psi},
\boldsymbol{g}_{\delta\psi}
\right)
=
\frac{
P
\left(
\delta\boldsymbol{d}
\mid
\delta\boldsymbol{\psi},
\mathbf{L}_{\delta\psi}
\right)
P
\left(
\delta\boldsymbol{\psi}
\mid
\boldsymbol{\xi}_{\delta\psi},
\boldsymbol{g}_{\delta\psi}
\right)
}{
P
\left(
\delta\boldsymbol{d}
\mid
\mathbf{L}_{\delta\psi},
\boldsymbol{\xi}_{\delta\psi},
\boldsymbol{g}_{\delta\psi}
\right)
}.
$$

The numerator combines:

$$
\text{likelihood}
\times
\text{regularization prior}.
$$

The denominator is the Bayesian evidence.

---

# 11. The MAP Potential Reconstruction

Combining the Gaussian likelihood and Gaussian prior gives a Gaussian posterior.

The MAP solution is:

$$
\boldsymbol{\delta\psi}_{\mathrm{MAP}}
=
\left(
\mathbf{L}_{\delta\psi}^{T}
\mathbf{C}_{D}^{-1}
\mathbf{L}_{\delta\psi}
+
\mathbf{R}_{\delta\psi}
\right)^{-1}
\mathbf{L}_{\delta\psi}^{T}
\mathbf{C}_{D}^{-1}
\delta\boldsymbol{d}.
$$

This equation can be interpreted as:

$$
\boxed{
\text{solution}
=
\left(
\text{data information}
+
\text{prior information}
\right)^{-1}
\times
\text{data forcing}.
}
$$

The important point is that thousands of potential-pixel values do not have to be independently explored by an ordinary MCMC.

For a fixed regularization matrix, they can be solved directly by matrix inversion.

---

# 12. Posterior Covariance

The posterior covariance of a linear Gaussian inversion has the form:

$$
\Sigma_{\delta\psi}
=
\left(
\mathbf{L}_{\delta\psi}^{T}
\mathbf{C}_{D}^{-1}
\mathbf{L}_{\delta\psi}
+
\mathbf{R}_{\delta\psi}
\right)^{-1}.
$$

This represents the uncertainty and covariance among reconstructed potential pixels under the assumed linearized model and regularization.

---

# 13. How the Regularization Strength Is Inferred

The regularization hyperparameters are collected into:

$$
\boldsymbol{\xi}_{\delta\psi}
=
\left(
\lambda^{\delta\psi},
\rho,
\nu
\right).
$$

For one proposed set of hyperparameters, the Bayesian evidence is:

$$
P
\left(
\delta\boldsymbol{d}
\mid
\boldsymbol{\xi}_{\delta\psi}
\right)
=
\int
P
\left(
\delta\boldsymbol{d}
\mid
\delta\boldsymbol{\psi}
\right)
P
\left(
\delta\boldsymbol{\psi}
\mid
\boldsymbol{\xi}_{\delta\psi}
\right)
d\delta\boldsymbol{\psi}.
$$

Interpretation:

> If this particular regularization rule were correct, how naturally would all the potential maps allowed by it produce the observed residual image?

Because the problem is linear and both likelihood and prior are Gaussian, this high-dimensional integral can be evaluated analytically.

The authors can therefore sample a much lower-dimensional hyperparameter space rather than sampling every potential pixel.

---

# 14. Hierarchical Bayesian View

There are two Bayesian levels.

## Level 1: infer the potential map for fixed regularization

$$
P
\left(
\delta\boldsymbol{\psi}
\mid
\delta\boldsymbol{d},
\lambda^{\delta\psi},
\rho,
\nu
\right)
\propto
P
\left(
\delta\boldsymbol{d}
\mid
\delta\boldsymbol{\psi}
\right)
P
\left(
\delta\boldsymbol{\psi}
\mid
\lambda^{\delta\psi},
\rho,
\nu
\right).
$$

## Level 2: infer the regularization hyperparameters

$$
P
\left(
\lambda^{\delta\psi},
\rho,
\nu
\mid
\delta\boldsymbol{d}
\right)
\propto
P
\left(
\delta\boldsymbol{d}
\mid
\lambda^{\delta\psi},
\rho,
\nu
\right)
P
\left(
\lambda^{\delta\psi},
\rho,
\nu
\right).
$$

The key conceptual statement is:

> **The evidence obtained by marginalizing over the potential map at Level 1 becomes the likelihood for the hyperparameters at Level 2.**

---

# 15. Hyperparameter Priors Used in the Paper

The paper assigns broad priors to the Matérn hyperparameters.

For the overall coefficient:

$$
\lambda^{\delta\psi}
\sim
\mathcal{L}
\left(
10^{-6},
10^{6}
\right),
$$

where $\mathcal{L}$ denotes a log-uniform prior.

For the correlation scale:

$$
\rho
\sim
\mathcal{L}
\left(
10^{-4},
10^{3}
\right).
$$

For the smoothness parameter:

$$
\nu
\sim
\mathcal{U}
\left(
0.5,
10
\right),
$$

where $\mathcal{U}$ denotes a uniform prior.

The optimal values are obtained by sampling the Bayesian evidence.

---

# 16. Why Evidence Does Not Simply Choose Zero Regularization

Very weak regularization gives the potential map a large amount of freedom.

That can produce an excellent best-fit image, including fitting noise.

However, evidence does not evaluate only the best map.

It averages over the entire prior distribution:

$$
P(d\mid\eta)
=
\int
P(d\mid\delta\psi)
P(\delta\psi\mid\eta)
d\delta\psi.
$$

A prior that allows an enormous volume of useless solutions can therefore have lower evidence than a more restrictive prior whose allowed solutions more naturally resemble the data.

This is the Bayesian Occam effect.

At the opposite extreme, very strong regularization produces a simple but inflexible model that cannot fit real perturbations.

Evidence balances:

$$
\text{quality of data fit}
\quad\text{against}\quad
\text{unnecessary model freedom}.
$$

---

# 17. Source Reconstruction

The method is extended from a potential-only inversion to simultaneous reconstruction of:

- pixelized source light;
- pixelized potential corrections.

This matters because source morphology and lens-potential perturbations can partially mimic one another.

The paper tests whether this covariance degrades recovery of the perturbation.

The authors find that simultaneous inversion remains effective, although inaccuracies in the initial macro model can introduce some bias.

---

# 18. Mock Experiments

The method is tested on four types of perturbations:

1. a spherical NFW subhalo;
2. external shear;
3. an angular multipole perturbation;
4. a Gaussian random field.

This is important because the same free-form method is intended to recover both:

$$
\text{localized perturbations}
$$

and

$$
\text{extended/global perturbations}.
$$

The method is not told in advance which type is present.

---

# 19. NFW Concentration

For an NFW halo, the concentration is:

$$
c_{200}
=
\frac{r_{200}}{r_s}.
$$

Here:

- $r_{200}$ is the radius enclosing a mean density 200 times the critical density;
- $r_s$ is the NFW scale radius.

Larger concentration means the same halo mass is distributed more strongly toward the centre.

The paper compares the Jackpot reconstruction with a previously inferred approximately:

$$
M_{200}
\sim
10^{10}M_\odot,
$$

high-concentration model with roughly:

$$
c
\sim
200,
$$

and with a much more massive conventional NFW interpretation following a standard mass-concentration relation.

The free-form morphology is more consistent with the compact, highly concentrated interpretation.

Importantly, the free-form method does **not** directly measure:

$$
c=200.
$$

Rather, its reconstructed morphology resembles the high-concentration parametric solution.

---

# 20. Application to the Jackpot Lens

The real system is:

**SLACS0946+1006**, commonly called the **Jackpot lens**.

The authors begin from an EPL plus external shear macro model and reconstruct the remaining potential perturbations.

They recover a localized positive convergence perturbation at approximately the location of the previously reported dark substructure.

The residual image is reduced close to the observational noise level.

The reconstructed compact structure is therefore independently recovered without requiring that the perturbation itself follow an NFW functional form.

This is one of the strongest results of the paper.

---

# 21. Why the Result Matters

A central systematic in subhalo searches is:

$$
\text{subhalo signal}
\leftrightarrow
\text{incorrect macro lens structure}.
$$

A parametric subhalo can sometimes compensate for an inadequate macro model.

A free-form potential reconstruction asks a less restrictive question:

> What perturbation does the image actually require?

The ability to recover subhalos, shear, multipoles, and random fields with the same framework provides a useful way to test whether an apparent subhalo detection is instead a manifestation of larger-scale lens complexity.

---

# 22. Important Limitation: Constant Regularization

The current implementation applies one regularization behaviour across the modelling region.

This creates conflicting requirements.

In regions without real perturbations, the reconstruction wants:

$$
\text{strong regularization}
$$

to suppress noise.

Near a compact real subhalo, it wants:

$$
\text{weak regularization}
$$

to preserve sharp spatial gradients.

A single global hyperparameter setting has to compromise between the two.

The authors conclude that the evidence-optimal constant regularization can therefore be:

- too weak in empty regions;
- too strong around compact perturbations.

This causes **oversmoothing** of highly concentrated subhalos.

---

# 23. Consequence: Mass Can Be Underestimated

The paper explicitly notes that strong constant smoothing suppresses the central cusp of compact mass clumps.

Therefore the free-form reconstruction can underestimate their central or aperture mass.

This is crucial when interpreting the Jackpot result.

The method strongly supports the presence and compact morphology of the perturber, but its current free-form mass reconstruction should not automatically be treated as an unbiased measurement of the inner density profile.

---

# 24. L2 Versus L1 Regularization

The current Matérn regularizer is quadratic.

This is an L2-type penalty:

$$
E_{\mathrm{reg}}
\propto
\delta\boldsymbol{\psi}^T
R
\delta\boldsymbol{\psi}.
$$

L2 regularization shrinks fluctuations but generally does not set unnecessary pixels exactly to zero.

The authors report artifacts such as negative-convergence features.

A sparse L1-type regularizer would instead favour:

$$
\delta\psi_i=0
$$

unless the data require a perturbation.

However, L1 regularization breaks the simple linear Gaussian inversion, so the potential pixels could no longer be obtained using the same analytic matrix solution.

This would create a much harder nonlinear optimization or sampling problem involving thousands of variables.

---

# 25. Macro-Model Bias

The current implementation cannot simultaneously vary the smooth main-lens mass model and the free-form potential correction.

The main lens is effectively fixed during the potential-correction step.

Mock tests show that starting from an inaccurate macro-model solution can shift recovered perturbation properties.

For the simulated subhalo case, the paper reports a tendency toward an approximately:

$$
0.5\ \mathrm{dex}
$$

underestimate of subhalo mass when starting from the macro-model estimate rather than the true lens.

This demonstrates that a "free-form correction" is not completely free of macro-model systematics.

---

# 26. Lens-Light Modelling

The current observational analysis does not perform a fully simultaneous inference of:

$$
\text{lens light}
+
\text{source light}
+
\text{main lens mass}
+
\text{potential correction}.
$$

The paper discusses incorporating lens-light modelling directly into the potential-correction framework as a future improvement.

This matters because imperfect subtraction of lens-galaxy light can produce image residuals that may otherwise be absorbed by the source or mass reconstruction.

---

# 27. Source Hyperparameters

For the Jackpot potential-correction analysis, some source-model hyperparameters are fixed to the values obtained from the preceding macro-model fit.

The authors state that allowing them to vary during the correction makes the matrix system numerically unstable.

Therefore "fully Bayesian" should be understood in the context of the variables and hyperparameters actually included in the implemented semi-linear framework, rather than as a simultaneous posterior over every astrophysical component.

---

# 28. Uncertainty in the Convergence Map

The linear inversion provides a covariance for the pixelized potential.

However, convergence is related to second derivatives of the potential:

$$
\kappa
=
\frac{1}{2}
\nabla^2\psi.
$$

Propagating correlated potential uncertainties through derivatives into a robust pixel-by-pixel convergence uncertainty is non-trivial.

The paper therefore discusses uncertainty quantification as an area requiring further development.

---

# 29. What the Paper Shows Strongly

The strongest conclusions are:

1. A Matérn-regularized free-form potential correction can recover different classes of mass perturbations within one framework.
2. Bayesian evidence can be used to determine regularization hyperparameters rather than hand-tuning them.
3. Source and potential perturbations can be reconstructed together.
4. The Jackpot data independently require a localized compact perturbation at the location of the previously reported subhalo.
5. The perturbation morphology is more consistent with a highly compact interpretation than with a conventional diffuse NFW interpretation.

---

# 30. What the Paper Does Not Yet Establish as Strongly

The current method does not by itself establish:

1. a precise model-independent NFW concentration such as:

$$
c=200;
$$

2. an unbiased central density or aperture mass for an extremely compact subhalo;
3. complete independence from macro-model assumptions;
4. simultaneous marginalization over all lens-light, source, macro-mass, and free-form components;
5. population-level evidence against cold dark matter from one lens.

A careful interpretation is therefore:

> **The free-form reconstruction provides strong independent evidence for a real and unusually compact perturbation, while precise claims about its density profile and implications for dark matter remain sensitive to remaining modelling systematics.**

---

# 31. A Compact Bayesian Summary of the Entire Method

## Unknown field

$$
\boldsymbol{\delta\psi}.
$$

## Data model

$$
\delta\boldsymbol{d}
=
\mathbf{L}_{\delta\psi}
\boldsymbol{\delta\psi}
+
\boldsymbol{n}.
$$

## Noise

$$
\boldsymbol{n}
\sim
\mathcal{N}
\left(
0,
\mathbf{C}_D
\right).
$$

## Prior

$$
\boldsymbol{\delta\psi}
\sim
\mathcal{N}
\left(
0,
\mathbf{R}_{\delta\psi}^{-1}
\right).
$$

## Matérn precision

$$
\mathbf{R}_{\delta\psi}
=
\lambda^{\delta\psi}
\mathbf{C}_{\delta\psi}^{-1}
(\rho,\nu).
$$

## Posterior

$$
P
\left(
\boldsymbol{\delta\psi}
\mid
\delta\boldsymbol{d},
\lambda^{\delta\psi},
\rho,
\nu
\right)
\propto
P
\left(
\delta\boldsymbol{d}
\mid
\boldsymbol{\delta\psi}
\right)
P
\left(
\boldsymbol{\delta\psi}
\mid
\lambda^{\delta\psi},
\rho,
\nu
\right).
$$

## MAP solution

$$
\boldsymbol{\delta\psi}_{\mathrm{MAP}}
=
\left(
\mathbf{L}_{\delta\psi}^{T}
\mathbf{C}_{D}^{-1}
\mathbf{L}_{\delta\psi}
+
\mathbf{R}_{\delta\psi}
\right)^{-1}
\mathbf{L}_{\delta\psi}^{T}
\mathbf{C}_{D}^{-1}
\delta\boldsymbol{d}.
$$

## Evidence

$$
P
\left(
\delta\boldsymbol{d}
\mid
\lambda^{\delta\psi},
\rho,
\nu
\right)
=
\int
P
\left(
\delta\boldsymbol{d}
\mid
\boldsymbol{\delta\psi}
\right)
P
\left(
\boldsymbol{\delta\psi}
\mid
\lambda^{\delta\psi},
\rho,
\nu
\right)
d\boldsymbol{\delta\psi}.
$$

## Hyperparameter posterior

$$
P
\left(
\lambda^{\delta\psi},
\rho,
\nu
\mid
\delta\boldsymbol{d}
\right)
\propto
P
\left(
\delta\boldsymbol{d}
\mid
\lambda^{\delta\psi},
\rho,
\nu
\right)
P
\left(
\lambda^{\delta\psi},
\rho,
\nu
\right).
$$

That is the statistical core of the paper.

---

# 32. Questions to Ask When Re-Reading the Paper

Use these questions to check whether you genuinely understand the method:

1. Why is the potential correction approximately linear in the image residual?
2. Which physical and numerical ingredients are hidden inside the response matrix?
3. Why is the unregularized inversion ill-posed?
4. Why does a quadratic regularizer correspond to a Gaussian prior?
5. What exactly does the Matérn covariance say about neighbouring potential pixels?
6. Why does increasing the regularization coefficient reduce prior covariance?
7. Why can the potential pixels be solved analytically for fixed hyperparameters?
8. What quantity is integrated out when computing the evidence?
9. Why is evidence not the same as the best chi-square?
10. Why can one globally optimal regularization strength still oversmooth a local subhalo?
11. How can macro-model bias leak into the free-form correction?
12. Which conclusions about the Jackpot perturber are directly free-form, and which rely on comparison with parametric NFW models?

If you can answer those twelve questions in your own words, you understand the main statistical and scientific logic of the paper.

---

# 33. One-Sentence Memory Aid

$$
\boxed{
\text{smooth macro lens}
+
\text{Bayesian pixelized potential correction}
+
\text{Matérn prior}
\rightarrow
\text{flexible test for real mass perturbations}.
}
$$

The main caution is:

$$
\boxed{
\text{global regularization}
\rightarrow
\text{noise suppression}
\quad\text{but also}\quad
\text{oversmoothing of very compact substructure}.
}
$$
