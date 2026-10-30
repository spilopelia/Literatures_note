---
tags: [AQM, quantum-mechanics, chapter-1, lecture-problems, midterm]
aliases: [AQM Chapter 1 Lecture Solutions]
---

# AQM Chapter 1 — Lecture Problems (Exam-length Solutions)

> [!info] Use
> These answers follow the numbering of Tian Lan's **lecture notes**. The uploaded 2024 solution handout numbers one density-operator theorem differently. Each answer gives a student's starting point, adequate working, and a final result. Companion: [[AQM Ch1 - Terminology and Formulas]] · [[AQM Ch1 - Homework 1]].

## Problem 1.2.1 — Vector-space identities

**Start:** Use the additive identity, additive inverse, and distributive axioms; do not assume the claims being proved.

**(1) Uniqueness of zero.** If $0_1,0_2$ are both zero vectors,

$$
0_1=0_1+0_2=0_2.
$$

**(2) $0\alpha=0$.**

$$
0\alpha=(0+0)\alpha=0\alpha+0\alpha\quad\Rightarrow\quad0\alpha=0,
$$

subtracting $0\alpha$ from both sides.

**(3) $c0=0$.**

$$
c0=c(0+0)=c0+c0\quad\Rightarrow\quad c0=0.
$$

**(4) Unique inverse and $-\alpha=(-1)\alpha$.** If $\alpha+\beta=\alpha+\gamma=0$,

$$
\beta=\beta+(\alpha+\gamma)=(\beta+\alpha)+\gamma=\gamma.
$$

Also $\alpha+(-1)\alpha=(1-1)\alpha=0\alpha=0$; uniqueness proves the formula.

## Problem 1.2.2 — Operators satisfy vector-space axioms

**Start:** Define $(A+B)v=Av+Bv$ and $(cA)v=cAv$. Check equality by applying both operators to arbitrary $v\in V$.

$$
\begin{aligned}
((A+B)+C)v&=(Av+Bv)+Cv=(A+(B+C))v,\\
(A+B)v&=Av+Bv=(B+A)v,\\
(A+0)v&=Av,\\
(A+(-A))v&=Av-Av=0,\\
(c_1(c_2A))v&=(c_1c_2)Av,\\
(1A)v&=Av,\\
c(A+B)v&=cAv+cBv=(cA+cB)v,\\
((c_1+c_2)A)v&=c_1Av+c_2Av.
\end{aligned}
$$

Thus $\operatorname{Hom}(V,W)$ is a vector space. Here $0$ means the zero operator in the relevant lines.

## Problem 1.2.3 — Operator inner product

**Start:** To prove $(A,B)=\operatorname{Tr}(A^\dagger B)$ is an inner product, verify linearity, conjugate symmetry, and positivity.

$$
\begin{aligned}
(A,cB+dC)&=\operatorname{Tr}(A^\dagger(cB+dC))=c(A,B)+d(A,C),\\
(A,B)^*&=\operatorname{Tr}[(A^\dagger B)^\dagger]=\operatorname{Tr}(B^\dagger A)=(B,A),\\
(A,A)&=\sum_i\langle i|A^\dagger A|i\rangle=\sum_i\|A|i\rangle\|^2\ge0.
\end{aligned}
$$

Equality in the last line means $A|i\rangle=0$ for every basis ket, hence $A=0$. This establishes the inner product in finite dimensions.

## Problem 1.2.4 — Six-part Pauli problem

### (1) Determine $Z$

**Start:** Work in the eigenbasis, possible because $Z=Z^\dagger$.

$$
Z=\operatorname{diag}(\lambda_1,\lambda_2),\qquad Z^2=I\Rightarrow\lambda_i=\pm1.
$$

$\operatorname{Tr}Z=0$ gives $\lambda_1+\lambda_2=0$. Order the basis so

$$
\boxed{Z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.}
$$

### (2) Determine $X$

**Start:** Use real entries, Hermiticity and zero trace first:

$$
X=\begin{pmatrix}a&b\\b&-a\end{pmatrix}.
$$

The anticommutator with $Z$ gives

$$
XZ+ZX=\begin{pmatrix}2a&0\\0&2a\end{pmatrix}=0\Rightarrow a=0.
$$

Then $X^2=I\Rightarrow b^2=1$. Choose the conventional basis phase $b=1$:

$$
\boxed{X=\begin{pmatrix}0&1\\1&0\end{pmatrix}.}
$$

The sign $-X$ is equally valid before choosing the phase convention.

### (3) Construct $Y=iXZ$

$$
Y=i\begin{pmatrix}0&-1\\1&0\end{pmatrix}=\boxed{\begin{pmatrix}0&-i\\i&0\end{pmatrix}}.
$$

