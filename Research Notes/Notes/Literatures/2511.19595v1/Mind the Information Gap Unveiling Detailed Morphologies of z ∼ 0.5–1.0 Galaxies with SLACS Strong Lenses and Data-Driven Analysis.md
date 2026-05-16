---
title: "Mind the Information Gap — SLACS Strong Lenses with Data-Driven Priors"
authors:
  - Ronan Legin
  - Connor Stone
  - Alexandre Adam
  - Gabriel M. Barco
  - Adam Coogan
  - Nikolay Malkin
  - Laurence Perreault-Levasseur
  - Yashar Hezaveh
year: 2025
arxiv: "2511.19595"
tags:
  - strong-lensing
  - source-reconstruction
  - score-based-priors
  - lens-light
  - SLACS
---

# Mind the Information Gap — SLACS Strong Lenses with Data-Driven Priors

## Summary

This paper analyzes real SLACS strong-lensing systems using data-driven score-based priors for the background source, foreground lens light, and PSF. The goal is to recover detailed source morphologies of galaxies at \(z \sim 0.5-1.0\) while accounting for uncertainty in the lensing reconstruction.

The lens mass model is still parametric, while the source, lens light, and PSF are modeled as high-dimensional image-like components with learned priors.

---

## Main Problem

The observed lens image contains several mixed components:

$$
y = \mathcal{P}\left[\mathcal{L}_{\theta}(s) + l\right] + n
$$

where:

| Symbol | Meaning |
|---|---|
| \(y\) | observed image |
| \(s\) | background source light |
| \(l\) | foreground lens light |
| \(\theta\) | parametric lens-mass parameters |
| \(\mathcal{L}_{\theta}\) | lensing operator |
| \(\mathcal{P}\) | PSF convolution |
| \(n\) | observational noise |

The corresponding model prediction is:

$$
\hat{y}
=
\mathcal{P}\left[\mathcal{L}_{\theta}(s) + l\right].
$$

For Gaussian noise, the likelihood is:

$$
p(y \mid s,l,\theta,\mathrm{PSF})
\propto
\exp
\left[
-\frac{1}{2}
\left\|
\frac{y - \hat{y}}{\sigma}
\right\|_2^2
\right].
$$

---

## Posterior

The full posterior can be written schematically as:

$$
p(s,l,\theta,\mathrm{PSF} \mid y)
\propto
p(y \mid s,l,\theta,\mathrm{PSF})
p(s)
p(l)
p(\mathrm{PSF})
p(\theta).
$$

The important modeling split is:

| Component | Treatment |
|---|---|
| Source \(s\) | learned score-based prior |
| Lens light \(l\) | learned score-based prior |
| PSF | learned score-based prior |
| Lens mass \(\theta\) | parametric lens model |

Thus, the method uses high-dimensional learned priors for light and PSF components, but not for a pixelated convergence field.

---

## Score-Based Priors

For an image-like component \(x\), a score model estimates:

$$
\nabla_x \log p_t(x),
$$

where \(p_t(x)\) is the noisy data distribution at diffusion time \(t\).

In posterior sampling, the score of the posterior can be written conceptually as:

$$
\nabla_x \log p(x \mid y)
=
\nabla_x \log p(y \mid x)
+
\nabla_x \log p(x).
$$

The learned score prior encourages the sampled source, lens light, or PSF to remain consistent with realistic examples from the training distribution.

---

## Likelihood Gradient

For Gaussian noise,

$$
\log p(y \mid x)
=
-\frac{1}{2}
\left\|
\frac{y - \hat{y}(x)}{\sigma}
\right\|_2^2
+ C.
$$

The likelihood gradient is:

$$
\nabla_x \log p(y \mid x)
=
\left(
\frac{\partial \hat{y}}{\partial x}
\right)^T
\frac{y - \hat{y}}{\sigma^2}.
$$

So the residual

$$
r = y - \hat{y}
$$

is backpropagated through the differentiable forward model.

For the source:

$$
s
\rightarrow
\mathcal{L}_{\theta}(s)
\rightarrow
\mathcal{P}[\mathcal{L}_{\theta}(s)]
\rightarrow
\hat{y}
\rightarrow
y - \hat{y}.
$$

For the lens light:

