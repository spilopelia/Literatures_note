	**Fisher Matrix — Postgraduate Cheat Sheet**

> [!summary]
> The Fisher matrix is a local map of how strongly the data respond to changes in model parameters.
>
> The core chain is:
>
> $$
> \text{model sensitivity}
> \rightarrow
> F
> \rightarrow
> F^{-1}
> \rightarrow
> \text{parameter uncertainty}
> $$
>
> Main warning:
>
> $$
> \text{Fisher is fundamentally a local Gaussian approximation.}
> $$

---

**1. The three equations to know**

**General definition**

For parameters

$$
\boldsymbol{\theta}=(\theta_1,\ldots,\theta_p),
$$

the Fisher information is

$$
F_{ij}
=
\mathbb{E}\left[
\frac{\partial\ln L}{\partial\theta_i}
\frac{\partial\ln L}{\partial\theta_j}
\right].
$$

Under standard regularity conditions,

$$
F_{ij}
=
-\mathbb{E}\left[
\frac{\partial^2\ln L}
{\partial\theta_i\partial\theta_j}
\right].
$$

Interpretation:

$$
F\sim\text{curvature of }-\ln L.
$$

Large curvature means a narrow likelihood and therefore strong information.

**Gaussian-data special case**

If

$$
\mathbf d
=
\mathbf f(\boldsymbol\theta)
+
\text{Gaussian noise},
$$

with data covariance

$$
C_d,
$$

then

$$
F
=
J^T C_d^{-1}J,
$$

where

$$
J_{ki}
=
\frac{\partial f_k}{\partial\theta_i}.
$$

For independent measurements,

$$
C_d
=
\operatorname{diag}(\sigma_1^2,\ldots,\sigma_N^2),
$$

and therefore

$$
F_{ij}
=
\sum_k
\frac{1}{\sigma_k^2}
\frac{\partial f_k}{\partial\theta_i}
\frac{\partial f_k}{\partial\theta_j}.
$$

**Fisher to covariance**

Under the local Gaussian approximation,

$$
C_\theta\approx F^{-1}.
$$

Therefore the marginalized uncertainty is

$$
\sigma_{\theta_i}
\approx
\sqrt{(F^{-1})_{ii}}.
$$

Do not generally use

$$
\sigma_{\theta_i}
=
\frac{1}{\sqrt{F_{ii}}}.
$$

That is only valid when the parameter is effectively uncorrelated with all others, or when all other parameters are fixed.

---

**2. Physical meaning**

If

$$
\left|\frac{\partial f}{\partial\theta}\right|
$$

is large, a small change in the parameter produces a noticeable change in the data.

Therefore,

$$
\text{large derivative}
\Rightarrow
\text{large Fisher information}
\Rightarrow
\text{small parameter uncertainty}.
$$

If the observational noise increases,

$$
F\propto\frac{1}{\sigma^2}.
$$

A useful verbal summary is:

> Fisher information measures model sensitivity relative to noise.

More precisely, it measures sensitivity times sensitivity, weighted by inverse noise covariance.

---

**3. One measurement contributes an outer product**

For one observable, define

$$
\mathbf g_k
=
\nabla_\theta f_k
=
\begin{pmatrix}
\partial f_k/\partial\theta_1\\
\partial f_k/\partial\theta_2\\
\vdots
\end{pmatrix}.
$$

For independent Gaussian noise,

$$
F^{(k)}
=
\frac{1}{\sigma_k^2}
\mathbf g_k\mathbf g_k^T.
$$

For many independent measurements,

$$
F
=
\sum_k F^{(k)}.
$$

Interpretation:

> Every measurement adds information in the parameter-space direction to which that measurement is sensitive.

---

**4. Why the inverse Fisher matrix becomes a covariance matrix**

Near a fiducial or best-fit point, define

$$
\Delta\boldsymbol\theta
=
\boldsymbol\theta-\boldsymbol\theta_0.
$$

