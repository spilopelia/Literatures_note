---
title: AQM Chapter 1 — Homework 2 Extension
tags: [AQM, chapter-1, homework-2, long-questions, cross-chapter]
---

# AQM Chapter 1 — Homework 2 Extension

> [!info] Scope
> Supplement to [[AQM Chapter 1 - Long Questions Revised Handwritten-Style]]. Includes every part of **Homework 2 (PHYS 5410, 2024)** and the **original §1.6 mock question**. The worked solutions follow the supplied handwritten approach: write the definition, apply the operator, simplify line by line, and conclude. Where a handwritten shortcut is incomplete or a sign needs correction, the missing step is shown explicitly. HW2 crosses chapter boundaries; Q1–2 chiefly reinforce §1.4, Q3(a) reinforces §1.7, and Q3(b–c) extend to quantization and gauge transformations.

## Before starting — how to write these answers in an exam

Use the same order as a student solving on paper: **(1)** write the given relation; **(2)** calculate in the given basis; **(3)** substitute a previously established result; **(4)** simplify; **(5)** box the conclusion. Do not introduce a more abstract theorem when an explicit two-line calculation is enough. This note retains the handwritten solution’s order but repairs omitted calculations.

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

### (b) When is the $Z$–$X$ uncertainty relation an equality?

**Step 1: Start with the inequality in the question.**

$$
(\Delta Z)^2(\Delta X)^2\ge\frac14|\langle[Z,X]\rangle|^2.
$$

The Pauli operators satisfy $Z^2=X^2=I$ and $[Z,X]=2iY$. Hence

$$
\begin{aligned}
(\Delta Z)^2&=\langle Z^2\rangle-\langle Z\rangle^2=1-\langle Z\rangle^2,\\
(\Delta X)^2&=1-\langle X\rangle^2,\\
\frac14|\langle[Z,X]\rangle|^2
&=\frac14|2i\langle Y\rangle|^2=\langle Y\rangle^2.
\end{aligned}
$$

**Step 2: Use the result from (a), rather than expanding trigonometric functions immediately.** For a pure qubit state we already found

$$
\langle X\rangle^2+\langle Y\rangle^2+\langle Z\rangle^2=1.
$$

Therefore

$$
\begin{aligned}
(\Delta Z)^2(\Delta X)^2
&=(1-\langle Z\rangle^2)(1-\langle X\rangle^2)\\
&=1-\langle Z\rangle^2-\langle X\rangle^2
+\langle Z\rangle^2\langle X\rangle^2\\
&=\langle Y\rangle^2+\langle Z\rangle^2\langle X\rangle^2.
\end{aligned}
$$

Thus equality is equivalent to

$$
\boxed{\langle Z\rangle\langle X\rangle=0.}
$$

In terms of the original angles, using (a),

$$
\boxed{\cos\theta\,\sin\theta\cos\phi=0.}
$$

So there are two overlapping families: $\langle Z\rangle=0$ (equator $\theta=\pi/2$), or $\langle X\rangle=0$ ($\sin\theta\cos\phi=0$, including the poles). **Do not divide by** $\langle X\rangle$ or $\langle Z\rangle$, because that would discard valid cases.

**Step 3: Check the claimed eigenstate equation.** We want to find real $a,b$, not both zero, such that

$$
(aZ+ibX)|\psi\rangle=\lambda|\psi\rangle.
$$

We can proceed by the same case split as above. Recall a simple identity for the given pure qubit state: its Bloch expectations $x=\langle X\rangle$, $y=\langle Y\rangle$, $z=\langle Z\rangle$ satisfy

$$
(xX+yY+zZ)|\psi\rangle=|\psi\rangle.
$$

To check this identity directly, substitute $x=\sin\theta\cos\phi$, $y=\sin\theta\sin\phi$, $z=\cos\theta$ and multiply the $2\times2$ matrix by $(c,e^{i\phi}s)^T$; both components return those of $|\psi\rangle$.

*Case 1: $\langle X\rangle=x=0$.* Then

