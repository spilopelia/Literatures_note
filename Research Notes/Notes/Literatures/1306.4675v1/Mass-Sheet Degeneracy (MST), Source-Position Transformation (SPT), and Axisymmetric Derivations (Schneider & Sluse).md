# Notes: Mass-Sheet Degeneracy (MST), Source-Position Transformation (SPT), and Schneider & Sluse (2013)

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

---

# Appendix: Non-axisymmetric (general) SPT material from the paper

## 17. Why the Jacobian of a *physical* lens is “identity minus a Hessian” (and symmetric)

Start from:
$$
\boldsymbol\beta(\boldsymbol\theta)=\boldsymbol\theta-\boldsymbol\alpha(\boldsymbol\theta),
\qquad
\boldsymbol\alpha(\boldsymbol\theta)=\nabla\psi(\boldsymbol\theta).
$$

Differentiate component-wise:
$$
A_{ij}(\boldsymbol\theta)
\equiv \frac{\partial \beta_i}{\partial \theta_j}
= \frac{\partial \theta_i}{\partial \theta_j}-\frac{\partial \alpha_i}{\partial \theta_j}
= \delta_{ij}-\frac{\partial}{\partial\theta_j}\left(\frac{\partial\psi}{\partial\theta_i}\right)
= \delta_{ij}-\frac{\partial^2\psi}{\partial\theta_i\partial\theta_j}.
$$

So:
$$
A(\boldsymbol\theta)=I-\nabla\nabla\psi(\boldsymbol\theta).
$$

If $\psi$ is smooth, mixed partials commute, so the Hessian is symmetric:
$$
\psi_{,ij}=\psi_{,ji}\quad\Rightarrow\quad A_{ij}=A_{ji}.
$$

This symmetry is the key obstruction in the general SPT: in general,
$$
\hat A(\theta)=B(\beta(\theta))\,A(\theta)
$$
need not be symmetric, so it may not correspond exactly to any potential $\hat\psi$ (equivalently, $\hat\alpha$ may have curl).

---

## 18. Convergence + shear form of $A$ (Eq. 27)

Define the usual second-derivative combinations:
$$
\kappa=\frac12(\psi_{,11}+\psi_{,22}),
\qquad
\gamma_1=\frac12(\psi_{,11}-\psi_{,22}),
\qquad
\gamma_2=\psi_{,12}.
$$

Then:
$$
A=
\begin{pmatrix}
1-\kappa-\gamma_1 & -\gamma_2\\
-\gamma_2 & 1-\kappa+\gamma_1
\end{pmatrix}.
$$

Write shear in amplitude–angle form:
$$
\gamma=\sqrt{\gamma_1^2+\gamma_2^2},
\qquad
\gamma_1=\gamma\cos2\vartheta,
\qquad
\gamma_2=\gamma\sin2\vartheta.
$$

Define the symmetric traceless “shear-direction” matrix:
$$
P(\vartheta)\equiv
\begin{pmatrix}
\cos2\vartheta & \sin2\vartheta\\
\sin2\vartheta & -\cos2\vartheta
\end{pmatrix}.
$$

Then (paper Eq. 27):
$$
A=(1-\kappa)\,I-\gamma\,P(\vartheta).
$$

---

## 19. Decomposition of $B$ and derivation of Eqs. (29)–(31)

They write $B$ analogously (paper Eq. 28):
$$
B = B_1 I + B_2 P(\eta),
\qquad
P(\eta)=
\begin{pmatrix}
\cos2\eta & \sin2\eta\\
\sin2\eta & -\cos2\eta
\end{pmatrix}.
$$

Using the chain rule:
$$
\hat A(\theta)=\frac{\partial\hat\beta}{\partial\theta}
=\frac{\partial\hat\beta}{\partial\beta}\frac{\partial\beta}{\partial\theta}
=B(\beta(\theta))\,A(\theta).
$$

Insert $A=(1-\kappa)I-\gamma P(\vartheta)$ and expand:
$$
\hat A
=(B_1 I + B_2 P(\eta))\Big((1-\kappa)I-\gamma P(\vartheta)\Big)
= B_1(1-\kappa)I + B_2(1-\kappa)P(\eta) -\gamma B_1 P(\vartheta) - \gamma B_2 P(\eta)P(\vartheta).
$$

Now compute $P(\eta)P(\vartheta)$. With $c_x=\cos2x$, $s_x=\sin2x$:
$$
P(\eta)=\begin{pmatrix}c_\eta&s_\eta\\ s_\eta&-c_\eta\end{pmatrix},
\qquad
P(\vartheta)=\begin{pmatrix}c_\vartheta&s_\vartheta\\ s_\vartheta&-c_\vartheta\end{pmatrix}.
$$