The negative log-likelihood is locally approximated by

$$
-\ln L
\approx
\text{constant}
+
\frac{1}{2}
\Delta\boldsymbol\theta^T
F
\Delta\boldsymbol\theta.
$$

A multivariate Gaussian has the form

$$
P(\boldsymbol\theta)
\propto
\exp\left[
-\frac{1}{2}
\Delta\boldsymbol\theta^T
C^{-1}
\Delta\boldsymbol\theta
\right].
$$

Comparing them gives

$$
F\approx C^{-1},
$$

so

$$
C\approx F^{-1}.
$$

This derivation is more important than simply memorizing the inverse relation.

---

**5. Diagonal and off-diagonal elements**

For two parameters,

$$
F
=
\begin{pmatrix}
F_{11}&F_{12}\\
F_{12}&F_{22}
\end{pmatrix}.
$$

After inversion,

$$
C
=
F^{-1}
=
\begin{pmatrix}
\sigma_1^2&C_{12}\\
C_{12}&\sigma_2^2
\end{pmatrix}.
$$

The diagonal elements of the covariance matrix are marginalized variances.

The off-diagonal elements are covariances.

The correlation coefficient is

$$
\rho_{12}
=
\frac{C_{12}}
{\sqrt{C_{11}C_{22}}}.
$$

It satisfies

$$
-1\le\rho_{12}\le1.
$$

If

$$
|\rho_{12}|\approx1,
$$

the parameters are strongly degenerate.

---

**6. Confidence ellipses and linear algebra**

For two Gaussian parameters, equal-probability contours satisfy

$$
\Delta\boldsymbol\theta^T
C^{-1}
\Delta\boldsymbol\theta
=
\text{constant}.
$$

This is an ellipse.

Decompose the covariance matrix as

$$
C
=
Q\Lambda Q^T,
$$

where

$$
\Lambda
=
\begin{pmatrix}
\lambda_1&0\\
0&\lambda_2
\end{pmatrix}.
$$

The eigenvectors in Q give the ellipse directions.

The eigenvalues give variances along those directions.

Therefore,

$$
\text{eigenvector of }C
=
\text{ellipse direction},
$$

and

$$
\sqrt{\lambda_i}
=
\text{Gaussian width along that direction}.
$$

Equivalent Fisher-space statement:

$$
\text{small eigenvalue of }F
=
\text{poorly constrained parameter combination}.
$$

---

**7. What a degeneracy means**

Suppose the data mainly constrain

$$
\theta_1+\theta_2.
$$

Then the transformation

$$
\theta_1\rightarrow\theta_1+\delta
$$

and

$$
\theta_2\rightarrow\theta_2-\delta
$$

may leave the prediction almost unchanged.

The data therefore cannot distinguish that direction.

The associated Fisher eigenvalue becomes small.

The eigenvector tells you which combination of parameters is weakly constrained.

---

**8. One-dimensional uncertainty versus a joint two-dimensional contour**

For one Gaussian parameter,

$$
|\Delta\theta|\le\sigma
$$

contains approximately 68.3 percent probability.

For a joint two-parameter Gaussian region, the 68.3 percent contour is

$$
\Delta\boldsymbol\theta^T
C^{-1}
\Delta\boldsymbol\theta
=
2.30.
$$

Therefore the semiaxes are

$$
a_i
=
\sqrt{2.30\,\lambda_i}
\approx
1.515\sqrt{\lambda_i}.
$$

Useful values for two joint parameters are

$$
68.3\%\Rightarrow\Delta\chi^2\approx2.30,
$$

and

$$
95\%\Rightarrow\Delta\chi^2\approx5.99.
$$

Always distinguish a marginalized one-dimensional interval from a joint multidimensional contour.

---

**9. Fiducial model**

For a nonlinear model, derivatives generally depend on the parameter values themselves.

Therefore evaluate the Fisher matrix at an assumed fiducial point:

$$
\boldsymbol\theta_{\mathrm{fid}}.
$$