$$
(yY+zZ)|\psi\rangle=|\psi\rangle.
$$

Multiply on the left by $Z$. As $ZY=-iX$ and $Z^2=I$,

$$
\begin{aligned}
(-iyX+zI)|\psi\rangle&=Z|\psi\rangle,\\
\boxed{(Z+iyX)|\psi\rangle}&=z|\psi\rangle.
\end{aligned}
$$

Thus take $a=1$, $b=y$, and $\lambda=z$, all consistent with real $a,b$.

*Case 2: $\langle Z\rangle=z=0$.* Now

$$
(xX+yY)|\psi\rangle=|\psi\rangle.
$$

Multiply by $X$. Since $XY=iZ$,

$$
\begin{aligned}
(xI+iyZ)|\psi\rangle&=X|\psi\rangle,\\
(X-iyZ)|\psi\rangle&=x|\psi\rangle,\\
\boxed{(yZ+iX)|\psi\rangle}&=ix|\psi\rangle.
\end{aligned}
$$

Here the **last line is obtained by multiplying by $i$**; take $a=y$, $b=1$ and $\lambda=ix$. This corrects a sign in the previous version of this note. Both cases are genuine eigenstate equations, including the zero-variance endpoints.

**Step 4: Guess the other uncertainty-equality conditions by cycling $X,Y,Z$.** From

$$
[X,Y]=2iZ,\qquad [Y,Z]=2iX,
$$

we obtain exactly the analogous results

$$
\boxed{\begin{aligned}
Y,Z:\quad&\langle Y\rangle\langle Z\rangle=0,\\
X,Y:\quad&\langle X\rangle\langle Y\rangle=0.
\end{aligned}}
$$

**Student check:** the sequence to remember is *variances → commutator → use $x^2+y^2+z^2=1$ → factor → split cases → eigenvalue check*. You do not need to memorize the eigenvalue $\lambda$ in advance.

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

---

## Additional practice — Lecture §1.6 Density operators (original HW2-style, 40 points)

> [!important] Status
> This is a newly written **practice question**, not an assigned homework or past-exam question. It is based on lecture §1.6 (density operators, partial trace, reduced states and local observables). It deliberately combines several skills in a single long question.

Consider two qubits $A$ and $B$ in the normalized pure state

$$
|\psi\rangle=\frac{\sqrt3}{2}|00\rangle+\frac12|11\rangle,
\qquad |ij\rangle=|i\rangle_A\otimes|j\rangle_B.
$$

**(a) (10 points)** Construct $\rho_{AB}=|\psi\rangle\langle\psi|$. Find $\rho_A=\operatorname{Tr}_B\rho_{AB}$ and $\rho_B=\operatorname{Tr}_A\rho_{AB}$, and verify their defining density-operator properties.

**(b) (10 points)** Use $\operatorname{Tr}(\rho^2)$ to decide whether $\rho_{AB}$ and $\rho_A$ are pure or mixed. Explain the apparent difference.

**(c) (10 points)** Measure $X_A=X\otimes I$. Determine each outcome probability, the normalized post-measurement joint state and the conditional state of $B$.

**(d) (10 points)** Compare the state with

$$
\sigma_{AB}=\frac34|00\rangle\langle00|+\frac14|11\rangle\langle11|.
$$

Show that the two states give identical expectation values for **all local observables on $A$**, then construct a joint observable that distinguishes them, calculating both expectations.

### Worked solution — student-style derivation

#### (a) Write $\rho_{AB}$ and take the partial traces

**Step 1: Expand the outer product.** Let $a=\sqrt3/2$ and $b=1/2$. Here both are real, so

$$
\begin{aligned}
\rho_{AB}&=|\psi\rangle\langle\psi|\\
&=(a|00\rangle+b|11\rangle)(a\langle00|+b\langle11|)\\
&=a^2|00\rangle\langle00|+ab|00\rangle\langle11|\\
&\quad+ab|11\rangle\langle00|+b^2|11\rangle\langle11|\\
&=\boxed{\frac34|00\rangle\langle00|+\frac{\sqrt3}{4}|00\rangle\langle11|
+\frac{\sqrt3}{4}|11\rangle\langle00|+\frac14|11\rangle\langle11|}.
\end{aligned}
$$