$$
Y^\dagger=-iZX=iXZ=Y,\qquad Y^2=-XZXZ=X^2Z^2=I,\qquad\operatorname{Tr}Y=0.
$$

### (4) Orthogonal basis of operator space

Since all are Hermitian and traceless except $I$,

$$
\operatorname{Tr}(X)=\operatorname{Tr}(Y)=\operatorname{Tr}(Z)=0,
$$

and $XY=iZ$, $YZ=iX$, $ZX=iY$, cross inner products vanish. Also

$$
\operatorname{Tr}(I^2)=\operatorname{Tr}(X^2)=\operatorname{Tr}(Y^2)=\operatorname{Tr}(Z^2)=2.
$$

Thus $\operatorname{Tr}(\sigma_\mu^\dagger\sigma_\nu)=2\delta_{\mu\nu}$. Four nonzero orthogonal operators form a basis because $\dim\operatorname{Hom}(V,V)=2^2=4$. With $\frac12\operatorname{Tr}(A^\dagger B)$ they are orthonormal.

### (5) Pauli commutators

$$
[X,Y]=iZ-(-iZ)=2iZ,\quad [Y,Z]=2iX,\quad[Z,X]=2iY.
$$

Reversed pairs have opposite signs; identical pairs commute. Hence

$$
\boxed{[\sigma_i,\sigma_j]=2i\sum_k\epsilon_{ijk}\sigma_k.}
$$

### (6) General $2\times2$ Hermitian eigensystem

**Start:** Introduce spherical coordinates early, as suggested by the lecturer:

$$
x=r\sin\theta\cos\phi,\quad y=r\sin\theta\sin\phi,\quad z=r\cos\theta.
$$

Then

$$
H=aI+r\begin{pmatrix}\cos\theta&\sin\theta e^{-i\phi}\\\sin\theta e^{i\phi}&-\cos\theta\end{pmatrix}.
$$

**Eigenvalues:**

$$
\begin{aligned}
0&=\det(H-\lambda I)\\
&=(a-\lambda)^2-r^2\cos^2\theta-r^2\sin^2\theta\\
&=(a-\lambda)^2-r^2.
\end{aligned}
$$

Hence $\boxed{\lambda_\pm=a\pm r}$. For $\lambda_+$ and $r>0$ write the eigenvector $(u,v)^T$. The first row of $(H-\lambda_+I)(u,v)^T=0$ gives

$$
 (\cos\theta-1)u+\sin\theta e^{-i\phi}v=0 \Rightarrow v=e^{i\phi}\tan\frac\theta2\,u.
$$

Choose $u=\cos(\theta/2)$ and normalize:

$$
|+\rangle=\begin{pmatrix}\cos(\theta/2)\\e^{i\phi}\sin(\theta/2)\end{pmatrix}.
$$

The orthogonal normalized eigenvector is

$$
|-\rangle=\begin{pmatrix}-e^{-i\phi}\sin(\theta/2)\\\cos(\theta/2)\end{pmatrix}.
$$

For $r=0$, $H=aI$ and all vectors are eigenvectors. Interpretation: $a$ is the midpoint of the eigenvalues, $r$ is half the gap, and $\theta,\phi$ determine eigenvectors.

> [!tip] Under exam conditions
> Do not invoke $M^2=I$ without working if it is not immediately obvious. The characteristic determinant above is direct, standard, and matches the requested eigenvalue method.

## Problem 1.2.5 — Tensor-product bases and matrices

### (1) Basis independence

Let $|e'_a\rangle=\sum_i S_{ia}|e_i\rangle$ and $|f'_b\rangle=\sum_j T_{jb}|f_j\rangle$ with invertible $S,T$. Bilinearity yields

$$
|e'_a\rangle\otimes|f'_b\rangle=\sum_{ij}S_{ia}T_{jb}|e_i\rangle\otimes|f_j\rangle.
$$

This is the invertible product basis change $S\otimes T$, with inverse $S^{-1}\otimes T^{-1}$. Thus the construction is basis-independent up to a canonical isomorphism.

### (2) Tensor product of operator spaces

Using dual basis functionals (or ordinary bras for orthonormal bases), rank-one maps $|e'_a\rangle\langle e_i|$ and $|f'_b\rangle\langle f_j|$ form bases of the local operator spaces. Their product is

$$
 (|e'_a\rangle\langle e_i|)\otimes(|f'_b\rangle\langle f_j|)=|e'_af'_b\rangle\langle e_if_j|.
$$

These span all linear maps between product spaces, giving the finite-dimensional isomorphism

$$
\operatorname{Hom}(V\otimes W,V'\otimes W')\simeq\operatorname{Hom}(V,V')\otimes\operatorname{Hom}(W,W').
$$

### (3) Matrix elements

