# Source-Position Transformation (SPT) — Equation & Derivation Cheatsheet

**Paper:** Schneider & Sluse (2014), _Source-position transformation: an approximate invariance in strong gravitational lensing_

## 0. The one idea to remember

If you forget everything else, remember this chain:

$$  
\boxed{  
\text{image position }\theta  
\rightarrow  
\text{source position }\beta  
\rightarrow  
\text{transformed source }\hat\beta  
}  
$$

The ordinary lens equation is

$$  
\boxed{  
\beta=\theta-\alpha  
}  
$$

and the SPT asks:

> If I change the source coordinate from $\beta$ to $\hat\beta$, can I change the mass distribution so that the **same observed image positions** $\theta$ are produced?

Define

$$  
\boxed{  
\hat\alpha=\theta-\hat\beta.  
}  
$$

Then the transformed lens automatically maps the same $\theta$ to the transformed source $\hat\beta$.

Everything in the paper is about:

1. whether this mapping is one-to-one;
    
2. what new $\hat\kappa$ it implies;
    
3. whether $\hat\alpha$ is physically realizable by gravity;
    
4. what this means for lens modeling.
    

---

# 1. Minimal notation

|Symbol|Meaning|
|---|---|
|$\boldsymbol\theta$|observed image-plane position|
|$\boldsymbol\beta$|true/unlensed source-plane position|
|$\boldsymbol\alpha$|deflection angle|
|$\psi$|lensing potential|
|$\kappa$|dimensionless projected mass density|
|$\mathbf A$|lens Jacobian $\partial\beta/\partial\theta$|
|$\mathbf B$|source-transformation Jacobian $\partial\hat\beta/\partial\beta$|
|$\mu$|magnification|
|$\theta_E$|Einstein radius|

The three equations to memorize first are

$$  
\boxed{  
\beta=\theta-\alpha  
}  
$$

$$  
\boxed{  
\alpha=\nabla\psi  
}  
$$

$$  
\boxed{  
\nabla^2\psi=2\kappa.  
}  
$$

Since $\alpha=\nabla\psi$,

# $$  
\nabla\cdot\alpha=

 \nabla\cdot\nabla\psi=

\nabla^2\psi.  
$$

Therefore

$$  
\boxed{  
2\kappa=\nabla\cdot\alpha.  
}  
$$

This is the connection that is easy to forget.

---

# 2. The derivative dictionary

You do not need to memorize every special-coordinate formula if you remember what the operations mean.

## Gradient

A gradient turns a scalar into a vector:

$$  
\boxed{  
\psi  
\xrightarrow{\nabla}  
\boldsymbol\alpha.  
}  
$$

In Cartesian coordinates,

# $$  
\nabla\psi=

\begin{pmatrix}  
\partial\psi/\partial x\  
\partial\psi/\partial y  
\end{pmatrix}.  
$$

Interpretation:

> Which direction does $\psi$ increase most rapidly?

---

## Divergence

Divergence turns a vector field into a scalar:

$$  
\boxed{  
\boldsymbol\alpha  
\xrightarrow{\nabla\cdot}  
2\kappa.  
}  
$$

In Cartesian coordinates,

# $$  
\nabla\cdot\boldsymbol\alpha=

\frac{\partial\alpha_x}{\partial x}  
+  
\frac{\partial\alpha_y}{\partial y}.  
$$

Interpretation:

> Is the vector field locally spreading out or converging?

---

## Hessian / Jacobian

Differentiate a vector with respect to a vector:

$$  
\frac{\partial\alpha_i}{\partial\theta_j}.  
$$

This gives a matrix.

The lens Jacobian is

# $$  
\boxed{  
\mathbf A=

\frac{\partial\boldsymbol\beta}  
{\partial\boldsymbol\theta}.  
}  
$$

Because

$$  
\beta=\theta-\alpha,  
$$

we get

# $$  
\boxed{  
\mathbf A=

\mathbf I-  
\frac{\partial\boldsymbol\alpha}  
{\partial\boldsymbol\theta}.  
}  
$$

And because

$$  
\alpha=\nabla\psi,  
$$

# $$  
\frac{\partial\alpha_i}{\partial\theta_j}=

\frac{\partial^2\psi}  
{\partial\theta_i\partial\theta_j}.  
$$

So this is the Hessian of $\psi$.

---

# 3. Why is a physical lens Jacobian symmetric?

Because

$$  
\alpha=\nabla\psi.  
$$

Therefore

# $$  
\frac{\partial\alpha_x}{\partial y}=

\frac{\partial^2\psi}{\partial y,\partial x},  
$$

while

# $$  
\frac{\partial\alpha_y}{\partial x}=

\frac{\partial^2\psi}{\partial x,\partial y}.  
$$

For a smooth potential,

# $$  
\frac{\partial^2\psi}{\partial y,\partial x}=

\frac{\partial^2\psi}{\partial x,\partial y}.  
$$

