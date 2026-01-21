
---

## 1. Basic Strong Lensing Setup

Lens equation:
$$
\boldsymbol\beta=\boldsymbol\theta-\boldsymbol\alpha(\boldsymbol\theta),
\qquad 
\boldsymbol\alpha(\boldsymbol\theta)=\nabla\psi(\boldsymbol\theta).
$$

Convergence:
$$
\kappa(\boldsymbol\theta)=\frac12\nabla^2\psi(\boldsymbol\theta).
$$

Critical surface density and convergence definition:
$$
\kappa(\boldsymbol\theta)=\frac{\Sigma(\boldsymbol\theta)}{\Sigma_{\rm crit}(z_d,z_s)},
\qquad
\Sigma_{\rm crit}=\frac{c^2}{4\pi G}\frac{D_s}{D_d\,D_{ds}}.
$$

---

## 2. Jacobian / Magnification

Jacobian of the lens mapping:
$$
A(\boldsymbol\theta)\equiv \frac{\partial\boldsymbol\beta}{\partial\boldsymbol\theta}.
$$

Magnification:
$$
\mu(\boldsymbol\theta)=\frac{1}{\det A(\boldsymbol\theta)}.
$$

Critical curves are where:
$$
\det A(\boldsymbol\theta)=0.
$$

---

## 3. Mass-Sheet Transformation (MST) / Mass-Sheet Degeneracy (MSD)

MST in convergence form:
$$
\kappa'(\boldsymbol\theta)=\lambda\,\kappa(\boldsymbol\theta)+(1-\lambda).
$$

Deflection transformation:
$$
\boldsymbol\alpha'(\boldsymbol\theta)=\lambda\,\boldsymbol\alpha(\boldsymbol\theta)+(1-\lambda)\boldsymbol\theta.
$$

Source-plane rescaling:
$$
\boldsymbol\beta'=\lambda\,\boldsymbol\beta.
$$

Potential transformation:
$$
\psi'(\boldsymbol\theta)=\lambda\,\psi(\boldsymbol\theta)+\frac{1-\lambda}{2}|\boldsymbol\theta|^2+\text{const}.
$$

Magnification scaling:
$$
\mu'=\frac{\mu}{\lambda^2}.
$$

Time-delay scaling:
$$
\Delta t'=\lambda\,\Delta t.
$$

Physical surface density form (shows redshift dependence via $\Sigma_{\rm crit}$):
$$
\Sigma'(\boldsymbol\theta)=\lambda\,\Sigma(\boldsymbol\theta)+(1-\lambda)\,\Sigma_{\rm crit}(z_d,z_s),
\qquad
\Sigma_{\rm sheet}=(1-\lambda)\Sigma_{\rm crit}(z_d,z_s).
$$

---

## 4. Einstein Radius and MST

Axisymmetric Einstein radius condition:
$$
\alpha(\theta_E)=\theta_E
\quad\Longleftrightarrow\quad
\beta(\theta_E)=\theta_E-\alpha(\theta_E)=0.
$$

