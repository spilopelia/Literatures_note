---
title: AQM Chapter 1 — Homework 2 Extension
tags: [AQM, chapter-1, homework-2, long-questions, cross-chapter]
---

# AQM Chapter 1 — Homework 2 Extension

> [!info] Scope
> Supplement to [[AQM Chapter 1 - Long Questions Revised Handwritten-Style]], using *Homework 2* (PHYS 5410, 2024), the supplied eight-page handwritten solution, and Tian Lan's lecture notes. All problems **1(a–b), 2(a–b), 3(a–c)** are included. HW2 does **not** correspond wholesale to Chapter 2: Q1 and Q2 primarily reinforce Chapter 1 §1.4, Q3(a) reinforces §1.7, while Q3(b–c) connects to Chapter 2 quantization and later symmetry/gauge material. Distinctions from the handwritten approach are explained where needed.

## Chapter map and reusable prerequisites

- **Q1:** $[A,B]=AB-BA$, commutator product rule and Jacobi identity; later reused by the Hadamard formula (lecture Problem 2.2.1).
- **Q2:** Pauli matrices, Bloch sphere, $\Delta A^2=\langle A^2\rangle-\langle A\rangle^2$, Robertson uncertainty. Most useful Chapter 1 long-question extension.
- **Q3:** $[x,p]=i\hbar$, unitary translation, momentum wavefunction, minimal coupling $p\mapsto p-qA/c$, and unitary gauge equivalence. This last component goes beyond the basic Chapter 1 presentation.

## Problem 1 (20 points) — Commutators as operators on operators

For an operator $A$, define $\operatorname{ad}_A(B):=[A,B]$. The input $B$ itself is an operator; $\operatorname{ad}_A$ is therefore a *superoperator*.

### (a) Prove the product (Leibniz) rule

Starting only with the definition, add and subtract the same term $BAC$:

$$
\begin{aligned}
\operatorname{ad}_A(BC)
&=[A,BC]=ABC-BCA\\
&=ABC-BAC+BAC-BCA\\
&=(AB-BA)C+B(AC-CA)\\
&=[A,B]C+B[A,C]\\
&=\boxed{(\operatorname{ad}_A B)C+B(\operatorname{ad}_A C)}.
\end{aligned}
$$

This acts like a derivative because it obeys a product rule, but it is *not* an ordinary scalar derivative.

### (b) Prove $[\operatorname{ad}_A,\operatorname{ad}_B]=\operatorname{ad}_{[A,B]}$

To prove equality of superoperators, apply both sides to an **arbitrary** $C$:

$$
\begin{aligned}
[\operatorname{ad}_A,\operatorname{ad}_B]C
&=\operatorname{ad}_A([B,C])-\operatorname{ad}_B([A,C])\\
&=[A,[B,C]]-[B,[A,C]].
\end{aligned}
$$

Recall Jacobi, $[A,[B,C]]+[B,[C,A]]+[C,[A,B]]=0$, together with $[C,A]=-[A,C]$. Hence

$$
\begin{aligned}
[A,[B,C]]-[B,[A,C]]
&=-[C,[A,B]]\\
&=[[A,B],C]\\
&=\operatorname{ad}_{[A,B]}C.
\end{aligned}
$$

Since $C$ was arbitrary, $\boxed{[\operatorname{ad}_A,\operatorname{ad}_B]=\operatorname{ad}_{[A,B]}}$. **Check the level:** the outer bracket on the left is a commutator of superoperators; the bracket on the right acts on an ordinary operator.

## Problem 2 (40 points) — Pauli expectations and uncertainty equality

**Given:**

$$
|\psi(\theta,\phi)\rangle=c|0\rangle+e^{i\phi}s|1\rangle,
\quad c=\cos\frac\theta2,\quad s=\sin\frac\theta2,
$$

and $X=|0\rangle\langle1|+|1\rangle\langle0|$, $Y=i|1\rangle\langle0|-i|0\rangle\langle1|$, $Z=|0\rangle\langle0|-|1\rangle\langle1|$. Their matrices in the ordered basis $(|0\rangle,|1\rangle)$ are

$$
X=\begin{pmatrix}0&1\\1&0\end{pmatrix},\quad
Y=\begin{pmatrix}0&-i\\i&0\end{pmatrix},\quad
Z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
$$

### (a) Evaluate $\langle X\rangle$, $\langle Y\rangle$, $\langle Z\rangle$

Take the Hermitian adjoint of the state **including the conjugate phase**:

$$
\langle\psi|=c\langle0|+e^{-i\phi}s\langle1|.
$$