$$
\boxed{\langle e_i f_\alpha|A\otimes B|e_j f_\beta\rangle=\langle e_i|A|e_j\rangle\langle f_\alpha|B|f_\beta\rangle=A_{ij}B_{\alpha\beta}.}
$$

## Problem 1.3.1 — Measurements on $|\psi\rangle=a|0\rangle+b|1\rangle$

Assume $|a|^2+|b|^2=1$.

### (1) Outcomes and probabilities

Eigenstates: $|x\pm\rangle=(|0\rangle\pm|1\rangle)/\sqrt2$ and $|y\pm\rangle=(|0\rangle\pm i|1\rangle)/\sqrt2$. Born's rule gives

| Observable | $P(+1)$ | $P(-1)$ |
|---|---|---|
| $Z$ | $\vert a\vert ^2$ | $\vert b\vert ^2$ |
| $X$ | $\vert a+b\vert ^2/2$ | $\vert a-b\vert ^2/2$ |
| $Y$ | $\vert a-ib\vert ^2/2$ | $\vert a+ib\vert ^2/2$ |

For example $\langle y+|\psi\rangle=(a-ib)/\sqrt2$. Remember to conjugate $i$ when forming $\langle y+|$.

### (2) Expectations and polar coordinates

$$
\begin{aligned}
\langle Z\rangle&=|a|^2-|b|^2,\\
\langle X\rangle&=a^*b+b^*a,\\
\langle Y\rangle&=-ia^*b+ib^*a.
\end{aligned}
$$

Then

$$
r^2=(|a|^2-|b|^2)^2+4|a^*b|^2=(|a|^2+|b|^2)^2=1.
$$

From $\langle Z\rangle=\cos\theta$ and $\langle X\rangle+i\langle Y\rangle=\sin\theta e^{i\phi}$, choose global phase so $a\ge0$:

$$
\boxed{|\psi\rangle=\cos\frac\theta2|0\rangle+e^{i\phi}\sin\frac\theta2|1\rangle.}
$$

### (3) Repeated $Z$ measurement

After $Z=+1$, the normalized state is $|0\rangle$. A second ideal $Z$ measurement gives $P(+1)=1$ and $P(-1)=0$.

### (4) $Y=-1$ followed by $X$

Post-first-measurement: $|y-\rangle=(|0\rangle-i|1\rangle)/\sqrt2$.

$$
\langle x+|y-\rangle=\frac{1-i}{2},\qquad\langle x-|y-\rangle=\frac{1+i}{2}.
$$

Thus $\boxed{P(X=\pm1)=1/2}$.

## Problem 1.4.1 — Equality in uncertainty relation

Set $|u\rangle=(A-\langle A\rangle)|\psi\rangle$, $|v\rangle=(B-\langle B\rangle)|\psi\rangle$. The proof uses

$$
\|u\|^2\|v\|^2\ge|\langle u|v\rangle|^2\ge[\operatorname{Im}\langle u|v\rangle]^2.
$$

Equality requires (i) $u,v$ linearly dependent, and (ii) the inner product purely imaginary. For nonzero deviations,

$$
\boxed{(A-\langle A\rangle)|\psi\rangle=i\xi(B-\langle B\rangle)|\psi\rangle,\quad\xi\in\mathbb R.}
$$

If either deviation vector is zero, equality also holds. Equivalently, with the sign convention $\eta=-\xi$, $(A+i\eta B)|\psi\rangle=\langle A+i\eta B\rangle|\psi\rangle$.

## Problem 1.4.2 — Commutator identities

Use $[A,B]=AB-BA$:

$$
[A,B]=AB-BA=-[B,A].
$$

$$
[A,B+C]=AB+AC-BA-CA=[A,B]+[A,C].
$$

$$
[A,BC]=ABC-BCA=(AB-BA)C+B(AC-CA).
$$

For Jacobi, expand all three:

$$
\begin{aligned}
[A,[B,C]]&=ABC-ACB-BCA+CBA,\\
[B,[C,A]]&=BCA-BAC-CAB+ACB,\\
[C,[A,B]]&=CAB-CBA-ABC+BAC.
\end{aligned}
$$

Every term cancels with its opposite, so the sum is zero.

## Problem 1.6.1 — Density formulas recover pure-state formulas

With normalized $\rho=|\psi\rangle\langle\psi|$,

$$
\operatorname{Tr}(\rho P_\lambda)=\langle\psi|P_\lambda|\psi\rangle,
$$

$$
\rho_\lambda=\frac{P_\lambda|\psi\rangle\langle\psi|P_\lambda}{\langle\psi|P_\lambda|\psi\rangle}=|\psi_\lambda\rangle\langle\psi_\lambda|,
$$