Mean convergence condition (axisymmetry):
$$
\bar\kappa(\theta_E)=1,
\qquad
\bar\kappa(\theta)=\frac{2}{\theta^2}\int_0^\theta \kappa(\theta')\,\theta'\,d\theta'.
$$

Einstein radius invariance under MST:
$$
\alpha'(\theta)=\lambda\alpha(\theta)+(1-\lambda)\theta
\;\Rightarrow\;
\alpha'(\theta_E)=\lambda\theta_E+(1-\lambda)\theta_E=\theta_E.
$$

Enclosed mass changes (physical units):
$$
M'(<\theta_E)=\lambda\,M(<\theta_E)+(1-\lambda)\,\pi(D_d\theta_E)^2\,\Sigma_{\rm crit}.
$$

---

## 5. Source-Position Transformation (SPT)

General SPT definition:
$$
\hat{\boldsymbol\beta}=\hat{\boldsymbol\beta}(\boldsymbol\beta),
\qquad
\hat{\boldsymbol\alpha}(\boldsymbol\theta)=\boldsymbol\theta-\hat{\boldsymbol\beta}(\boldsymbol\beta(\boldsymbol\theta)).
$$

MST is the special case:
$$
\hat{\boldsymbol\beta}=\lambda\boldsymbol\beta.
$$

### Jacobian chain rule (key matrix identity)

Define:
$$
A(\boldsymbol\theta)=\frac{\partial\boldsymbol\beta}{\partial\boldsymbol\theta},
\qquad
B(\boldsymbol\beta)=\frac{\partial\hat{\boldsymbol\beta}}{\partial\boldsymbol\beta},
\qquad
\hat A(\boldsymbol\theta)=\frac{\partial\hat{\boldsymbol\beta}}{\partial\boldsymbol\theta}.
$$

Then by chain rule:
$$
\hat A(\boldsymbol\theta)=B(\boldsymbol\beta(\boldsymbol\theta))\,A(\boldsymbol\theta).
$$

Taking determinants:
$$
\det\hat A(\boldsymbol\theta)=(\det B(\boldsymbol\beta(\boldsymbol\theta)))\,(\det A(\boldsymbol\theta)).
$$

### “Same $B$ for multiple images of the same source”

If $\theta_1,\theta_2$ are images of the same source point $\beta_s$:
$$
\beta(\theta_1)=\beta(\theta_2)=\beta_s
\quad\Rightarrow\quad
B(\beta(\theta_1))=B(\beta(\theta_2))=B(\beta_s).
$$

Relative linear mapping invariance:
$$
\hat A(\theta_1)\hat A(\theta_2)^{-1}=A(\theta_1)A(\theta_2)^{-1}.
$$

Magnification ratio invariance:
$$
\hat\mu(\theta)=\frac{1}{\det\hat A(\theta)},\qquad
\frac{\hat\mu(\theta_1)}{\hat\mu(\theta_2)}=
\frac{\mu(\theta_1)}{\mu(\theta_2)}.
$$

### Extended source brightness relabeling

Observed image brightness:
$$
I(\boldsymbol\theta)=S(\boldsymbol\beta(\boldsymbol\theta)).
$$

Under SPT coordinate remapping $\hat{\boldsymbol\beta}=f(\boldsymbol\beta)$, define:
$$
\hat S(\hat{\boldsymbol\beta})=S(f^{-1}(\hat{\boldsymbol\beta})).
$$

Then:
$$
I(\boldsymbol\theta)=S(\boldsymbol\beta(\boldsymbol\theta))=\hat S(\hat{\boldsymbol\beta}(\boldsymbol\theta)).
$$

---

## 6. Why SPT is Exact in Axisymmetry but Only Approximate in General

Physical lensing requires:
$$
\boldsymbol\alpha(\boldsymbol\theta)=\nabla\psi(\boldsymbol\theta)
\quad\Rightarrow\quad
\nabla\times\boldsymbol\alpha=0.
$$

Generic SPT construction can produce:
$$
\nabla\times\hat{\boldsymbol\alpha}\neq 0,
$$
so no physical potential $\hat\psi$ exists exactly (hence approximate in non-axisymmetric case). In axisymmetry, the mapping is effectively 1D radial so this obstruction disappears.

---

## 7. Axisymmetric Lens Relations (Scalars)

Axisymmetric lens equation:
$$
\beta(\theta)=\theta-\alpha(\theta).
$$

Enclosed (dimensionless) mass definition (paper convention):
$$
m(\theta)=2\int_0^\theta \theta'\,\kappa(\theta')\,d\theta'.
$$

Deflection–mass relation:
$$
\alpha(\theta)=\frac{m(\theta)}{\theta}.
$$

Derivative identity:
$$
m'(\theta)=2\theta\kappa(\theta).
$$

From $\alpha=m/\theta$:
$$
\alpha'(\theta)=\frac{m'(\theta)}{\theta}-\frac{m(\theta)}{\theta^2}
=2\kappa(\theta)-\frac{\alpha(\theta)}{\theta}.
$$

Eigenvalues of $A$:
$$
\lambda_t=1-\frac{\alpha}{\theta}=\frac{\theta-\alpha}{\theta},
\qquad
\lambda_r=1-\alpha'.
$$