More explicitly,

$$
F_{ij}
=
F_{ij}(\boldsymbol\theta_{\mathrm{fid}}).
$$

For example,

$$
f(x)=e^{-x/x_0},
$$

has derivative

$$
\frac{\partial f}{\partial x_0}
=
\frac{x}{x_0^2}e^{-x/x_0}.
$$

A Fisher forecast does not predict the parameter value.

It answers:

> If the true parameters are near the fiducial values, how accurately could the experiment measure them?

---

**10. Fisher is local**

A first-order Taylor expansion gives

$$
f(\boldsymbol\theta+\Delta\boldsymbol\theta)
\approx
f(\boldsymbol\theta)
+
J\Delta\boldsymbol\theta.
$$

Fisher effectively assumes this local linearization adequately describes the relevant posterior region.

It can fail for:

- strongly curved degeneracies
- banana-shaped posteriors
- multiple modes
- hard parameter boundaries
- strong skewness
- discrete degeneracies
- poorly identifiable parameters
- cases where first derivatives vanish
- strongly non-Gaussian priors

Key warning:

$$
\text{Fisher sees local curvature, not the full global posterior.}
$$

---

**11. Priors**

For a Gaussian prior with covariance

$$
C_{\mathrm{prior}},
$$

the prior Fisher information is

$$
F_{\mathrm{prior}}
=
C_{\mathrm{prior}}^{-1}.
$$

Independent information adds:

$$
F_{\mathrm{total}}
=
F_{\mathrm{likelihood}}
+
F_{\mathrm{prior}}.
$$

Then

$$
C_{\mathrm{posterior}}
=
F_{\mathrm{total}}^{-1}.
$$

For an independent prior

$$
\theta_i
=
\theta_{i,0}
\pm
\sigma_{i,\mathrm{prior}},
$$

add

$$
\frac{1}{\sigma_{i,\mathrm{prior}}^2}
$$

to the corresponding Fisher diagonal.

Bayes gives

$$
\ln P(\boldsymbol\theta\mid d)
=
\ln L
+
\ln P(\boldsymbol\theta)
+
\text{constant},
$$

so the local curvatures add.

---

**12. Nuisance parameters and marginalization**

Suppose

$$
\boldsymbol\theta
=
(\boldsymbol\theta_{\mathrm{science}},\boldsymbol\eta_{\mathrm{nuisance}}).
$$

If a nuisance parameter affects the observables, include it in the Fisher matrix even if it is not scientifically interesting.

To marginalize:

- build the full Fisher matrix
- add priors
- invert the full Fisher matrix
- take the desired science block of the covariance matrix

The crucial distinction is

$$
\text{remove nuisance parameter before inversion}
\Rightarrow
\text{fix it},
$$

whereas

$$
\text{invert first, then remove its covariance row and column}
\Rightarrow
\text{marginalize it}.
$$

---

**13. Schur complement**

If

$$
F
=
\begin{pmatrix}
A&B\\
B^T&D
\end{pmatrix},
$$

where A describes science parameters and D nuisance parameters, then the marginalized science Fisher information is

$$
F_{\mathrm{marg}}
=
A-BD^{-1}B^T.
$$

For one science and one nuisance parameter,

$$
F
=
\begin{pmatrix}
A&B\\
B&D
\end{pmatrix},
$$

so

$$
F_{\mathrm{marg}}
=
A-\frac{B^2}{D}.
$$

Interpretation:

$$
A
=
\text{raw science information},
$$

while

$$
\frac{B^2}{D}
=
\text{information effectively lost because of nuisance degeneracy}.
$$

A stronger prior on the nuisance parameter increases D and reduces this loss.

---

**14. Combining independent experiments**

For statistically independent datasets,

$$
L_{\mathrm{total}}
=
L_1L_2\cdots,
$$

so

$$
F_{\mathrm{total}}
=
F_1+F_2+\cdots.
$$

Different experiments can be complementary.

