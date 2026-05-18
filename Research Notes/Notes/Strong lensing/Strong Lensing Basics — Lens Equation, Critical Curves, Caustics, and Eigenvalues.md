---
title: "Strong Lensing Basics — Lens Equation, Critical Curves, Caustics, and Eigenvalues"
tags:
  - strong-lensing
  - gravitational-lensing
  - lens-equation
  - critical-curve
  - caustic
---

# Strong Lensing Basics

## 1. Basic Geometry

In strong gravitational lensing, a foreground mass distribution deflects light from a background source.

The main coordinate systems are:

| Symbol | Meaning |
|---|---|
| $$\boldsymbol{\theta}$$ | angular position in the image / lens plane |
| $$\boldsymbol{\beta}$$ | angular position in the source plane |
| $$\boldsymbol{\alpha}(\boldsymbol{\theta})$$ | deflection angle |
| $$\psi(\boldsymbol{\theta})$$ | lensing potential |
| $$\kappa(\boldsymbol{\theta})$$ | convergence, dimensionless projected surface mass density |

The lens equation is:

$$
\boldsymbol{\beta}
=
\boldsymbol{\theta}
-
\boldsymbol{\alpha}(\boldsymbol{\theta}).
$$

The deflection is related to the lensing potential by:

$$
\boldsymbol{\alpha}(\boldsymbol{\theta})
=
\nabla_{\boldsymbol{\theta}} \psi(\boldsymbol{\theta}).
$$

The convergence is:

$$
\kappa(\boldsymbol{\theta})
=
\frac{1}{2}
\nabla^2 \psi(\boldsymbol{\theta}).
$$

Physically, the lens equation maps every image-plane position $$\boldsymbol{\theta}$$ back to a source-plane position $$\boldsymbol{\beta}$$.

---

## 2. Jacobian Matrix

The local behavior of the lens mapping is described by the Jacobian matrix:

$$
A
=
\frac{\partial \boldsymbol{\beta}}
{\partial \boldsymbol{\theta}}.
$$

Using the lens equation:

$$
\boldsymbol{\beta}
=
\boldsymbol{\theta}
-
\nabla \psi,
$$

we get:

$$
A_{ij}
=
\delta_{ij}
-
\frac{\partial^2 \psi}
{\partial \theta_i \partial \theta_j}.
$$

In terms of convergence $$\kappa$$ and shear components $$\gamma_1,\gamma_2$$:

$$
A
=
\begin{pmatrix}
1-\kappa-\gamma_1 & -\gamma_2 \\
-\gamma_2 & 1-\kappa+\gamma_1
\end{pmatrix}.
$$

The determinant is:

$$
\det A
=
(1-\kappa)^2
-
\gamma^2,
$$

where:

$$
\gamma^2
=
\gamma_1^2+\gamma_2^2.
$$

---

## 3. Magnification

The Jacobian tells us how a small image-plane area maps to the source plane:

$$
d^2\beta
=
|\det A|\,d^2\theta.
$$

Therefore, the magnification is:

$$
\mu
=
\frac{\text{image area}}
{\text{source area}}
=
\frac{d^2\theta}{d^2\beta}
=
\frac{1}{|\det A|}.
$$

The signed magnification is:

$$
\mu
=
\frac{1}{\det A}.
$$

Therefore:

$$
\det A = 0
\quad \Rightarrow \quad
|\mu| \rightarrow \infty.
$$

This is the mathematical reason why critical curves are defined by:

$$
\det A = 0.
$$

In real observations, magnification is finite because sources have finite size, PSF convolution smooths the image, and the lens model is not perfectly singular.

---

## 4. Eigenvalues and Eigenvectors of the Lens Mapping

The matrix $$A$$ has two eigenvalues and two eigenvectors.

The eigenvectors give the local principal directions of distortion. The eigenvalues give the local mapping factors from image plane to source plane along those directions.

For a locally circular or nearly circular lens, the two important directions are:

| Direction | Eigenvalue | Physical meaning |
|---|---|---|
| radial direction | $$\lambda_r$$ | toward or away from the lens center |
| tangential direction | $$\lambda_t$$ | around the lens center |

The determinant is the product of the eigenvalues:

$$
\det A
=
\lambda_r \lambda_t.
$$

Thus:

$$
\mu
=
\frac{1}{\lambda_r\lambda_t}.
$$

If one eigenvalue approaches zero, magnification becomes very large.

---

## 5. Tangential and Radial Critical Curves

A critical curve occurs where:

$$
\det A = 0.
$$

Since:

$$
\det A
=
\lambda_r\lambda_t,
$$

there are two possible types of critical curves.

### Tangential Critical Curve

The tangential critical curve satisfies:

$$
\lambda_t = 0.
$$

This means the image is highly stretched in the tangential direction.

It produces:

- tangential arcs;
- partial Einstein rings;
- full Einstein rings in nearly symmetric systems.

This is the most common type of critical curve in galaxy-scale strong lensing.

### Radial Critical Curve

The radial critical curve satisfies:

$$
\lambda_r = 0.
$$

This means the image is highly stretched in the radial direction.

It produces:

- radial arcs;
- images elongated toward or away from the lens center.

Radial arcs are usually closer to the lens center and less common than tangential arcs.

---

## 6. Axisymmetric Lens Case

For a circular lens, define:

$$
R = |\boldsymbol{\theta}|.
$$

The deflection is radial:

$$
\boldsymbol{\alpha}(\boldsymbol{\theta})
=
\alpha(R)\hat{\boldsymbol{e}}_R.
$$

The lens equation becomes:

$$
\beta(R)
=
R-\alpha(R).
$$

### Tangential Eigenvalue

A small tangential displacement in the image plane has length:

$$
ds_{\theta}
=
R\,d\phi.
$$

The corresponding source-plane radius is:

$$
\beta(R)
=
R-\alpha(R).
$$

So the source-plane tangential length is:

$$
ds_{\beta}
=
\beta(R)d\phi
=
[R-\alpha(R)]d\phi.
$$

Therefore:

$$
\lambda_t
=
\frac{ds_{\beta}}{ds_{\theta}}
=
\frac{[R-\alpha(R)]d\phi}{R\,d\phi}
=
1-\frac{\alpha(R)}{R}.
$$

Thus:

$$
\lambda_t(R)
=
1-\frac{\alpha(R)}{R}.
$$

### Radial Eigenvalue

For a small radial displacement:

$$
\beta(R)
=
R-\alpha(R).
$$

Differentiate:

$$
d\beta
=
\left(
1-\frac{d\alpha}{dR}
\right)dR.
$$

Therefore:

$$
\lambda_r(R)
=
1-\frac{d\alpha}{dR}.
$$

---

## 7. Relation to Convergence

For an axisymmetric lens, the dimensionless mass enclosed inside radius $$R$$ is:

$$
m(R)
=
2\int_0^R \kappa(r)r\,dr.
$$

The deflection is:

$$
\alpha(R)
=
\frac{m(R)}{R}.
$$

The mean convergence inside $$R$$ is:

$$
\bar{\kappa}(<R)
=
\frac{2}{R^2}
\int_0^R \kappa(r)r\,dr
=
\frac{m(R)}{R^2}.
$$

Therefore:

$$
\frac{\alpha(R)}{R}
=
\frac{m(R)}{R^2}
=
\bar{\kappa}(<R).
$$

So the tangential eigenvalue becomes:

$$
\lambda_t(R)
=
1-\bar{\kappa}(<R).
$$

The tangential critical curve satisfies:

$$
\lambda_t = 0
\quad \Rightarrow \quad
\bar{\kappa}(<R)=1.
$$

This is the Einstein-radius condition for an axisymmetric lens.

For the radial eigenvalue:

$$
\lambda_r(R)
=
1-\frac{d\alpha}{dR}.
$$

Since:

$$
\alpha(R)
=
\frac{m(R)}{R},
$$

we have:

$$
\frac{d\alpha}{dR}
=
\frac{1}{R}\frac{dm}{dR}
-
\frac{m(R)}{R^2}.
$$

Because:

$$
\frac{dm}{dR}
=
2\kappa(R)R,
$$

we get:

$$
\frac{d\alpha}{dR}
=
2\kappa(R)
-
\bar{\kappa}(<R).
$$

Therefore:

$$
\lambda_r(R)
=
1
-
2\kappa(R)
+
\bar{\kappa}(<R).
$$

Final axisymmetric expressions:

$$
\lambda_t(R)
=
1-\bar{\kappa}(<R),
$$

$$
\lambda_r(R)
=
1-2\kappa(R)+\bar{\kappa}(<R).
$$

---

## 8. Critical Curves and Caustics

A critical curve is defined in the image plane by:

$$
\det A(\boldsymbol{\theta})=0.
$$

A caustic is the mapping of the critical curve into the source plane using the lens equation:

$$
\boldsymbol{\beta}_{\rm caustic}
=
\boldsymbol{\theta}_{\rm crit}
-
\boldsymbol{\alpha}(\boldsymbol{\theta}_{\rm crit}).
$$

Thus:

| Object | Plane | Definition |
|---|---|---|
| Critical curve | image/lens plane | where $$\det A=0$$ |
| Caustic | source plane | image of the critical curve under the lens equation |

A source near a caustic produces highly magnified images near the corresponding critical curve.

Compact relation:

$$
\text{source near caustic}
\quad \Rightarrow \quad
\text{image near critical curve}
\quad \Rightarrow \quad
\text{large magnification}.
$$

---

## 9. Why Elliptical Critical Curves Map to Diamond-Shaped Caustics

For a circular lens, the tangential critical curve is a circle:

$$
R = R_E.
$$

For a circular lens, all points on the tangential critical curve map to the same source-plane point:

$$
\boldsymbol{\beta}=0.
$$

So:

$$
\text{circular critical curve}
\rightarrow
\text{point caustic}.
$$

When ellipticity or external shear is added, circular symmetry is broken. The critical curve becomes distorted, and its mapping through the nonlinear lens equation produces a four-cusped caustic.

The dominant angular distortion is quadrupolar, roughly involving angular modes like:

$$
\cos 2\phi,
\qquad
\sin 2\phi.
$$

This produces four preferred directions and therefore four cusps.

For simple elliptical or shear-perturbed lenses, the tangential caustic often resembles an astroid:

$$
\beta_1 \propto \cos^3\phi,
$$

$$
\beta_2 \propto \sin^3\phi.
$$

This gives the familiar diamond-like caustic.

---

## 10. Interpretation of Typical Strong-Lensing Plots

In a source-plane plot:

- the source is plotted in $$\boldsymbol{\beta}$$ coordinates;
- the caustic shows where sources produce highly magnified multiple images;
- if the source overlaps or lies near the caustic, strong arcs appear in the image plane.

In an image-plane plot:

- the lensed image is plotted in $$\boldsymbol{\theta}$$ coordinates;
- the critical curve marks where the magnification formally diverges;
- arcs tend to lie close to the critical curve.

For an SIE-like lens:

- the image-plane critical curve is approximately elliptical;
- the source-plane caustic is diamond-shaped;
- sources near the caustic are mapped into tangential arcs around the critical curve.

---

## 11. Compact Summary

The lens equation is:

$$
\boldsymbol{\beta}
=
\boldsymbol{\theta}
-
\boldsymbol{\alpha}(\boldsymbol{\theta}).
$$

The Jacobian is:

$$
A
=
\frac{\partial \boldsymbol{\beta}}
{\partial \boldsymbol{\theta}}.
$$

The magnification is:

$$
\mu
=
\frac{1}{\det A}.
$$

Critical curves satisfy:

$$
\det A = 0.
$$

Caustics are critical curves mapped to the source plane:

$$
\boldsymbol{\beta}_{\rm caustic}
=
\boldsymbol{\theta}_{\rm crit}
-
\boldsymbol{\alpha}(\boldsymbol{\theta}_{\rm crit}).
$$

The eigenvalues satisfy:

$$
\det A
=
\lambda_r\lambda_t.
$$

Tangential arcs occur when:

$$
\lambda_t \approx 0.
$$

Radial arcs occur when:

$$
\lambda_r \approx 0.
$$

For a circular lens:

$$
\lambda_t
=
1-\bar{\kappa}(<R),
$$

$$
\lambda_r
=
1-2\kappa(R)+\bar{\kappa}(<R).
$$