Multiply:
$$
P(\eta)P(\vartheta)=
\begin{pmatrix}
c_\eta c_\vartheta+s_\eta s_\vartheta & c_\eta s_\vartheta-s_\eta c_\vartheta\\
s_\eta c_\vartheta-c_\eta s_\vartheta & s_\eta s_\vartheta+c_\eta c_\vartheta
\end{pmatrix}
=
\begin{pmatrix}
\cos2(\eta-\vartheta) & -\sin2(\eta-\vartheta)\\
\sin2(\eta-\vartheta) & \cos2(\eta-\vartheta)
\end{pmatrix}.
$$

Therefore (paper Eq. 29):
$$
\hat A = B_1 (1-\kappa)I + B_2(1-\kappa)P(\eta) - \gamma B_1 P(\vartheta)
-\gamma B_2
\begin{pmatrix}
\cos2(\eta-\vartheta) & -\sin2(\eta-\vartheta)\\
\sin2(\eta-\vartheta) & \cos2(\eta-\vartheta)
\end{pmatrix}.
$$

### Trace definition of an “effective” $\hat\kappa$ (paper Eq. 30)

For any physical lens Jacobian, $\mathrm{tr}\,A=2(1-\kappa)$. They define $\hat\kappa$ from the trace as if $\hat A$ came from a potential:
$$
\mathrm{tr}\,\hat A \equiv 2(1-\hat\kappa).
$$

Take the trace of the expression above:
- $\mathrm{tr}(I)=2$
- $\mathrm{tr}(P(\eta))=\mathrm{tr}(P(\vartheta))=0$
- the last matrix has trace $2\cos2(\eta-\vartheta)$

So:
$$
\mathrm{tr}\,\hat A = 2B_1(1-\kappa) - 2\gamma B_2 \cos2(\eta-\vartheta),
$$
hence:
$$
\hat\kappa = 1 + B_1(\kappa-1) + B_2\gamma\cos2(\eta-\vartheta).
$$

### Asymmetry measure (paper Eq. 31)

The antisymmetric part is controlled by the off-diagonal difference:
$$
\frac{\hat A_{12}-\hat A_{21}}{2} = \gamma B_2 \sin2(\eta-\vartheta).
$$

They define:
$$
\hat\kappa_I \equiv B_2\gamma\sin2(\eta-\vartheta).
$$

Interpretation:
- $\hat\kappa$ is the “best” isotropic focusing part of $\hat A$
- $\hat\kappa_I$ measures how non-Hessian / non-physical the mapping is (a rotation/curl artifact)
- $\hat A$ is symmetric (physically realizable) if $\hat\kappa_I=0$, e.g. if $B_2=0$ (MST-like) or $\eta=\vartheta$ (aligned shear directions).

---

## 20. Radial “stretching” SPT in 2D and reduction to the axisymmetric formula (Eqs. 32–33)

Consider the commonly used “radial” SPT in the source plane:
$$
\hat{\boldsymbol\beta} = \bigl[1+f(\beta)\bigr]\boldsymbol\beta,
\qquad
\beta\equiv|\boldsymbol\beta|.
$$

Compute $B_{ij}=\partial\hat\beta_i/\partial\beta_j$. Since $\hat\beta_i=(1+f)\beta_i$:
$$
B_{ij}=\frac{\partial}{\partial\beta_j}\Big((1+f)\beta_i\Big)
=(1+f)\delta_{ij} + \beta_i\frac{\partial f}{\partial\beta_j}.
$$

Because $f=f(\beta)$ and $\partial\beta/\partial\beta_j=\beta_j/\beta$:
$$
\frac{\partial f}{\partial\beta_j}=f'(\beta)\frac{\beta_j}{\beta}.
$$