One may mainly constrain

$$
\theta_1+\theta_2,
$$

while another constrains

$$
\theta_1-\theta_2.
$$

Individually each can be strongly degenerate; together they can determine both parameters well.

Therefore,

$$
\text{different degeneracy directions}
\Rightarrow
\text{strong complementarity}.
$$

---

**15. Shared nuisance parameters**

If two experiments share the same nuisance parameter, do not independently marginalize it out of each experiment first.

Instead:

- construct a common parameter vector
- embed both Fisher matrices in that common parameter space
- add them
- add relevant priors
- invert
- marginalize the shared nuisance parameter afterward

This allows one experiment to help constrain a nuisance parameter that also affects another experiment.

---

**16. Fisher matrix for experimental design**

Before taking data, different experimental designs can have different Fisher matrices:

$$
F(D).
$$

To optimize one parameter, one may minimize

$$
\left[F(D)^{-1}\right]_{ii}.
$$

A criterion for reducing total variance is

$$
\min_D\operatorname{Tr}[F(D)^{-1}].
$$

A criterion for reducing uncertainty volume is

$$
\max_D\det F(D).
$$

Since

$$
\det C
=
\frac{1}{\det F},
$$

maximizing the Fisher determinant approximately minimizes the uncertainty-ellipsoid volume.

---

**17. Fisher forecast versus Fisher-assisted inference**

**Fisher forecast**

Use

$$
C\approx F^{-1}
$$

as the final forecasted covariance.

The Fisher approximation is being used as the answer.

**Fisher-assisted inference**

Run a full MCMC, nested sampler, HMC, or other inference method, but use Fisher information to make the algorithm more efficient.

For example,

$$
\Delta\boldsymbol\theta
\sim
\mathcal N(0,s^2F^{-1}).
$$

Here Fisher helps the algorithm explore the posterior but does not replace the full likelihood.

---

**18. Fisher matrix as a preconditioner**

A highly elongated posterior is difficult to sample in raw coordinates.

Using

$$
F
=
Q\Lambda Q^T,
$$

one can rotate and rescale the coordinates so the local posterior becomes more nearly spherical.

A schematic whitening transformation is

$$
\mathbf z
=
F^{1/2}
(\boldsymbol\theta-\boldsymbol\theta_0).
$$

Locally,

$$
\operatorname{Cov}(\mathbf z)
\approx
I.
$$

Related terms include:

- whitening
- preconditioning
- Fisher reparameterization
- decorrelation
- natural coordinates

---

**19. Natural gradient**

In optimization and variational inference, the natural gradient is

$$
\widetilde{\nabla}
=
F^{-1}\nabla.
$$

The Fisher matrix defines a local statistical distance:

$$
ds^2
=
d\boldsymbol\theta^T
F
d\boldsymbol\theta.
$$

Ordinary gradients measure changes in numerical coordinates.

Natural gradients account for how strongly the probability model itself changes.

---

**20. Expected Fisher versus observed information**

Before seeing the data, a Fisher forecast commonly uses

$$
F_{ij}
=
-\mathbb E\left[
\frac{\partial^2\ln L}
{\partial\theta_i\partial\theta_j}
\right].
$$

This asks how informative the experiment should be on average.

After observing a dataset, one can evaluate

$$
J_{ij}
=
-\left.
\frac{\partial^2\ln L(d_{\mathrm{obs}}\mid\boldsymbol\theta)}
{\partial\theta_i\partial\theta_j}
\right|_{\hat{\boldsymbol\theta}}.
$$

This is often called observed information.

Conceptually,

$$
\text{expected Fisher}
=
\text{forecast before seeing the data},
$$

while

$$
\text{observed information}
=
\text{curvature for the actual dataset}.
$$

---

**21. Units**

If parameter i has units

$$
U_i,
$$

then

$$
F_{ij}
$$

has units

$$
\frac{1}{U_iU_j}.
$$

Consequently,