For $X$, $X|\psi\rangle=e^{i\phi}s|0\rangle+c|1\rangle$. Therefore

$$
\begin{aligned}
\langle X\rangle&=(c\langle0|+e^{-i\phi}s\langle1|)
(e^{i\phi}s|0\rangle+c|1\rangle)\\
&=cs(e^{i\phi}+e^{-i\phi})=2cs\cos\phi
=\boxed{\sin\theta\cos\phi}.
\end{aligned}
$$

Similarly, $Y|\psi\rangle=-ie^{i\phi}s|0\rangle+ic|1\rangle$ gives

$$
\langle Y\rangle=cs(-ie^{i\phi}+ie^{-i\phi})
=2cs\sin\phi=\boxed{\sin\theta\sin\phi}.
$$

Finally, $Z|\psi\rangle=c|0\rangle-e^{i\phi}s|1\rangle$:

$$
\langle Z\rangle=c^2-s^2=\boxed{\cos\theta}.
$$

Thus $\langle X\rangle^2+\langle Y\rangle^2+\langle Z\rangle^2=1$ for this pure state.

### (b) Saturating the $Z$–$X$ uncertainty inequality

**Start with the exact inequality in the question**:

$$
(\Delta Z)^2(\Delta X)^2\geq\frac14|\langle[Z,X]\rangle|^2.
$$

Use $X^2=Y^2=Z^2=I$. Therefore $(\Delta Z)^2=1-\langle Z\rangle^2$ and $(\Delta X)^2=1-\langle X\rangle^2$. Also $[Z,X]=2iY$:

$$
\begin{aligned}
& (1-\langle Z\rangle^2)(1-\langle X\rangle^2)-\langle Y\rangle^2\\
&=1-\langle Z\rangle^2-\langle X\rangle^2
+\langle X\rangle^2\langle Z\rangle^2-\langle Y\rangle^2\\
&=\langle X\rangle^2\langle Z\rangle^2.
\end{aligned}
$$

Hence equality holds **if and only if**

$$
\boxed{\langle X\rangle\langle Z\rangle=0}
\quad\Longleftrightarrow\quad
\boxed{\sin\theta\cos\phi=0\ \text{or}\ \cos\theta=0}.
$$

Explicitly, these states comprise the $Y$–$Z$ great circle ($\langle X\rangle=0$) **or** the $X$–$Y$ great circle ($\langle Z\rangle=0$) on the pure-state Bloch sphere. This includes $X$ eigenstates and $Z$ eigenstates, for which one variance vanishes.

**Why are they eigenstates of $aZ+ibX$?** The general equality condition behind the Robertson inequality (including zero-variance cases, handled by allowing $a=0$ or $b=0$) is linear dependence of

$$
|u\rangle=(Z-\langle Z\rangle)|\psi\rangle,\qquad
|v\rangle=(X-\langle X\rangle)|\psi\rangle.
$$

When the Robertson bound is saturated, the relevant proportionality is purely imaginary, giving $a|u\rangle+ib|v\rangle=0$ for real $a,b$, not both zero. Rearrangement yields

$$
\boxed{(aZ+ibX)|\psi\rangle
=(a\langle Z\rangle+ib\langle X\rangle)|\psi\rangle.}
$$

One can **check constructively** for each family, retaining the natural handwritten-solution approach:

For a fully explicit check without guesswork, take a state with $\langle X\rangle=0$. Its Bloch vector is $(0,y,z)$ and $Y Z=iX$, so

$$
(Z-zI)|\psi\rangle
= (Z-zI)(yY+zZ)|\psi\rangle
$$

is not by itself a useful eigenvalue equation; instead, applying $(\boldsymbol n\cdot\boldsymbol\sigma)|\psi\rangle=|\psi\rangle$ gives $(yY+zZ)|\psi\rangle=|\psi\rangle$. Multiply by $Z$:

$$
(zI+ yZY)|\psi\rangle=Z|\psi\rangle,
\quad ZY=-iX,
\quad\Rightarrow\quad (Z-zI)|\psi\rangle=-iyX|\psi\rangle.
$$

Thus $\boxed{(Z+iyX)|\psi\rangle=z|\psi\rangle}$: choose $a=1,b=y$ (including $y=0$). Likewise when $\langle Z\rangle=0$, the Bloch vector $(x,y,0)$ yields $\boxed{(iyZ+X)|\psi\rangle=x|\psi\rangle}$ after multiplying $(xX+yY)|\psi\rangle=|\psi\rangle$ by $X$ and using $XY=iZ$; multiplying the equation by $i$ gives a valid $aZ+ibX$ form, with real $a=y,b=1$. These identities verify the claimed eigenstate condition including the endpoints.