Hence

# $$  
\boxed{  
\frac{\partial\alpha_x}{\partial y}=

\frac{\partial\alpha_y}{\partial x}.  
}  
$$

Therefore

$$  
\boxed{  
\mathbf A=\mathbf A^T.  
}  
$$

Equivalent statement:

$$  
\boxed{  
\nabla\times\alpha=0.  
}  
$$

### Memory shortcut

**Gravity comes from a scalar potential.**

Therefore:

$$  
\boxed{  
\text{physical lens}  
\Rightarrow  
\alpha=\nabla\psi  
\Rightarrow  
\text{zero curl}  
\Rightarrow  
\text{symmetric Jacobian}.  
}  
$$

---

# 4. Axisymmetric lens: reduce 2D to one radial function

For a circular lens,

# $$  
\boldsymbol\alpha=

\alpha(\theta)\mathbf e_r.  
$$

Here

$$  
\theta=|\boldsymbol\theta|.  
$$

Because the deflection points radially,

# $$  
\boldsymbol\beta=

\boldsymbol\theta-\boldsymbol\alpha  
$$

also points radially.

So the vector lens equation becomes the scalar radial equation

$$  
\boxed{  
\beta=\theta-\alpha(\theta).  
}  
$$

This is why the axisymmetric part of the paper is much easier.

---

# 5. Divergence of a radial field

You may forget the polar-coordinate formula. That is fine.

The formula is

# $$  
\boxed{  
\nabla\cdot[F(r)\mathbf e_r]=

\frac{1}{r}\frac{d}{dr}[rF(r)].  
}  
$$

For lensing,

$$  
F(r)\rightarrow\alpha(\theta),  
$$

so

# $$  
\nabla\cdot\alpha=

\frac1\theta  
\frac{d}{d\theta}  
[\theta\alpha].  
$$

Use the product rule:

# $$  
\frac{d}{d\theta}(\theta\alpha)=

\alpha+\theta\alpha'.  
$$

Therefore

# $$  
\nabla\cdot\alpha=