$$
(F^{-1})_{ij}
$$

has units

$$
U_iU_j.
$$

This is useful for checking derivations and code.

---

**22. Singular and nearly singular Fisher matrices**

If

$$
\det F=0,
$$

at least one parameter combination is unconstrained.

Equivalently, at least one Fisher eigenvalue is zero:

$$
\lambda_i=0.
$$

Possible causes include:

- too few independent observables
- two parameters affecting the model in nearly the same way
- nuisance-parameter degeneracy
- inappropriate parameterization
- zero or inaccurate numerical derivatives
- missing prior information
- a genuine physical degeneracy

Do not immediately treat singularity as only a numerical problem. It may be scientifically meaningful.

---

**23. Condition number**

A useful diagnostic is

$$
\kappa(F)
=
\frac{\lambda_{\max}}{\lambda_{\min}}.
$$

If

$$
\kappa(F)\gg1,
$$

the inference geometry is highly anisotropic or poorly conditioned.

This can indicate:

- strong parameter degeneracy
- unstable numerical inversion
- inefficient sampling
- badly scaled parameters

In practice, eigendecomposition or singular-value decomposition is often safer than blindly applying a matrix inverse.

---

**24. Numerical derivatives**

If analytic derivatives are unavailable, a common central finite-difference approximation is

$$
\frac{\partial f}{\partial\theta_i}
\approx
\frac{f(\theta_i+h)-f(\theta_i-h)}{2h}.
$$

If h is too large, the derivative is not sufficiently local.

If h is too small, floating-point errors or numerical noise can dominate.

A serious Fisher analysis should test convergence with respect to derivative step size.

Automatic differentiation is preferable when available.

---

**25. Parameter scaling**

If one parameter is naturally of order

$$
10^{-8},
$$

while another is of order

$$
10^6,
$$

the Fisher matrix can become numerically poorly conditioned even when the physical problem is well behaved.

Scaled dimensionless parameters can help:

$$
q_i
=
\frac{\theta_i}{\theta_{i,\mathrm{scale}}}.
$$

For positive scale parameters, logarithmic coordinates can also be useful:

$$
\phi=\ln\theta.
$$

The physics should not depend on parameterization, but numerical stability can.

---

**26. Reparameterization**

If new parameters are

$$
\boldsymbol\phi
=
\boldsymbol\phi(\boldsymbol\theta),
$$

define

$$
J_{ij}
=
\frac{\partial\theta_i}{\partial\phi_j}.
$$

Then

$$
F_\phi
=
J^TF_\theta J.
$$

The numerical matrix changes because the coordinates change, but the underlying local information geometry is the same.

---

**27. Fisher matrix versus Hessian**

The Hessian of the negative log-likelihood is

$$
H_{ij}
=
-\frac{\partial^2\ln L}
{\partial\theta_i\partial\theta_j}.
$$

The Fisher information is the expected Hessian:

$$
F
=
\mathbb E[H].
$$

Near a well-behaved maximum with sufficient data,

$$
H_{\mathrm{observed}}\approx F.
$$

They are closely related but not conceptually identical.

---

**28. Fisher matrix versus Laplace approximation**

A Laplace approximation takes the actual posterior near its mode and approximates it as Gaussian:

$$
P(\boldsymbol\theta\mid d)
\approx
\mathcal N(\hat{\boldsymbol\theta},H^{-1}).
$$

A Fisher forecast usually evaluates expected information around a fiducial model before observing the particular data realization.

Both rely on local quadratic or Gaussian behavior.

---

**29. Cramér–Rao bound**

Under suitable regularity conditions, for an unbiased estimator,

$$
\operatorname{Cov}(\hat{\boldsymbol\theta})
\succeq
F^{-1}.
$$

In one dimension,

$$
\operatorname{Var}(\hat\theta)
\ge
\frac{1}{F}.
$$

The Fisher information sets a lower bound on the variance of an unbiased estimator.