**Guess the other pairwise equality conditions.** Cycling $(X,Y,Z)$ and using $[Y,Z]=2iX$, $[X,Y]=2iZ$ gives

$$
\boxed{\begin{aligned}
Y,Z:\quad&\langle Y\rangle\langle Z\rangle=0,\\
X,Y:\quad&\langle X\rangle\langle Y\rangle=0.
\end{aligned}}
$$

**Exam checks:** use the correct commutator sign; note the inequality requires the *absolute square*, so its sign drops out; check any zero-variance eigenstate cases separately instead of dividing by a variance.

## Problem 3 (40 points) — Position, momentum, and gauge phase

> [!important] Technical convention
> The question calls $|0\rangle$ a **normalized position eigenstate**. In a continuous position spectrum, an exact $|x\rangle$ is instead a generalized, delta-normalized eigenket and is not a normalizable Hilbert-space vector. Below we follow the question's formal ket manipulations, interpreting normalization of $|0\rangle$ as a simplification or as a regulated finite-volume/discrete analogue. On $\mathbb R$, the momentum eigenfunctions are also delta-normalized.

### (a)(i) Translation preserves the norm

Define $T(a)=e^{-ia\hat p/\hbar}$, where $\hat p=\hat p^\dagger$ and $a\in\mathbb R$. The adjoint is $T(a)^\dagger=e^{ia\hat p/\hbar}$ and the exponents commute, hence

$$
\begin{aligned}
\|T(a)|0\rangle\|^2
&=\langle0|T(a)^\dagger T(a)|0\rangle\\
&=\langle0|e^{ia\hat p/\hbar}e^{-ia\hat p/\hbar}|0\rangle
=\langle0|0\rangle.
\end{aligned}
$$

Thus a nonzero ket remains nonzero. The statement is formal for position eigenkets, as noted above.

### (a)(ii) Prove that the translated state has position eigenvalue $a$

Recall $[\hat x,\hat p]=i\hbar I$. Apply Hadamard with $A=ia\hat p/\hbar$; only the first commutator survives:

$$
\begin{aligned}
T(a)^\dagger\hat x T(a)
&=e^{ia\hat p/\hbar}\hat x e^{-ia\hat p/\hbar}\\
&=\hat x+[ia\hat p/\hbar,\hat x]\\
&=\hat x+\frac{ia}{\hbar}(-i\hbar)I=\hat x+aI.
\end{aligned}
$$

Multiply on the left by $T(a)$ to obtain $\hat xT(a)=T(a)(\hat x+aI)$. Therefore, since $\hat x|0\rangle=0$,

$$
\hat xT(a)|0\rangle=T(a)(\hat x+aI)|0\rangle=aT(a)|0\rangle.
$$

So $T(a)|0\rangle$ is a position eigenket with eigenvalue $a$.

**Momentum eigenwavefunction.** With $|x\rangle=T(x)|0\rangle$,

$$
\begin{aligned}
\langle x|p\rangle
&=\langle0|e^{ix\hat p/\hbar}|p\rangle\\
&=\boxed{e^{ixp/\hbar}\langle0|p\rangle},
\end{aligned}
$$

because $\hat p|p\rangle=p|p\rangle$. Standard delta normalization gives $\langle0|p\rangle=(2\pi\hbar)^{-1/2}$ up to an overall phase.

**Rephased position basis.** If $|x\rangle_{\phi}=e^{i\phi(x)}T(x)|0\rangle$ for real $\phi$, take its adjoint:

$$
{}_{\phi}\langle x|=e^{-i\phi(x)}\langle0|e^{ix\hat p/\hbar}.
$$

Hence

$$
\boxed{{}_{\phi}\langle x|p\rangle=e^{-i\phi(x)}e^{ixp/\hbar}\langle0|p\rangle.}
$$

The *bra* acquires the negative phase. This is a change of basis convention, not a change in measured momentum eigenvalues.

### (b)(i) Vanishing electromagnetic four-potential

Using minimal coupling, the quantum Hamiltonian is

$$
\hat H=\frac1{2m}\left(\hat{\boldsymbol p}-\frac qc\boldsymbol A(\hat{\boldsymbol x})\right)^2+q\Phi(\hat{\boldsymbol x}).
$$

For $(\Phi,\boldsymbol A)=(0,\boldsymbol0)$, $\hat H_0=\hat{\boldsymbol p}^{\,2}/(2m)$. In infinite space, generalized momentum eigenstates are