**Step 2: Trace out $B$, term by term.** Recall the rule

$$
\operatorname{Tr}_B\left(|i\rangle_A|j\rangle_B\,{}_A\langle k|{}_B\langle l|\right)
=|i\rangle_A{}_A\langle k|\,\langle l|j\rangle_B.
$$

For the diagonal and a cross term,

$$
\begin{aligned}
\operatorname{Tr}_B(|00\rangle\langle00|)&=|0\rangle\langle0|\langle0|0\rangle=|0\rangle\langle0|,\\
\operatorname{Tr}_B(|00\rangle\langle11|)&=|0\rangle\langle1|\langle1|0\rangle=0,\\
\operatorname{Tr}_B(|11\rangle\langle00|)&=0,\\
\operatorname{Tr}_B(|11\rangle\langle11|)&=|1\rangle\langle1|.
\end{aligned}
$$

Therefore,

$$
\boxed{\rho_A=\frac34|0\rangle\langle0|+\frac14|1\rangle\langle1|
=\begin{pmatrix}3/4&0\\0&1/4\end{pmatrix}.}
$$

Tracing out $A$ instead gives, by the same four terms,

$$
\boxed{\rho_B=\frac34|0\rangle\langle0|+\frac14|1\rangle\langle1|.}
$$

**Step 3: Check the density-operator properties.** For $\rho_A$ and $\rho_B$,

$$
\rho^\dagger=\rho,\quad \operatorname{Tr}\rho=\frac34+\frac14=1,
\quad \langle v|\rho|v\rangle=\frac34|v_0|^2+\frac14|v_1|^2\ge0.
$$

So both reduced operators are valid density operators. For $\rho_{AB}$, the same properties follow immediately from $\rho_{AB}=|\psi\rangle\langle\psi|$ and $\langle\psi|\psi\rangle=1$.

#### (b) Pure or mixed? Calculate rather than guess

The purity test is $\operatorname{Tr}(\rho^2)=1$ for a pure state and less than $1$ for a mixed state.

For the joint state,

$$
\begin{aligned}
\rho_{AB}^2&=|\psi\rangle\langle\psi|\psi\rangle\langle\psi|\\
&=|\psi\rangle\langle\psi|=\rho_{AB},\\
\boxed{\operatorname{Tr}(\rho_{AB}^2)}&=1.
\end{aligned}
$$

For the reduced state, use the matrix from (a):

$$
\begin{aligned}
\rho_A^2&=\begin{pmatrix}3/4&0\\0&1/4\end{pmatrix}^2
=\begin{pmatrix}9/16&0\\0&1/16\end{pmatrix},\\
\boxed{\operatorname{Tr}(\rho_A^2)}&=\frac9{16}+\frac1{16}=\frac58<1.
\end{aligned}
$$

Hence the **whole system is pure** while **subsystem $A$ is mixed**. The two qubits are entangled, so discarding $B$ discards information about correlations.

#### (c) Measure $X$ on qubit $A$

**Step 1: Write the measurement eigenstates and projectors.**

$$
|\pm\rangle=\frac{|0\rangle\pm|1\rangle}{\sqrt2},\qquad
P_\pm=|\pm\rangle\langle\pm|\otimes I.
$$

**Step 2: Expand the given state in this measurement basis.** Recall

$$
|0\rangle=\frac{|+\rangle+|-\rangle}{\sqrt2},\qquad
|1\rangle=\frac{|+\rangle-|-\rangle}{\sqrt2}.
$$

Substitution gives

$$
\begin{aligned}
|\psi\rangle
&=a\left(\frac{|+\rangle+|-\rangle}{\sqrt2}\right)|0\rangle
+b\left(\frac{|+\rangle-|-\rangle}{\sqrt2}\right)|1\rangle\\
&=\frac1{\sqrt2}|+\rangle(a|0\rangle+b|1\rangle)
+\frac1{\sqrt2}|-\rangle(a|0\rangle-b|1\rangle).
\end{aligned}
$$