\frac{\alpha+\theta\alpha'}{\theta}.  
$$

Hence

# $$  
\boxed{  
\nabla\cdot\alpha=

\alpha'  
+  
\frac{\alpha}{\theta}.  
}  
$$

Since

$$  
2\kappa=\nabla\cdot\alpha,  
$$

we obtain

# $$  
\boxed{  
\kappa=

\frac12  
\left(  
\alpha'  
+  
\frac{\alpha}{\theta}  
\right).  
}  
$$

---

# 6. Do not memorize the radial-divergence formula blindly

There is a physical way to remember why there are **two terms**:

$$  
\boxed{  
\alpha'  
+  
\frac{\alpha}{\theta}.  
}  
$$

A radial vector field can change in two ways:

1. its **magnitude changes with radius**:
    

$$  
\alpha';  
$$

2. its **direction changes as you move around a circle**:
    

$$  
\frac{\alpha}{\theta}.  
$$

Those are the radial and tangential derivatives.

That same pair appears again in the lens eigenvalues.

This is not a coincidence.

---

# 7. Lens Jacobian eigenvalues

For an axisymmetric lens, the natural directions are:

$$  
\mathbf e_r  
\qquad\text{and}\qquad  
\mathbf e_t.  
$$

These are the Jacobian eigenvectors.

The corresponding eigenvalues are

$$  
\boxed{  
\lambda_r=1-\alpha'  
}  
$$

and

$$  
\boxed{  
\lambda_t=1-\frac{\alpha}{\theta}.  
}  
$$

## Why is the radial eigenvalue $1-\alpha'$?

Start from

$$  
\beta=\theta-\alpha(\theta).  
$$

Differentiate:

# $$  
\frac{d\beta}{d\theta}=

1-\alpha'.  
$$

So a tiny radial displacement obeys

# $$  
d\beta_r=

(1-\alpha')d\theta_r.  
$$

Therefore

# $$  
\boxed{  
\lambda_r=

 \frac{d\beta_r}{d\theta_r}=

1-\alpha'.  
}  
$$

---

# 8. Why is the tangential eigenvalue $1-\alpha/\theta$?

Do not differentiate $\beta$ here.

Instead, consider a small angle $d\phi$.

At image-plane radius $\theta$,

$$  
d\ell_\theta=\theta,d\phi.  
$$

At source-plane radius $\beta$,

$$  
d\ell_\beta=\beta,d\phi.  
$$

Therefore

# $$  
\lambda_t=

 \frac{d\ell_\beta}{d\ell_\theta}=

\frac{\beta}{\theta}.  
$$

But

$$  
\beta=\theta-\alpha.  
$$

So

# $$  
\boxed{  
\lambda_t=

 \frac{\theta-\alpha}{\theta}=

1-\frac{\alpha}{\theta}.  
}  
$$

### Memory shortcut

Radial:

# $$  
\boxed{  
\lambda_r=

\frac{d\beta}{d\theta}.  
}  
$$

Tangential:

# $$  
\boxed{  
\lambda_t=

\frac{\beta}{\theta}.  
}  
$$

Then insert

$$  
\beta=\theta-\alpha.  
$$

---

# 9. Eigenvalue versus eigenvector

Do not mix these up.

The **eigenvectors** are directions:

$$  
\boxed{  
\mathbf e_r,\quad\mathbf e_t.  
}  
$$

The **eigenvalues** tell you the local scaling along those directions:

$$  
\boxed{  
\lambda_r=1-\alpha',  
}  
$$

$$  
\boxed{  
\lambda_t=1-\frac{\alpha}{\theta}.  
}  
$$

Mathematically,

# $$  
\mathbf A\mathbf e_r=

\lambda_r\mathbf e_r,  
$$

# $$  
\mathbf A\mathbf e_t=

\lambda_t\mathbf e_t.  
$$

---

# 10. Determinant of the Jacobian

For a matrix, the determinant equals the product of eigenvalues:

$$  
\boxed{  
\det A=\lambda_r\lambda_t.  
}  
$$

Therefore

# $$  
\det A
=
(1-\alpha')  
\left(  
1-\frac{\alpha}{\theta}  
\right).  
$$

But

# $$  
1-\frac{\alpha}{\theta}=

\frac{\beta}{\theta}.  
$$

Hence

# $$  
\boxed{  
\det A=

(1-\alpha')  
\frac{\beta}{\theta}.  
}  
$$

Multiply by $\theta$:

# $$  
\boxed{  
\theta\det A=

\beta(1-\alpha').  
}  
$$

This identity is needed later in the SPT $\hat\kappa$ derivation.

---

# 11. Magnification and critical curves

Magnification is

$$  
\boxed{  
\mu=\frac1{\det A}.  
}  
$$

Therefore if

$$  
\det A=0,  
$$

the formal magnification diverges.

Since

$$  
\det A=\lambda_r\lambda_t,  
$$

a critical curve occurs when either eigenvalue vanishes.

## Tangential critical curve

$$  
\lambda_t=0.  
$$

Therefore

$$  
1-\frac{\alpha}{\theta}=0,  
$$

so

$$  
\boxed{  
\alpha(\theta_E)=\theta_E.  
}  
$$

Then

$$  
\beta=0.  
$$

This is the Einstein ring condition.

---

## Radial critical curve

$$  
\lambda_r=0,  
$$

so

$$  
\boxed{  
\alpha'=1.  
}  
$$

---

# 12. The SPT itself

Choose an axisymmetric source transformation

$$  
\boxed{  
\hat\beta=[1+f(\beta)]\beta.  
}  
$$

Interpretation:

- $f=0$: nothing changes;
    
- constant $f$: ordinary mass-sheet transformation;
    
- changing $f(\beta)$: genuine SPT.
    

---

# 13. Why require $f(-\beta)=f(\beta)$?

We want opposite sides of the circular source plane to transform symmetrically.

If

$$  
f(-\beta)=f(\beta),  
$$

then

# $$  
\hat\beta(-\beta)

# -[1+f(\beta)]\beta

-\hat\beta(\beta).  
$$

Thus

$$  
\boxed{  
f\text{ even}  
\Rightarrow  
\text{axisymmetry preserved}.  
}  
$$

---

# 14. Why require $1+f+\beta f'>0$?

Differentiate

$$  
\hat\beta=[1+f(\beta)]\beta.  
$$

Product rule:

# $$  
\boxed{  
\frac{d\hat\beta}{d\beta}

1+f+\beta f'.  
}  
$$

If this becomes zero,

$$  
\frac{d\hat\beta}{d\beta}=0,  
$$

the map locally collapses a range of source positions.

If it becomes negative, radial ordering reverses.

Then two distinct $\beta$ values could map to the same $\hat\beta$.

That is source-plane folding.

So require

$$  
\boxed{  
1+f+\beta f'>0.  
}  
$$

For the full 2D radial mapping, the tangential scaling is also

$$  
1+f.  
$$

Thus the complete local orientation-preserving condition is

$$  
\boxed{  
1+f>0  
}  
$$

and

$$  
\boxed{  
1+f+\beta f'>0.  
}  
$$

---

# 15. Construct the transformed deflection

Original:

$$  
\beta=\theta-\alpha.  
$$

Transformed lens:

$$  
\hat\beta=\theta-\hat\alpha.  
$$

Therefore

$$  
\hat\alpha=\theta-\hat\beta.  
$$

Insert

$$  
\hat\beta=(1+f)\beta:  
$$

# $$  
\hat\alpha

\theta-(1+f)\beta.  
$$

Since

$$  
\theta-\beta=\alpha,  
$$

we obtain

# $$  
\boxed{  
\hat\alpha

\alpha-f\beta.  
}  
$$

This is one of the central SPT equations.

---

# 16. Derive the transformed convergence $\hat\kappa$

Remember:

# $$  
\boxed{  
\hat\kappa

\frac12  
\left(  
\hat\alpha'  
+  
\frac{\hat\alpha}{\theta}  
\right).  
}  
$$

Start with

$$  
\hat\alpha=\alpha-f(\beta)\beta.  
$$

Differentiate:

# $$  
\hat\alpha'

## \alpha'

\frac{d}{d\theta}[f(\beta)\beta].  
$$

Chain rule:

# $$  
\frac{d}{d\theta}[f(\beta)\beta]

\frac{d[f\beta]}{d\beta}  
\frac{d\beta}{d\theta}.  
$$

First factor:

# $$  
\frac{d[f\beta]}{d\beta}

f+\beta f'.  
$$

Second factor:

# $$  
\frac{d\beta}{d\theta}

1-\alpha'.  
$$

Therefore

# $$  
\boxed{  
\hat\alpha'

\alpha'-(f+\beta f')(1-\alpha').  
}  
$$

Also,

# $$  
\frac{\hat\alpha}{\theta}

## \frac{\alpha}{\theta}

\frac{f\beta}{\theta}.  
$$

Put both into $\hat\kappa$:

# $$  
\hat\kappa

## \frac12  
\left[  
\alpha'  
+  
\frac{\alpha}{\theta}

## (f+\beta f')(1-\alpha')

\frac{f\beta}{\theta}  
\right].  
$$

Use

# $$  
\alpha'  
+  
\frac{\alpha}{\theta}

2\kappa.  
$$

So

# $$  
\hat\kappa

## \kappa

\frac12  
\left[  
f(1-\alpha')  
+  
\frac{f\beta}{\theta}  
+  
\beta f'(1-\alpha')  
\right].  
$$

Now combine the two $f$ terms.

Because

# $$  
\frac{\beta}{\theta}

1-\frac{\alpha}{\theta},  
$$

we have

# $$  
(1-\alpha')  
+  
\frac{\beta}{\theta}

2-  
\left(  
\alpha'  
+  
\frac{\alpha}{\theta}  
\right).  
$$

But

# $$  
\alpha'  
+  
\frac{\alpha}{\theta}

2\kappa.  
$$

Therefore

# $$  
(1-\alpha')  
+  
\frac{\beta}{\theta}

2(1-\kappa).  
$$

So

# $$  
\hat\kappa

## \kappa

## (1-\kappa)f

\frac12\beta f'(1-\alpha').  
$$

Finally use

# $$  
\theta\det A

\beta(1-\alpha').  
$$

Then

# $$  
\boxed{  
\hat\kappa

## \kappa

## (1-\kappa)f

\frac{\theta}{2}\det A,f'.  
}  
$$

This is the transformed convergence equation.

---

# 17. How to remember the transformed-$\kappa$ equation

Do not memorize the whole expression initially.

Remember its structure:

# $$  
\boxed{  
\hat\kappa

\kappa  
+  
\text{MST-like term}  
+  
\text{new SPT term}.  
}  
$$

Explicitly,

# $$  
\boxed{  
\hat\kappa

## \underbrace{\kappa}_{\rm original}

## \underbrace{(1-\kappa)f}_{\rm MST-like}

\underbrace{  
\frac{\theta}{2}\det A,f'  
}_{\rm genuine\ SPT}.  
}  
$$

If

$$  
f'=0,  
$$

the genuine SPT term disappears.

So constant $f$ gives the ordinary MST.

---

# 18. Recover the mass-sheet transformation

Take

$$  
f(\beta)=f_0.  
$$

Then

$$  
f'=0.  
$$

Thus

# $$  
\hat\kappa

\kappa-(1-\kappa)f_0.  
$$

Expand:

# $$  
\hat\kappa

(1+f_0)\kappa-f_0.  
$$

Define

$$  
\lambda=1+f_0.  
$$

Then

# $$  
\boxed{  
\hat\kappa

\lambda\kappa+(1-\lambda).  
}  
$$

That is exactly the MST.

### Memory statement

$$  
\boxed{  
\text{MST = constant source-plane scaling}  
}  
$$

while

$$  
\boxed{  
\text{SPT = position-dependent source-plane scaling}.  
}  
$$

---

# 19. General 2D SPT: introduce the two Jacobians

Original lens Jacobian:

# $$  
\boxed{  
A

\frac{\partial\beta}{\partial\theta}.  
}  
$$

SPT Jacobian:

# $$  
\boxed{  
B

\frac{\partial\hat\beta}{\partial\beta}.  
}  
$$

The full transformed mapping is

$$  
\theta  
\rightarrow\beta  
\rightarrow\hat\beta.  
$$

Chain rule therefore gives

# $$  
\boxed{  
\hat A

BA.  
}  
$$

This equation is central to understanding why the general SPT may not be physical.

---

# 20. Why can $BA$ become asymmetric?

Suppose both $A$ and $B$ are symmetric:

$$  
A=A^T,  
\qquad  
B=B^T.  
$$

Then

# $$  
(BA)^T

# A^TB^T

AB.  
$$

Therefore

$$  
BA  
$$

is symmetric only when

$$  
\boxed{  
BA=AB.  
}  
$$

So the condition is

$$  
\boxed{  
[A,B]=0.  
}  
$$

where

$$  
[A,B]=AB-BA  
$$

is the matrix commutator.

---

# 21. The antisymmetric piece

Any matrix can be decomposed into

# $$  
M

M_{\rm sym}  
+  
M_{\rm asym},  
$$

where

# $$  
M_{\rm sym}

\frac12(M+M^T)  
$$

and

# $$  
M_{\rm asym}

\frac12(M-M^T).  
$$

For

$$  
\hat A=BA,  
$$

we obtain

# $$  
\hat A_{\rm asym}

\frac12(BA-AB).  
$$

Therefore

# $$  
\boxed{  
\hat A_{\rm asym}

\frac12[B,A].  
}  
$$

So:

$$  
\boxed{  
[A,B]=0  
\Rightarrow  
\hat A_{\rm asym}=0.  
}  
$$

If they do not commute,

$$  
\boxed{  
[A,B]\neq0  
\Rightarrow  
\text{antisymmetric component}.  
}  
$$

---

# 22. Why does antisymmetric mean nonphysical?

A physical lens requires

$$  
\hat\alpha=\nabla\hat\psi.  
$$

Therefore

$$  
\nabla\times\hat\alpha=0.  
$$

Equivalently,

# $$  
\frac{\partial\hat\alpha_x}{\partial y}

\frac{\partial\hat\alpha_y}{\partial x}.  
$$

That is exactly the condition that the derivative matrix is symmetric.

So

$$  
\boxed{  
\hat A_{\rm asym}\neq0  
}  
$$

implies

$$  
\boxed{  
\nabla\times\hat\alpha\neq0.  
}  
$$

Hence no scalar gravitational potential $\hat\psi$ exists whose gradient equals the formal transformed deflection everywhere.

Therefore:

$$  
\boxed{  
\text{formal SPT may reproduce the image mapping exactly}  
}  
$$

but

$$  
\boxed{  
\text{it may not correspond to an exact physical mass distribution}.  
}  
$$

---

# 23. Why does the MST always remain physical?

For the MST,

$$  
\hat\beta=\lambda\beta.  
$$

Therefore

$$  
B=\lambda I.  
$$

The identity matrix commutes with every matrix:

$$  
IA=AI.  
$$

Hence

$$  
BA=AB.  
$$

Therefore

$$  
\boxed{  
\text{MST is exactly physical for any lens}.  
}  
$$

---

# 24. Why does a radial SPT work for an axisymmetric lens?

For an axisymmetric lens, $A$ has eigenvectors

$$  
\mathbf e_r,\mathbf e_t.  
$$

The radial source transformation also has eigenvectors

$$  
\mathbf e_r,\mathbf e_t.  
$$

So in that basis,

$$  
A=  
\begin{pmatrix}  
\lambda_r&0\  
0&\lambda_t  
\end{pmatrix}  
$$

and

$$  
B=  
\begin{pmatrix}  
b_r&0\  
0&b_t  
\end{pmatrix}.  
$$

Diagonal matrices commute:

$$  
AB=BA.  
$$

Therefore

$$  
\boxed{  
\text{axisymmetric lens + radial SPT}  
\Rightarrow  
\text{exact physical transformed lens}.  
}  
$$

---

# 25. Why does the general elliptical case fail?

For an elliptical/sheared lens, the eigen-directions of $A$ vary around the image plane.

The same source $\beta$ can produce several images:

$$  
\theta_1,\theta_2,\theta_3,\ldots  
$$

All those images share the same source transformation matrix

$$  
B(\beta).  
$$

But they have different lens Jacobians:

$$  
A(\theta_1),  
\quad  
A(\theta_2),  
\quad  
A(\theta_3).  
$$

Their principal directions generally differ.

So a single anisotropic $B$ cannot usually commute with all of them:

$$  
BA_i\neq A_iB.  
$$

Therefore a nonlinear SPT generally develops a small antisymmetric/curl component.

The only matrix guaranteed to commute with every $A_i$ is essentially

$$  
\boxed{  
B=\lambda I.  
}  
$$

That brings us back to the MST.

---

# 26. Exact versus approximate SPT

The formal transformed deflection

$$  
\hat\alpha  
$$

exactly reproduces the transformed source-image mapping.

But it may have

$$  
\nabla\times\hat\alpha\neq0.  
$$

If that curl is tiny, we may find a nearby physical field

$$  
\tilde\alpha=\nabla\tilde\psi  
$$

such that

$$  
\boxed{  
\tilde\alpha\approx\hat\alpha.  
}  
$$

Then image changes may be below observational uncertainties.

Hence:

$$  
\boxed{  
\text{general SPT = approximate observational invariance}.  
}  
$$

---

# 27. The complete logical chain of the paper

Memorize this rather than individual equations:

$$  
\boxed{  
\beta=\theta-\alpha  
}  
$$

↓

Change the source coordinate:

$$  
\boxed{  
\beta\rightarrow\hat\beta(\beta)  
}  
$$

↓

Define a transformed deflection:

# $$  
\boxed{  
\hat\alpha

\theta-\hat\beta.  
}  
$$

↓

The same image positions can map to transformed source positions.

↓

For circular lenses:

$$  
\boxed{  
\hat\alpha  
\rightarrow  
\text{exact physical }\hat\kappa.  
}  
$$

↓

For general lenses:

$$  
\boxed{  
\hat A=BA.  
}  
$$

↓

Usually

$$  
BA\neq AB.  
$$

↓

Therefore

$$  
\boxed{  
\hat A_{\rm asym}\neq0  
}  
$$

↓

Therefore

$$  
\boxed{  
\nabla\times\hat\alpha\neq0.  
}  
$$

↓

Formal transformed lens is not exactly physical.

↓

But if the antisymmetric component is small,

$$  
\boxed{  
\text{nearby physical lens can produce nearly identical observations}.  
}  
$$

That is the SPT degeneracy.

---

# 28. What does the paper imply for lens modeling?

The main implication is:

$$  
\boxed{  
\text{an excellent image fit does not guarantee a unique mass reconstruction}.  
}  
$$

The observed image constrains a combined mapping involving both

$$  
\kappa  
$$

and

$$  
S(\beta).  
$$

So one should think of the inference as

$$  
\boxed{  
(\kappa,S)\rightarrow d  
}  
$$

rather than merely

$$  
\kappa\rightarrow d.  
$$

---

# 29. Bayesian interpretation

The posterior is

$$  
p(\kappa,S|d)  
\propto  
p(d|\kappa,S)  
p(\kappa)  
p(S).  
$$

An SPT-like direction can give

$$  
p(d|\kappa,S)  
\approx  
p(d|\hat\kappa,\hat S).  
$$

So the likelihood may be nearly flat along

$$  
(\kappa,S)  
\rightarrow  
(\hat\kappa,\hat S).  
$$

Then the posterior can be selected substantially by

$$  
p(\kappa)  
$$

and

$$  
p(S).  
$$

This means:

> A narrow posterior is not necessarily the same thing as the imaging data uniquely identifying the mass.

The prior/model family may have removed part of the degeneracy.

---

# 30. Consequence for source regularization

Suppose two reconstructions satisfy

$$  
\chi^2_1\approx\chi^2_2,  
$$

but

$$  
R(S_1)\ll R(S_2).  
$$

A smoothness prior may strongly prefer solution 1.

That does **not** necessarily mean the image data prefer $\kappa_1$.

It may mean

$$  
\boxed{  
\text{the source prior prefers the source associated with }\kappa_1.  
}  
$$

Therefore, when doing flexible source reconstruction, check whether mass conclusions are robust against reasonable changes in source regularization.

---

# 31. Consequence for mass parameterization

Suppose your model only allows

$$  
\rho(r)\propto r^{-\gamma}.  
$$

You obtain

$$  
\gamma=2.03\pm0.02.  
$$

This only strictly means:

$$  
\boxed{  
\text{among the permitted power-law models, }\gamma\text{ is tightly constrained}.  
}  
$$

An SPT-related mass profile may not be a pure power law and therefore might never appear in your posterior.

So very restrictive mass parameterizations can hide the true degeneracy.

---

# 32. What remains robust?

The paper does **not** imply that nothing can be measured.

Strong lensing strongly constrains the mass near the Einstein radius.

At

$$  
\theta=\theta_E,  
$$

$$  
\beta=0  
$$

and

$$  
\alpha(\theta_E)=\theta_E.  
$$

For an axisymmetric lens,

# $$  
\alpha(\theta)

\frac{m(\theta)}{\theta}.  
$$

Thus

# $$  
m(\theta_E)

# \theta_E\alpha(\theta_E)

\theta_E^2.  
$$

So

$$  
\boxed{  
M(<\theta_E)  
}  
$$

is generally much more robust than the detailed radial profile.

A useful rule of thumb is:

$$  
\boxed{  
\text{enclosed Einstein-radius mass: robust}  
}  
$$

but

$$  
\boxed{  
\text{detailed profile slope/curvature: more degenerate}.  
}  
$$

---

# 33. What can help break the degeneracy?

Use information that does not transform in the same way.

Examples:

- stellar kinematics;
    
- multiple source redshifts;
    
- weak lensing;
    
- time delays;
    
- physically justified mass priors;
    
- independent information about the source.
    

For time delays,

$$  
\Delta t  
\propto  
\Delta\phi,  
$$

where

# $$  
\phi

\frac12|\theta-\beta|^2-\psi.  
$$

Image positions constrain stationary points:

$$  
\nabla_\theta\phi=0.  
$$

Time delays additionally depend on the **values** of $\phi$ at those stationary points.

So two models can preserve image positions but predict different time delays.

---

# 34. SPT does not mean “source can absorb any subhalo”

This distinction is important.

An SPT uses one coherent transformation

$$  
\boxed{  
\hat\beta=F(\beta).  
}  
$$

If one source feature produces several images, the same $F$ must work for all of them.

A local mass perturbation can affect multiple images in a pattern that no single global source transformation can reproduce.

Therefore:

$$  
\boxed{  
\text{SPT is one rigorous example of lens-source degeneracy}  
}  
$$

but not

$$  
\boxed{  
\text{proof that arbitrary mass structure can always be hidden in the source}.  
}  
$$

---

# 35. Five equations worth actually memorizing

If your memory is limited, memorize only these first.

### 1. Lens equation

$$  
\boxed{  
\beta=\theta-\alpha.  
}  
$$

### 2. Deflection from potential

$$  
\boxed{  
\alpha=\nabla\psi.  
}  
$$

### 3. Convergence from divergence

$$  
\boxed{  
2\kappa=\nabla\cdot\alpha.  
}  
$$

### 4. Lens Jacobian

$$  
\boxed{  
A=\frac{\partial\beta}{\partial\theta}.  
}  
$$

### 5. SPT Jacobian chain rule

$$  
\boxed{  
\hat A=BA.  
}  
$$

Everything else can be re-derived from these.

---

# 36. Five secondary equations to re-derive rather than memorize

For an axisymmetric lens:

# $$  
\boxed{  
\nabla\cdot\alpha

\alpha'  
+  
\frac{\alpha}{\theta}.  
}  
$$

# $$  
\boxed{  
\lambda_r

1-\alpha'.  
}  
$$

# $$  
\boxed{  
\lambda_t

# 1-\frac{\alpha}{\theta}

\frac{\beta}{\theta}.  
}  
$$

# $$  
\boxed{  
\det A

\lambda_r\lambda_t.  
}  
$$

# $$  
\boxed{  
\hat\kappa

\kappa-(1-\kappa)f  
-\frac{\theta}{2}\det A,f'.  
}  
$$

If you forget them, rebuild them using the five primary equations.

---

# 37. Derivation map when you get stuck

If you encounter

# $$  
\kappa

\frac12  
\left(  
\alpha'  
+  
\frac{\alpha}{\theta}  
\right),  
$$

ask:

> Where does this come from?

Answer:

$$  
\alpha=\nabla\psi  
$$

↓

$$  
\nabla\cdot\alpha=\nabla^2\psi  
$$

↓

$$  
\nabla^2\psi=2\kappa  
$$

↓

radial divergence:

# $$  
\nabla\cdot\alpha

\frac1\theta\frac{d}{d\theta}(\theta\alpha)  
$$

↓

# $$  
2\kappa

\alpha'  
+  
\frac{\alpha}{\theta}.  
$$

---

If you encounter

$$  
\lambda_t=1-\frac{\alpha}{\theta},  
$$

ask:

> Why?

Answer:

# $$  
\lambda_t

\frac{\text{source tangential length}}  
{\text{image tangential length}}  
$$

↓

# $$

\frac{\beta d\phi}{\theta d\phi}  
$$

↓

# $$

\frac{\beta}{\theta}  
$$

↓

# $$

\frac{\theta-\alpha}{\theta}.  
$$

---

If you encounter

$$  
\theta\det A=\beta(1-\alpha'),  
$$

ask:

> Where did that come from?

Answer:

$$  
\det A=\lambda_r\lambda_t  
$$

↓

# $$

(1-\alpha')\frac{\beta}{\theta}  
$$

↓

multiply by $\theta$.

---

If you encounter

$$  
\hat A=BA,  
$$

ask:

> Why?

Answer:

$$  
\theta\rightarrow\beta\rightarrow\hat\beta  
$$

and apply the chain rule:

# $$  
\frac{\partial\hat\beta}{\partial\theta}

\frac{\partial\hat\beta}{\partial\beta}  
\frac{\partial\beta}{\partial\theta}.  
$$

---

If you encounter the antisymmetric problem, ask:

> Why is $BA$ problematic?

Answer:

$$  
(BA)^T=AB.  
$$

Thus

$$  
BA\text{ symmetric}  
\iff  
BA=AB.  
$$

If not,

$$  
\text{curl}\neq0  
$$

and it cannot be an exact gravitational potential field.

---

# 38. Three calculus rules you need for essentially the whole paper

You do not need advanced calculus.

## Product rule

$$  
\boxed{  
(uv)'=u'v+uv'.  
}  
$$

Example:

# $$  
\frac{d}{d\theta}(\theta\alpha)

\alpha+\theta\alpha'.  
$$

---

## Chain rule

# $$  
\boxed{  
\frac{df(\beta)}{d\theta}

\frac{df}{d\beta}  
\frac{d\beta}{d\theta}.  
}  
$$

Example:

# $$  
\frac{d}{d\theta}[f(\beta)\beta]

(f+\beta f')  
(1-\alpha').  
$$

---

## Matrix chain rule

If

$$  
\theta\rightarrow\beta\rightarrow\hat\beta,  
$$

then

# $$  
\boxed{  
\frac{\partial\hat\beta}{\partial\theta}

\frac{\partial\hat\beta}{\partial\beta}  
\frac{\partial\beta}{\partial\theta}.  
}  
$$

Hence

$$  
\boxed{  
\hat A=BA.  
}  
$$

Those three rules generate most of the paper's algebra.

---

# 39. One-page conceptual summary

### Observation

We observe

$$  
\theta,  
$$

not

$$  
\beta.  
$$

### Freedom

Therefore we can consider

$$  
\beta\rightarrow\hat\beta.  
$$

### Compensation

Change

$$  
\alpha\rightarrow\hat\alpha  
$$

so that

$$  
\hat\beta=\theta-\hat\alpha.  
$$

### Result

Different

$$  
(\kappa,S)  
$$

pairs can reproduce essentially the same strong-lensing images.

### Axisymmetric case

Radial SPTs are exactly physical.

### General lens

The formal SPT can generate curl because

$$  
\hat A=BA  
$$

and generally

$$  
BA\neq AB.  
$$

### Therefore

General SPT is generally an **approximate**, rather than exact, physical invariance.

### Modeling implication

$$  
\boxed{  
\text{good image residuals}  
\not\Rightarrow  
\text{unique mass profile}.  
}  
$$

You must distinguish what is constrained by

$$  
p(d|\kappa,S)  
$$

from what is selected by

$$  
p(\kappa)  
$$

and

$$  
p(S).  
$$

---

# 40. The exam-style answer

If asked:

> **What is the source-position transformation and why is it important?**

A compact answer is:

The SPT generalizes the mass-sheet transformation by applying a one-to-one transformation $\hat{\boldsymbol\beta}(\boldsymbol\beta)$ to source-plane coordinates and defining a corresponding transformed deflection field

# $$  
\hat{\boldsymbol\alpha}(\boldsymbol\theta)

\boldsymbol\theta-  
\hat{\boldsymbol\beta}  
[  
\boldsymbol\theta-\boldsymbol\alpha(\boldsymbol\theta)  
].  
$$

This leaves the multiple-image mapping invariant. For axisymmetric lenses, radial SPTs correspond exactly to alternative physical surface-density distributions, including the MST as the constant-scaling special case. For general non-axisymmetric lenses, the transformed Jacobian is

$$  
\hat A=BA,  
$$

which is generally not symmetric because $A$ and $B$ need not commute; the resulting transformed deflection therefore contains curl and may not correspond exactly to a gravitational potential. If the antisymmetric component is sufficiently small, however, a nearby physical mass model can produce observationally indistinguishable images. The implication for lens modeling is that strong-lensing imaging alone may tightly constrain image mappings and enclosed mass around the Einstein radius while leaving substantial degeneracy in the detailed radial mass profile and reconstructed source.

---

# 41. Final memory hierarchy

When revising, learn this in layers.

## Layer 1 — absolutely remember

$$  
\boxed{  
\beta=\theta-\alpha  
}  
$$

$$  
\boxed{  
\alpha=\nabla\psi  
}  
$$

$$  
\boxed{  
2\kappa=\nabla\cdot\alpha  
}  
$$

$$  
\boxed{  
A=\partial\beta/\partial\theta  
}  
$$

$$  
\boxed{  
\hat A=BA  
}  
$$

---

## Layer 2 — know how to reconstruct

$$  
\lambda_r=1-\alpha',  
$$

$$  
\lambda_t=1-\frac{\alpha}{\theta},  
$$

$$  
\det A=\lambda_r\lambda_t.  
$$

---

## Layer 3 — understand conceptually

$$  
\boxed{  
\text{SPT = trade source mapping against mass mapping}.  
}  
$$

$$  
\boxed{  
\text{MST = constant special case}.  
}  
$$

$$  
\boxed{  
\text{general SPT + general lens}  
\rightarrow  
\text{possible curl}.  
}  
$$

$$  
\boxed{  
\text{image agreement alone does not guarantee unique }\kappa.  
}  
$$

If you can reconstruct Layers 2 and 3 from Layer 1, you do not need to rely heavily on memorizing isolated equations.