$$
\boxed{\psi_{\boldsymbol k}^{(0)}(\boldsymbol r)
=\frac{e^{i\boldsymbol k\cdot\boldsymbol r}}{(2\pi)^{3/2}},\qquad
E_{\boldsymbol k}=\frac{\hbar^2|\boldsymbol k|^2}{2m}.}
$$

This normalization means $\int d^3r\,\psi_{\boldsymbol k}^*\psi_{\boldsymbol k'}=\delta^3(\boldsymbol k-\boldsymbol k')$. If ordinary norm-one eigenstates are desired, introduce a finite box of volume $V$ (with compatible boundary conditions), use $V^{-1/2}e^{i\boldsymbol k\cdot\boldsymbol r}$, and quantize the allowed momenta.

### (b)(ii) Potential $\boldsymbol A=(Bx,0,0)$ and $\Phi=0$

The notation $Bx$ means $B\,x$ in the $x$-component of the vector potential; $B$ is a constant, **not a magnetic field pointing along $x$**. The Hamiltonian in the position representation is

$$
\boxed{\hat H_B=\frac1{2m}\left[\left(-i\hbar\partial_x-\frac{qB}{c}x\right)^2-\hbar^2\partial_y^2-\hbar^2\partial_z^2\right].}
$$

Here $\boldsymbol A=\nabla\chi$ with $\chi=Bx^2/2$, so let $G(\boldsymbol r)=e^{iq\chi(\boldsymbol r)/(\hbar c)}$. Direct differentiation checks the cancellation:

$$
\begin{aligned}
\left(-i\hbar\partial_x-\frac{qB}{c}x\right)(Gf)
&=-i\hbar\bigl[(\partial_xG)f+G\partial_xf\bigr]-\frac{qB}{c}xGf\\
&=G(-i\hbar\partial_x f),
\end{aligned}
$$

because $\partial_xG=i(qBx/\hbar c)G$. Similarly for $y,z$; therefore

$$
\hat H_B=G\hat H_0G^\dagger.
$$

The energies are unchanged, and the delta-normalized eigenfunctions are

$$
\boxed{\psi_{\boldsymbol k}^{(B)}(\boldsymbol r)
=\frac1{(2\pi)^{3/2}}\exp\!\left[\frac{i q Bx^2}{2\hbar c}+i\boldsymbol k\cdot\boldsymbol r\right],\quad
E_{\boldsymbol k}=\frac{\hbar^2|\boldsymbol k|^2}{2m}.}
$$

The extra phase has modulus one, so it preserves delta normalization. For a box one must transform the boundary conditions consistently under $G$.

### (c) Why both potentials give the same physics

First compute the fields, rather than interpreting $B$ as a magnetic field:

$$
\boldsymbol B_{\rm physical}=\nabla\times\boldsymbol A=\boldsymbol0,\qquad
\boldsymbol E=-\nabla\Phi-\frac1c\partial_t\boldsymbol A=\boldsymbol0.
$$

The potentials differ by the pure gauge $\boldsymbol A'=\boldsymbol A+\nabla\chi$, with $\chi=Bx^2/2$. The associated unitary operator $G=e^{iq\chi/(\hbar c)}$ relates the Hamiltonians and wavefunctions:

$$
\boxed{H_B=GH_0G^\dagger,\quad |\psi_B\rangle=G|\psi_0\rangle,\quad
H_B|\psi_B\rangle=E|\psi_B\rangle.}
$$

Furthermore $|\psi_B(\boldsymbol r)|^2=|\psi_0(\boldsymbol r)|^2$. To compare other observables, transform them as $O_B=GO_0G^\dagger$, yielding

$$
\langle\psi_B|O_B|\psi_B\rangle
=\langle\psi_0|G^\dagger GO_0G^\dagger G|\psi_0\rangle
=\langle\psi_0|O_0|\psi_0\rangle.
$$

Thus the different-looking wavefunctions are the same physics in gauge-related representations. **Cross-chapter connection:** this is the same structural idea as Chapter 2 dynamical pictures—unitary transformations redistribute the mathematical representation without changing measured predictions.

## Closed-book exercise checklist

1. Prove both $\operatorname{ad}$ identities, starting with an arbitrary test operator for the second.
2. Calculate the three Pauli expectation values using the conjugate bra, not by recalling only the Bloch-sphere final result.
3. Derive $\langle X\rangle\langle Z\rangle=0$ from the **difference** between the two sides of the uncertainty inequality; handle zero variances.
4. Derive the translation identity $T^\dagger xT=x+a$ and propagate the phase through $\langle x|p\rangle$.
5. For a pure gauge, calculate $\nabla\times A$, construct $G$, verify the derivative cancellation, then explain why energies and observables agree.