Determinant:
$$
\det A=\lambda_t\lambda_r=\frac{\theta-\alpha}{\theta}(1-\alpha').
$$

Useful product:
$$
\theta^2\det A=\theta(\theta-\alpha)(1-\alpha').
$$

At the Einstein radius:
$$
\alpha(\theta_E)=\theta_E \;\Rightarrow\; \beta(\theta_E)=0,\quad \det A(\theta_E)=0.
$$

---

## 8. Axisymmetric SPT Specialization

SPT ansatz (Eq. 11):
$$
\hat\beta=[1+f(\beta)]\,\beta.
$$

Evenness:
$$
f(-\beta)=f(\beta).
$$

Derivative implication (even $\Rightarrow$ $f'$ odd $\Rightarrow$ $f'(0)=0$):
$$
f(-x)=f(x)
\Rightarrow
\frac{d}{dx}f(-x)=\frac{d}{dx}f(x)
\Rightarrow
-f'(-x)=f'(x)
\Rightarrow
f'(-x)=-f'(x)
\Rightarrow
f'(0)=0.
$$

Transformed deflection (Eq. 12):
$$
\hat\alpha(\theta)=\alpha(\theta)-f(\beta)\,\beta,
\qquad
\beta=\theta-\alpha(\theta).
$$

Transformed enclosed mass:
$$
\hat m(\theta)=\theta\hat\alpha(\theta)=\theta\alpha(\theta)-\theta\,\beta\,f(\beta).
$$

---

## 9. Differentiating $\hat m$ (full derivation)

Start:
$$
\hat m(\theta)=\theta\alpha(\theta)-\theta\,\beta(\theta)\,f(\beta(\theta)),
\qquad
\beta(\theta)=\theta-\alpha(\theta).
$$

Differentiate the first term:
$$
\frac{d}{d\theta}[\theta\alpha]=\alpha+\theta\alpha'.
$$

For the second term, product + chain rule:
$$
\frac{d}{d\theta}[\theta\beta f(\beta)]
=
\beta f(\beta)+\theta\frac{d}{d\theta}[\beta f(\beta)].
$$

Compute:
$$
\frac{d}{d\theta}[\beta f(\beta)]
=
\beta' f(\beta)+\beta f'(\beta)\beta',
\qquad
\beta'=1-\alpha'.
$$

So:
$$
\frac{d}{d\theta}[\theta\beta f(\beta)]
=
\beta f+\theta(1-\alpha')f+\theta\beta(1-\alpha')f'.
$$

Thus:
$$
\hat m'
=
(\alpha+\theta\alpha')-\Big[\beta f+\theta(1-\alpha')f+\theta\beta(1-\alpha')f'\Big].
$$

Rewrite using $\beta=\theta-\alpha$:
$$
\beta+\theta(1-\alpha')=(\theta-\alpha)+(\theta-\theta\alpha')=2\theta-\alpha-\theta\alpha'.
$$

So:
$$
\hat m'=\theta\alpha'+\alpha-(2\theta-\alpha-\theta\alpha')f-\theta(\theta-\alpha)(1-\alpha')f'.
$$

Use:
$$
\alpha+\theta\alpha'=2\theta\kappa,
\qquad
2\theta-\alpha-\theta\alpha'=2\theta-2\theta\kappa=2\theta(1-\kappa),
\qquad
\theta(\theta-\alpha)(1-\alpha')=\theta^2\det A.
$$

Hence:
$$
\hat m'=2\theta\kappa-2\theta(1-\kappa)f-\theta^2(\det A)\,f'.
$$

Convert to convergence:
$$
\hat\kappa(\theta)=\frac{\hat m'(\theta)}{2\theta}
=
\kappa(\theta)-(1-\kappa(\theta))f(\beta)-\frac{\theta}{2}\det A(\theta)\,f'(\beta).
$$

This is Eq. (16).

---

## 10. Behavior at Special Radii (Einstein radius and others)

### At $\theta_E$
Since $\beta(\theta_E)=0$ and $\det A(\theta_E)=0$:
$$
\hat\kappa(\theta_E)=\kappa(\theta_E)[1+f(0)]-f(0).
$$

And:
$$
\hat\kappa'(\theta_E)=\kappa'(\theta_E)[1+f(0)].
$$

Higher derivatives involve $f''(0)$ etc., e.g. schematically:
$$
\hat\kappa''(\theta_E)=\kappa''(\theta_E)[1+f(0)]-\text{(coefficient)}\,[1-\kappa(\theta_E)]^3 f''(0).
$$

Radial critical curve condition:
$$
1-\alpha'(\theta_c)=0.
$$

(Then $\det A(\theta_c)=0$ as well, so value is MST-like, but slopes can involve $f'(\beta_c)$ because $\beta_c\neq 0$.)

---

## 11. Local Power-Law Constraint Near $\theta_E$ (Eq. 20)

Assume locally:
$$
\hat\kappa(\theta)\approx \hat\kappa(\theta_E)\left(\frac{\theta}{\theta_E}\right)^{-\nu}.
$$

Then:
$$
\hat\kappa'(\theta)= -\nu\frac{\hat\kappa(\theta)}{\theta}
\;\Rightarrow\;
\nu=-\frac{\theta_E\hat\kappa'(\theta_E)}{\hat\kappa(\theta_E)}.
$$

Second derivative:
$$
\hat\kappa''(\theta)=\nu(\nu+1)\frac{\hat\kappa(\theta)}{\theta^2}
\;\Rightarrow\;
\theta_E^2\hat\kappa''(\theta_E)=\nu(\nu+1)\hat\kappa(\theta_E).
$$

Eliminate $\nu$ using
$$
x\equiv \frac{\hat\kappa'(\theta_E)\theta_E}{\hat\kappa(\theta_E)}=-\nu,
\quad
\nu(\nu+1)=x(x-1),
$$
giving:
$$
\theta_E^2\hat\kappa''(\theta_E)
=
\left(\frac{\hat\kappa'(\theta_E)\theta_E}{\hat\kappa(\theta_E)}-1\right)\hat\kappa'(\theta_E)\theta_E.
$$

---

## 12. SIS Specialization (used in Section 3.3 example)

SIS convergence:
$$
\kappa(\theta)=\frac{\theta_E}{2\theta}.
$$

At $\theta_E$:
$$
\kappa(\theta_E)=\frac12.
$$

Derivative:
$$
\kappa'(\theta)=\frac{\theta_E}{2}\frac{d}{d\theta}\left(\theta^{-1}\right)
=-\frac{\theta_E}{2\theta^2}
\;\Rightarrow\;
\kappa'(\theta_E)=-\frac{1}{2\theta_E}.
$$

Using Einstein-radius relations:
$$
\hat\kappa(\theta_E)=\frac12(1+f_0)-f_0=\frac12(1-f_0),
\qquad
\hat\kappa'(\theta_E)=\left(-\frac{1}{2\theta_E}\right)(1+f_0),
\quad f_0\equiv f(0).
$$

Then local slope:
$$
\nu=-\frac{\theta_E\hat\kappa'(\theta_E)}{\hat\kappa(\theta_E)}
=
\frac{1+f_0}{1-f_0}.
$$

Equivalently:
$$
f_0=\frac{\nu-1}{\nu+1}.
$$

---

## 13. Interpreting Eq. (16): Local “Degrees of Freedom”

Eq. (16):
$$
\hat\kappa(\theta)
=
\kappa(\theta)-[1-\kappa(\theta)]f(\beta)-\frac{\theta}{2}\det A(\theta)\,f'(\beta),
\qquad
\beta(\theta)=\theta-\alpha(\theta).
$$

- At generic $\theta$ where $\det A\neq 0$, $\hat\kappa$ depends on **two local quantities**: $f(\beta)$ and $f'(\beta)$.
- On critical curves where $\det A=0$, the $f'(\beta)$ term drops out, leaving only an MST-like dependence on $f(\beta)$.
- At $\theta_E$, additionally $\beta=0$ and evenness forces $f'(0)=0$, so the transformation is especially MST-like at the ring.

---

## 14. ODE for Designing $f(\beta)$ Given a Target $\hat\kappa$ (outside caustic)

Rearrange Eq. (16):
$$
\kappa-\hat\kappa=(1-\kappa)f+\frac{\theta}{2}\det A\,f'.
$$

Multiply by $\frac{2}{\theta\det A}$ (in a region where $\theta\leftrightarrow\beta$ is one-to-one and $\det A\neq 0$):
$$
f'(\beta)+\underbrace{\frac{2(1-\kappa)}{\theta\det A}}_{g(\beta)}\,f(\beta)
=
\underbrace{\frac{2(\kappa-\hat\kappa)}{\theta\det A}}_{h(\beta)}.
$$

So:
$$
f'(\beta)+g(\beta)f(\beta)=h(\beta).
$$

---

## 15. Worked Example: SIS → Target $\hat\kappa(\theta)=(\theta_1/\theta)^2$

For SIS:
$$
\alpha=\theta_E,\qquad
\beta=\theta-\theta_E \Rightarrow \theta=\beta+\theta_E.
$$

Solve the linear ODE with integrating factor to obtain:
$$
f(\beta)=\frac{\theta_E}{\beta}
-\frac{2\theta_1^2\ln(\beta+\theta_E)}{\beta(\beta+\theta_E)}.
$$

To enforce evenness, a common modification described is to replace:
$$
\beta \mapsto \sqrt{\beta^2+\beta_0^2},
$$
so $f$ becomes a function of $\beta^2$ (even in $\beta$).

---

## 16. Key Takeaways

- MST is a special case of SPT with constant $f$.
- In axisymmetry, SPT can produce *exactly* invariant strong-lensing imaging (for point sources), while changing $\kappa(\theta)$.
- Eq. (16) shows explicitly how $f(\beta)$ and its derivative control $\hat\kappa(\theta)$.
- Near critical curves, the extra $f'$ freedom is suppressed by $\det A\to 0$, making degeneracies MST-like right where arcs are most constraining.
- For SIS, the mapping from $f(0)$ to local slope $\nu$ near $\theta_E$ becomes especially simple:
$$
\nu=\frac{1+f(0)}{1-f(0)}.
$$