$$
l
\rightarrow
\mathcal{P}[l]
\rightarrow
\hat{y}
\rightarrow
y - \hat{y}.
$$

For the lens parameters:

$$
\theta
\rightarrow
\alpha_{\theta}
\rightarrow
\beta = \theta_{\rm img} - \alpha_{\theta}(\theta_{\rm img})
\rightarrow
s(\beta)
\rightarrow
\hat{y}
\rightarrow
y - \hat{y}.
$$

---

## Source–Lens-Light Degeneracy

The observed image is the sum of lensed source light and foreground lens light:

$$
y \approx \mathcal{P}\left[\mathcal{L}_{\theta}(s) + l\right].
$$

Therefore, some image flux can be explained by either changing the source or changing the lens light:

$$
\mathcal{L}_{\theta}(s + \Delta s) + l
\approx
\mathcal{L}_{\theta}(s) + (l + \Delta l).
$$

Equivalently,

$$
\mathcal{L}_{\theta}(\Delta s)
\approx
\Delta l.
$$

This degeneracy is strongest where the lensed source and lens light overlap, especially near bright arcs.

The learned priors \(p(s)\) and \(p(l)\) constrain this decomposition by favoring realistic source morphologies and realistic foreground lens-light morphologies.

---

## Posterior Sampling Interpretation

The paper emphasizes posterior sampling rather than only producing a single best-fit reconstruction.

Given samples:

$$
s^{(1)}, s^{(2)}, \dots, s^{(N)}
\sim
p(s \mid y),
$$

the posterior mean is:

$$
\bar{s}
=
\frac{1}{N}
\sum_{i=1}^{N}
s^{(i)}.
$$

The posterior variance is:

$$
\mathrm{Var}[s]
=
\frac{1}{N}
\sum_{i=1}^{N}
\left(s^{(i)} - \bar{s}\right)^2.
$$

Features that persist across posterior samples are interpreted as more strongly supported by the data, while features that vary across samples are more uncertain or prior-dependent.

---

## Methodological Structure

The analysis combines:

1. A parametric lens-mass model.
2. A learned source prior.
3. A learned lens-light prior.
4. A learned PSF prior.
5. A Gaussian image likelihood.
6. Posterior sampling using score-based methods.

The key posterior is:

$$
p(s,l,\theta,\mathrm{PSF} \mid y).
$$

The method therefore treats source reconstruction, lens-light subtraction, PSF modeling, and lens modeling as a joint inference problem rather than as fully separate preprocessing steps.

---

## Main Contribution

The paper demonstrates that data-driven score-based priors can be applied to real SLACS strong lenses to infer detailed background source morphologies while jointly modeling foreground lens light and PSF uncertainty.

The main scientific motivation is to recover high-resolution morphology of lensed galaxies beyond what is directly accessible from the observed image.

---

## Main Limitation

The lens mass model remains parametric. Therefore, the recovered source morphology can still be affected by lens-model assumptions.

If the true lens mass differs from the assumed parametric family,

$$
\theta_{\rm true} \neq \theta_{\rm parametric},
$$

then source reconstruction may absorb lens-model errors:

$$
s_{\rm recon}
=
s_{\rm true}
+
\delta s_{\rm lens\ model}.
$$

This is a limitation for applications where flexible or pixelated mass reconstruction is required.

---

## Relevance

This paper is useful as an example of real-data strong-lensing inference with learned priors. Its main relevance is the joint treatment of source light, lens light, PSF, and lens parameters within a probabilistic framework.

The most relevant idea is that foreground lens light is not merely a preprocessing nuisance; it directly affects source reconstruction through the additive image model:

$$
\hat{y}
=
\mathcal{P}\left[\mathcal{L}_{\theta}(s) + l\right].
$$

Errors in \(l\) can bias \(s\), and errors in \(s\) can bias the inferred lens-light component.

---

## Compact Takeaway

The paper extends score-based strong-lensing reconstruction to real SLACS data by jointly modeling source light, lens light, PSF, and parametric lens mass. Its central idea is that learned priors help regularize high-dimensional components while posterior sampling exposes uncertainty and degeneracy in the reconstruction.

The main methodological limitation is that the lens mass remains parametric rather than a fully pixelated convergence field.