**Step 3: Project, find probabilities, and normalize.** Since $\langle\pm|\mp\rangle=0$,

$$
\begin{aligned}
P_+|\psi\rangle&=\frac1{\sqrt2}|+\rangle(a|0\rangle+b|1\rangle),\\
P_-|\psi\rangle&=\frac1{\sqrt2}|-\rangle(a|0\rangle-b|1\rangle).
\end{aligned}
$$

As $a^2+b^2=1$,

$$
\boxed{p_+=\langle\psi|P_+|\psi\rangle=\frac12,\qquad
p_-=\langle\psi|P_-|\psi\rangle=\frac12.}
$$

Now divide by $\sqrt{p_\pm}=1/\sqrt2$:

$$
\boxed{\begin{aligned}
|\psi_+\rangle&=|+\rangle\otimes\left(\frac{\sqrt3}{2}|0\rangle+\frac12|1\rangle\right),\\
|\psi_-\rangle&=|-\rangle\otimes\left(\frac{\sqrt3}{2}|0\rangle-\frac12|1\rangle\right).
\end{aligned}}
$$

**Step 4: Read off $B$'s conditional states.** The result for $A$ is already a product state, so

$$
\boxed{|\phi_B^\pm\rangle=\frac{\sqrt3}{2}|0\rangle\pm\frac12|1\rangle.}
$$

If the result on $A$ is not selected, averaging the two conditional density operators cancels their cross terms and recovers $\rho_B$ from (a).

#### (d) Compare the pure state and the classical mixture

**Step 1: Compare what $A$ alone can see.** The other joint state is

$$
\sigma_{AB}=\frac34|00\rangle\langle00|+\frac14|11\rangle\langle11|.
$$

Trace out $B$ just as in (a):

$$
\operatorname{Tr}_B\sigma_{AB}
=\frac34|0\rangle\langle0|+\frac14|1\rangle\langle1|
=\rho_A.
$$

For any observable $O_A$ acting only on $A$,

$$
\begin{aligned}
\operatorname{Tr}[\rho_{AB}(O_A\otimes I)]
&=\operatorname{Tr}(\rho_A O_A)\\
&=\operatorname{Tr}[\sigma_{AB}(O_A\otimes I)].
\end{aligned}
$$

Thus **no measurement on $A$ alone distinguishes them**.

**Step 2: Try a joint observable sensitive to the cross terms.** Choose $X\otimes X$ because

$$
(X\otimes X)|00\rangle=|11\rangle,\qquad
(X\otimes X)|11\rangle=|00\rangle.
$$

For the pure state,

$$
\begin{aligned}
\langle X\otimes X\rangle_{\rho}
&=\langle\psi|(X\otimes X)|\psi\rangle\\
&=(a\langle00|+b\langle11|)(a|11\rangle+b|00\rangle)\\
&=ab+ba=2ab=\boxed{\frac{\sqrt3}{2}}.
\end{aligned}
$$

For the mixture,

$$
\begin{aligned}
\langle X\otimes X\rangle_{\sigma}
&=\frac34\langle00|X\otimes X|00\rangle
+\frac14\langle11|X\otimes X|11\rangle\\
&=\boxed{0}.
\end{aligned}
$$

**Conclusion:** the two states have the same reduced density operator on $A$ but different *joint coherences*. An observable involving both qubits can detect that difference.

### Closed-book plan for this mock problem

- **(a)** Expand all four outer-product terms, trace term-by-term, then check Hermiticity, trace and positivity.
- **(b)** Square $\rho_{AB}$ using projector normalization; square the diagonal reduced matrix explicitly.
- **(c)** Rewrite $|0\rangle,|1\rangle$ in the $X$ basis, project, take norms, and normalize.
- **(d)** First compare reduced states; then look for an operator exchanging $|00\rangle$ and $|11\rangle$ to test the missing coherence.