where $|\psi_\lambda\rangle=P_\lambda|\psi\rangle/\sqrt{\langle\psi|P_\lambda|\psi\rangle}$ for nonzero-probability outcomes. Also $\operatorname{Tr}(\rho O)=\langle\psi|O|\psi\rangle$. Thus all three formulas coincide with §1.3.

## Problem 1.6.2 — Pure reduced state iff factorization

**($\Leftarrow$)** If $\rho=|\phi\rangle\langle\phi|\otimes\rho_2$,

$$
\operatorname{Tr}_2\rho=|\phi\rangle\langle\phi|\operatorname{Tr}\rho_2=|\phi\rangle\langle\phi|.
$$

**($\Rightarrow$)** Suppose $\rho_1=\operatorname{Tr}_2\rho=|\phi\rangle\langle\phi|$. Choose $|e_j\rangle\perp|\phi\rangle$. Then

$$
0=\langle e_j|\rho_1|e_j\rangle=\sum_b\langle e_jb|\rho|e_jb\rangle.
$$

Every summand is nonnegative since $\rho\ge0$, so each vanishes. Positive semidefiniteness implies $\rho|e_jb\rangle=0$ (because $\langle v|\rho|v\rangle=\|\sqrt\rho|v\rangle\|^2$). Thus $\rho$ has support only on $\operatorname{span}\{|\phi\rangle\}\otimes\mathcal H_2$ and is $|\phi\rangle\langle\phi|\otimes S$. Taking $\operatorname{Tr}_1$ gives $S=\rho_2$. Therefore $\boxed{\rho=|\phi\rangle\langle\phi|\otimes\rho_2}$.

## Problem 1.7.1 — Step function and delta

For $x\ne0$, $\theta(x)=\int_{-\infty}^x\delta(y)\,dy$; hence $d\theta/dx=\delta(x)$ in the distributional sense. Integrate by parts:

$$
\int_a^bf(x)\delta(x)\,dx=[f(x)\theta(x)]_a^b-\int_a^b\theta(x)f'(x)\,dx.
$$

- $a<b<0$: both terms zero, result $0$.
- $a<0<b$: result $f(b)-\int_0^bf'(x)\,dx=f(0)$.
- $0<a<b$: result $f(b)-f(a)-\int_a^bf'(x)\,dx=0$.

## Problem 1.7.2 — Equivalent definitions of $f(A)$

If $A|\alpha_i\rangle=\lambda_i|\alpha_i\rangle$, then $A^n|\alpha_i\rangle=\lambda_i^n|\alpha_i\rangle$. Thus

$$
\begin{aligned}
f(A)|\alpha_i\rangle
&=\sum_{n=0}^\infty\frac{f^{(n)}(0)}{n!}A^n|\alpha_i\rangle\\
&=\sum_{n=0}^\infty\frac{f^{(n)}(0)}{n!}\lambda_i^n|\alpha_i\rangle\\
&=f(\lambda_i)|\alpha_i\rangle.
\end{aligned}
$$

As eigenvectors span the space, $\boxed{f(A)=\sum_i f(\lambda_i)|\alpha_i\rangle\langle\alpha_i|}$ whenever both definitions apply.

## Problem 1.7.3 — Fourier relation implies canonical momentum properties

Given $\langle x|p\rangle=(2\pi\hbar)^{-1/2}e^{ipx/\hbar}$,

$$
\begin{aligned}
\langle x|\hat p|\psi\rangle
&=\int dp\,p\langle x|p\rangle\langle p|\psi\rangle\\
&=-i\hbar\frac{d}{dx}\int dp\,\langle x|p\rangle\langle p|\psi\rangle\\
&=-i\hbar\psi'(x).
\end{aligned}
$$

Next,

$$
\begin{aligned}
\langle x|[\hat x,\hat p]|\psi\rangle
&=-i\hbar x\psi'(x)+i\hbar\frac{d}{dx}[x\psi(x)]\\
&=-i\hbar x\psi'(x)+i\hbar[\psi(x)+x\psi'(x)]\\
&=i\hbar\psi(x).
\end{aligned}
$$

Therefore $\boxed{[\hat x,\hat p]=i\hbar I}$. Finally, $|\phi_0\rangle=\int dx\,|x\rangle$ has wavefunction $\langle x|\phi_0\rangle=\int dy\,\delta(x-y)=1$, so

$$
\langle x|\hat p|\phi_0\rangle=-i\hbar\frac{d}{dx}(1)=0\quad\Rightarrow\quad\boxed{\int dx\,\hat p|x\rangle=0}.
$$

> [!tip] Last-minute practice
> Reproduce Problems **1.2.4(6)**, **1.3.1**, **1.4.1**, **1.6.2**, and **1.7.3** without looking. They test different techniques rather than repeating one routine proof.