Therefore:
$$
B_{ij}=(1+f)\delta_{ij}+\frac{f'(\beta)}{\beta}\beta_i\beta_j.
$$

This matrix has eigenvalues:
- tangential direction: $1+f$
- radial direction: $1+f+\beta f'$

Writing this in the $(B_1,B_2,\eta)$ form yields (paper Eq. 32):
$$
B_1 = 1+f+\frac{\beta f'}{2},
\qquad
B_2 = \frac{\beta f'}{2},
\qquad
\eta=\phi,
$$
where $\phi$ is the polar angle of $\boldsymbol\beta$.

For an axisymmetric lens, the shear phase is the polar angle of $\boldsymbol\theta$:
$$
\vartheta=\varphi,
\qquad
\gamma=\kappa-\bar\kappa,
\qquad
\bar\kappa(\theta)=\frac{m(\theta)}{\theta^2}.
$$

Because $\boldsymbol\beta$ and $\boldsymbol\theta$ are collinear in axisymmetry, $\phi=\varphi$ (or $\varphi+\pi$), so:
$$
\sin2(\eta-\vartheta)=0 \quad\Rightarrow\quad \hat\kappa_I=0,
$$
and the mapping is physically realizable.

Plugging these into Eq. (30) gives (paper Eq. 33):
$$
\hat\kappa
= \kappa + (\kappa-1)f + \frac{\beta f'}{2}\,(2\kappa-1-\bar\kappa).
$$

Connection to Eq. (16): use $\beta=\theta-\alpha=\theta(1-\bar\kappa)$ and
$$
\alpha' = 2\kappa-\bar\kappa
\quad\Rightarrow\quad
\det A=(1-\bar\kappa)(1-2\kappa+\bar\kappa)
\quad\Rightarrow\quad
\theta\det A = (\theta-\alpha)(1+\bar\kappa-2\kappa).
$$
Then Eq. (33) matches Eq. (16).

---

## 21. Quadrupole lens estimate (Sect. 4.2): what controls the “non-physical” part

For a quadrupole lens (axisymmetric mass + external shear), the angle misalignment $\eta-\vartheta$ is generally nonzero, so $\hat\kappa_I$ can be nonzero.

For the radial SPT above, they obtain (paper Eq. 40):
$$
\hat\kappa
=
(1+f)\kappa - f
+\frac{\beta f'}{2}\Big(\kappa-1+\gamma\cos2(\phi-\vartheta)\Big).
$$

If $f$ is approximated near the origin by an even expansion:
$$
f(\beta)=f_0+\frac{f_2}{2}\beta^2,
$$
then $\beta f'/2=f_2\beta^2/2$, and the “nonlinear” (beyond-MST) part is controlled by $f_2$.

Their key qualitative result for asymmetry (paper Eq. 42) is that
$$
\hat\kappa_I \propto \gamma_p\,(\theta^2 f_2)\times(\text{angular terms}),
$$
so the non-physical part is suppressed if:
- the external shear $\gamma_p$ is small (typical $\lesssim 0.1$)
- the curvature $f_2$ is not too large (otherwise $\hat\kappa$ becomes unphysical even in axisymmetry).

This is the main reason they expect the “best physical approximation” from $\hat\kappa$ (trace) to be very close to the formal $\hat\alpha$ in realistic strong lenses.

---

## 22. Non-axisymmetric illustrative example (Sect. 4.3): how they *actually* construct the transform

They compare two *different* (non-axisymmetric) lens models, both with external shear:
- fiducial composite model (Hernquist + generalized NFW) + shear
- target cored power-law model + shear

### Step A: generate image configurations in the fiducial model
Pick a grid of sources $\{\beta\}$ in the source plane.
For each source $\beta$, solve the fiducial lens equation to get the image positions $\{\theta_i\}$.

### Step B: for each fiducial source, find the corresponding $\hat\beta$ in the target model
For the target model, adjust the source position $\hat\beta$ so that the target-predicted image positions $\{\hat\theta_i(\hat\beta)\}$ match the fiducial images $\{\theta_i\}$ as closely as possible.

Operationally this is an astrometric fit, e.g.
$$
\chi^2(\hat\beta)=\sum_i \frac{|\hat\theta_i(\hat\beta)-\theta_i|^2}{\sigma_\theta^2},
\qquad
\hat\beta = \arg\min_{\hat\beta}\chi^2(\hat\beta).
$$

This produces an *empirical* mapping:
$$
\beta \mapsto \hat\beta(\beta).
$$

### Step C: interpret the mapping as an approximate SPT and check if it is MST-like
For an MST you would have:
$$
\hat\beta=\lambda\beta \quad (\lambda=\text{constant}).
$$

They instead plot:
$$
\frac{|\hat\beta|}{|\beta|}
$$
as a function of $|\beta|$ and polar angle $\phi$ and find:
- it varies with $|\beta|$ (so **not MST**),
- it has only weak dependence on $\phi$ (so **almost isotropic**).

This motivates an approximate radial SPT interpretation:
$$
\hat\beta \approx [1+f(\beta)]\,\beta,
\qquad
1+f(\beta)\approx \frac{|\hat\beta|}{|\beta|}.
$$

### Step D: what they find for magnification and time delays (diagnostics)
Empirically, they find the magnification scaling behaves like:
$$
\hat\mu \approx [1+f(\beta)]^2\,\mu,
$$
i.e. “MST-like” but with a $\beta$-dependent scaling.

For time delays, MST would imply (up to conventions) a constant scaling with $\lambda$, but they find:
$$
\frac{\tau/\hat\tau}{|\beta|/|\hat\beta|}\neq 1,
$$
and, for quads, the ratio $\tau/\hat\tau$ can vary between different images of the same source (time-delay ratios not preserved), with spreads that can reach $\sim 10\%$ for some source positions.

**Interpretation:** in realistic non-axisymmetric lenses, two different mass models can be nearly indistinguishable in image positions/shapes over the strong-lensing region (an approximate SPT), but time delays provide a sensitive way to break the degeneracy.