Do not interpret every Fisher forecast as a guaranteed achievable error bar; the assumptions matter.

---

**30. Checklist when reading a Fisher-matrix paper**

Ask:

- What are the model parameters?
- What are the observables?
- What likelihood or noise model is assumed?
- What fiducial parameter values are used?
- How are derivatives calculated?
- Which parameters are scientifically interesting?
- Which are nuisance parameters?
- Which parameters are fixed?
- Which parameters are marginalized?
- What priors are included?
- Are datasets truly independent?
- Are nuisance parameters shared between datasets?
- Is the Fisher matrix well conditioned?
- What are the smallest eigenvalues and associated eigenvectors?
- Is Fisher being used as the final forecast?
- Or is Fisher only being used to accelerate full inference?
- Is the local Gaussian approximation plausible?
- Has the result been validated against simulations, MCMC, or nested sampling?

---

**31. Standard workflow**

Given

$$
d_k
=
f_k(\boldsymbol\theta)+n_k,
$$

choose fiducial parameters:

$$
\boldsymbol\theta_{\mathrm{fid}}.
$$

Evaluate the Jacobian:

$$
J_{ki}
=
\left.
\frac{\partial f_k}{\partial\theta_i}
\right|_{\boldsymbol\theta_{\mathrm{fid}}}.
$$

Construct the data Fisher matrix:

$$
F_{\mathrm{data}}
=
J^T C_d^{-1}J.
$$

Add priors:

$$
F_{\mathrm{total}}
=
F_{\mathrm{data}}+F_{\mathrm{prior}}.
$$

Invert:

$$
C_\theta
=
F_{\mathrm{total}}^{-1}.
$$

Read marginalized uncertainties:

$$
\sigma_i
=
\sqrt{(C_\theta)_{ii}}.
$$

Compute correlations:

$$
\rho_{ij}
=
\frac{(C_\theta)_{ij}}
{\sqrt{(C_\theta)_{ii}(C_\theta)_{jj}}}.
$$

For nuisance parameters, invert the full matrix first and then select the desired science covariance block.

---

**32. Conceptual reconstruction when you forget the formulas**

If you forget the details, rebuild the idea from this chain:

$$
\text{change a parameter}
$$

$$
\downarrow
$$

$$
\text{prediction changes}
$$

$$
\downarrow
$$

$$
\frac{\partial f}{\partial\theta}
$$

$$
\downarrow
$$

$$
\text{compare the prediction change with observational noise}
$$

$$
\downarrow
$$

$$
F
=
J^T C_d^{-1}J
$$

$$
\downarrow
$$

$$
F
=
\text{local information geometry}
$$

$$
\downarrow
$$

$$
F^{-1}
=
\text{approximate uncertainty geometry}.
$$

The covariance diagonal gives parameter variances.

The off-diagonal elements give covariances.

The eigenvectors give degeneracy directions.

The eigenvalues give constraint strength along those directions.

---

**33. Minimum set to memorize**

General Fisher information:

$$
F_{ij}
=
-\mathbb E\left[
\frac{\partial^2\ln L}
{\partial\theta_i\partial\theta_j}
\right].
$$

Gaussian-data Fisher:

$$
F
=
J^T C_d^{-1}J.
$$

Approximate covariance:

$$
C_\theta\approx F^{-1}.
$$

Independent information adds:

$$
F_{\mathrm{total}}
=
\sum_{\mathrm{experiments}}F_e
+
F_{\mathrm{prior}}.
$$

Marginalization rule:

$$
\text{invert first, then keep the desired covariance block}.
$$

Degeneracy rule:

$$
\text{small eigenvalue of }F
=
\text{poorly constrained parameter combination}.
$$

Main limitation:

$$
\text{Fisher is local; always question the Gaussian approximation.}
$$

> [!important]
> If these ideas are understood rather than merely memorized, they are sufficient to follow most uses of Fisher matrices in astrophysics, cosmology, gravitational-wave inference, and experimental design.
