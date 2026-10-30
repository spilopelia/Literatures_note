---
title: "AQM Chapter 1 — Long-Question Exam Revision"
aliases:
  - "AQM Chapter 1 Complete Revision"
tags:
  - AQM
  - quantum-mechanics
  - chapter-1
  - midterm
  - long-questions
---

# AQM Chapter 1 — Long-Question Exam Revision

> [!info] Sources and scope
> Tian Lan, *Advanced Quantum Mechanics*, Chapter 1 (§§1.1–1.7), including every numbered lecture problem and all subparts of Homework 1. The midterm covers **Weeks 1–5**, so this note covers **Chapter 1 only**, not necessarily the entire examination. The updated assumption is that the paper uses **long questions**; the earlier MCQ/terminology breakdown is superseded.

> [!abstract] Navigation
> - [[#Part I — Reference: concepts, starting equations, and derivation map|Part I — Formula and derivation reference]]
> - [[#Part II — Worked lecture problems|Part II — Lecture problems]]
> - [[#Part III — Worked Homework 1|Part III — Homework 1]]
> - [[#Final closed-book rehearsal|Closed-book rehearsal]]
>
> All equations use Obsidian's MathJax-compatible `$...$` (inline) and `$$...$$` (display) delimiters. Switch to Reading view or Live Preview to render them.


## How to use this note for long questions

1. **First pass — derivation map:** Memorize the *starting equation*, mathematical justification, and final result for each topic in Part I. Do not memorize only final matrices.
2. **Second pass — closed-book reproduction:** For each problem in Part II and Part III, cover the answer and write the solution yourself, including any normalization, projection or sign manipulation.
3. **Third pass — mixed questions:** Chain results together: Pauli eigensystem → measurement → conditional state; tensor product → Bell basis → projection → correction; density matrix → partial trace → purity; Fourier transform → differential operator → commutator.
4. **Check:** Test operator order, conjugates, dimensions, state normalization, and whether a result is exact or only equal up to global phase.

> [!warning] Important conventions
> $|\psi\rangle$ is normalized unless otherwise specified. Bell states use the **ordered qubit positions** stated in the homework. Exponents of $X$ and $Z$ on qubits are taken modulo 2. A global phase is physically irrelevant but should be retained when the homework requests an exact algebraic identity.

## Long-question starting-point index

| If the question says…              | Begin with…                                                                                                                               |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Determine eigenvalues/eigenvectors | $\det(A-\lambda I)=0$, then $(A-\lambda I)\vert v\rangle=0$ and normalize                                                                 |
| Compute outcome and probability    | Spectral projector $P_\lambda$, then $p_\lambda=\langle\psi\vert P_\lambda\vert \psi\rangle$                                              |
| Subsequent measurement             | Replace the initial state by $P_\lambda\vert \psi\rangle/\sqrt{p_\lambda}$                                                                |
| Act on one subsystem               | Insert $A\otimes I$ or $I\otimes B$ before applying the operator                                                                          |
| Compute reduced state              | Expand $\rho$ and use $$\operatorname{Tr}_2(\vert i\alpha\rangle\langle j\beta\vert )=\delta_{\alpha\beta}\vert i\rangle\langle j\vert $$ |
| Prove a commutator identity        | Expand $[A,B]=AB-BA$ and use associativity                                                                                                |
| Prove uncertainty inequality       | Set $\vert u\rangle=\delta A\vert \psi\rangle$, $\vert v\rangle=\delta B\vert \psi\rangle$ and use Cauchy–Schwarz                         |
| Fourier / momentum                 | Insert $I=\int dp\,\vert p\rangle\langle p\vert $ and differentiate $e^{ipx/\hbar}$                                                       |
| No cloning                         | Apply inner-product preservation to two states before and after copying                                                                   |

---

## Part I — Reference: concepts, starting equations, and derivation map

#### 1. Postulates and quantum states (§§1.1, 1.3)

- **Hilbert space:** complete complex inner-product space $\mathcal H$; every Cauchy sequence converges in the space.
- **State:** a nonzero ket $|\psi\rangle\in\mathcal H$. A physical pure state is a *ray*: $|\psi\rangle\sim c|\psi\rangle$ for any $c\ne0$.
- **Superposition:** linear combination $c_1|\alpha\rangle+c_2|\beta\rangle$.
- **Global phase:** $e^{i\chi}|\psi\rangle$ represents the same pure state; a relative phase generally affects measurements.
- **Observable:** Hermitian operator $O=O^\dagger$; possible measurement results are its eigenvalues.
- **Measurement projector:** $P_\lambda$ is the orthogonal projector onto the *whole* eigenspace of outcome $\lambda$.

For a normalized state and ideal projective measurement:

$$
P(\lambda)=\langle\psi|P_\lambda|\psi\rangle,\qquad
|\psi_\lambda\rangle=\frac{P_\lambda|\psi\rangle}{\sqrt{\langle\psi|P_\lambda|\psi\rangle}}.
$$

For an unnormalized ket divide probabilities by $\langle\psi|\psi\rangle$. For nondegenerate $\lambda$, $P_\lambda=|\lambda\rangle\langle\lambda|$ and $P(\lambda)=|\langle\lambda|\psi\rangle|^2$ when normalized. The expectation is

$$
\langle O\rangle=\frac{\langle\psi|O|\psi\rangle}{\langle\psi|\psi\rangle}.
$$

> [!warning] Common T/F trap
> An expectation value is an average, **not** necessarily one of the observable's eigenvalues. A projective measurement onto a degenerate eigenspace need not yield one unique eigenvector.

#### 2. Linear algebra (§1.2)

##### Fundamental vocabulary

| Term | Definition / test |
|---|---|
| Complex vector space | Addition and complex scalar multiplication satisfying the eight vector-space axioms |
| Linear map | $A(cu+dv)=cAu+dAv$ |
| Basis | Linearly independent spanning family; unique vector expansion |
| Dimension | Number of elements in a basis (finite-dimensional case) |
| Inner product | Linear in the second argument, conjugate-linear in the first; conjugate symmetric and positive definite |
| Orthogonal vectors | $\langle\alpha\vert \beta\rangle=0$ |
| Orthonormal basis | $\langle i\vert j\rangle=\delta_{ij}$ |
| Adjoint | $\langle\beta\vert A\alpha\rangle=\langle A^\dagger\beta\vert \alpha\rangle$; conjugate transpose in an orthonormal basis |
| Hermitian | $A=A^\dagger$; eigenvalues real |
| Unitary | $U^\dagger U=UU^\dagger=I$ (same space); preserves inner products |
| Normal | $AA^\dagger=A^\dagger A$; unitarily diagonalizable in finite dimensions |
| Orthogonal projector | $P^2=P=P^\dagger$ |
| Degenerate eigenvalue | Corresponding eigenspace dimension $>1$ |
| Trace | $\operatorname{Tr}A=\sum_i\langle i\vert A\vert i\rangle$, independent of orthonormal basis |

##### Recite these identities

$$
\begin{gathered}
\langle\alpha|c\beta\rangle=c\langle\alpha|\beta\rangle,\qquad
\langle c\alpha|\beta\rangle=c^*\langle\alpha|\beta\rangle,\\
(AB)^\dagger=B^\dagger A^\dagger,\qquad(cA)^\dagger=c^*A^\dagger,\\
\sum_i|i\rangle\langle i|=I,\qquad
A=\sum_\lambda\lambda P_\lambda\quad(A=A^\dagger),\\
\operatorname{Tr}(AB)=\operatorname{Tr}(BA),\qquad
\operatorname{Tr}(U^\dagger A U)=\operatorname{Tr}(A).
\end{gathered}
$$

**Operator inner product (Hilbert–Schmidt):**

$$
(A,B)_{\mathrm{HS}}=\operatorname{Tr}(A^\dagger B),\qquad
\operatorname{Tr}(A^\dagger A)=\sum_i\|A|i\rangle\|^2\ge0.
$$

##### Pauli matrices — memorize exactly

$$
X=\begin{pmatrix}0&1\\1&0\end{pmatrix},\quad
Y=\begin{pmatrix}0&-i\\i&0\end{pmatrix},\quad
Z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
$$

$$
X^2=Y^2=Z^2=I,\qquad
XY=iZ,\quad YZ=iX,\quad ZX=iY.
$$

Reverse the order to reverse the sign: $YX=-iZ$, etc. Hence

$$
[\sigma_i,\sigma_j]=2i\sum_k\epsilon_{ijk}\sigma_k,\qquad
\operatorname{Tr}(\sigma_\mu^\dagger\sigma_\nu)=2\delta_{\mu\nu}
$$

where $\sigma_\mu\in\{I,X,Y,Z\}$. Every $2\times2$ operator has the expansion

$$
A=\frac12\sum_{\mu\in\{0,x,y,z\}}\operatorname{Tr}(\sigma_\mu A)\sigma_\mu,\qquad\sigma_0=I.
$$

| Operator | $+1$ eigenstate | $-1$ eigenstate |
|---|---|---|
| $Z$ | $\vert 0\rangle$ | $\vert 1\rangle$ |
| $X$ | $(\vert 0\rangle+\vert 1\rangle)/\sqrt2$ | $(\vert 0\rangle-\vert 1\rangle)/\sqrt2$ |
| $Y$ | $(\vert 0\rangle+i\vert 1\rangle)/\sqrt2$ | $(\vert 0\rangle-i\vert 1\rangle)/\sqrt2$ |

**General Hermitian $2\times2$ matrix:**

$$
H=aI+xX+yY+zZ=\begin{pmatrix}a+z&x-iy\\x+iy&a-z\end{pmatrix}.
$$

Write $(x,y,z)=r(\sin\theta\cos\phi,\sin\theta\sin\phi,\cos\theta)$. Then

$$
\lambda_\pm=a\pm r,\quad
|+\rangle=\begin{pmatrix}\cos(\theta/2)\\e^{i\phi}\sin(\theta/2)\end{pmatrix},\quad
|-\rangle=\begin{pmatrix}-e^{-i\phi}\sin(\theta/2)\\\cos(\theta/2)\end{pmatrix}.
$$

If $r=0$, $H=aI$ has a degenerate eigenvalue and no preferred eigenbasis. Eigenvectors are defined up to individual nonzero factors/phases.

#### 3. Measurements of a qubit (§1.3)

For normalized $|\psi\rangle=a|0\rangle+b|1\rangle$:

| Measurement | $P(+1)$ | $P(-1)$ |
|---|---|---|
| $Z$ | $\vert a\vert^2$ | $\vert b\vert^2$ |
| $X$ | $\vert a+b\vert^2/2$ | $\vert a-b\vert^2/2$ |
| $Y$ | $\vert a-ib\vert^2/2$ | $\vert a+ib\vert^2/2$ |

$$
\langle Z\rangle=|a|^2-|b|^2,\quad
\langle X\rangle=2\operatorname{Re}(a^*b),\quad
\langle Y\rangle=2\operatorname{Im}(a^*b).
$$

Pure-state Bloch parametrization:

$$
|\psi\rangle=\cos\frac\theta2|0\rangle+e^{i\phi}\sin\frac\theta2|1\rangle,\qquad
\langle X\rangle^2+\langle Y\rangle^2+\langle Z\rangle^2=1.
$$

After obtaining $Z=+1$, an immediate repeat ideal $Z$ measurement yields $+1$ with certainty. After obtaining $Y=-1$, measuring $X$ gives $\pm1$ with probability $1/2$ each.

#### 4. Commutators and uncertainty (§1.4)

Two Hermitian operators are **compatible** in finite dimensions exactly when they commute (equivalently, they admit a common orthonormal eigenbasis).

$$
\begin{aligned}
[A,B]&=AB-BA=-[B,A],\\
[A,B+C]&=[A,B]+[A,C],\\
[A,BC]&=[A,B]C+B[A,C],\\
[A,[B,C]]+[B,[C,A]]+[C,[A,B]]&=0.
\end{aligned}
$$

The last identity is the **Jacobi identity**. Let $\delta A=A-\langle A\rangle I$ and $\Delta A=\sqrt{\langle(\delta A)^2\rangle}$ for normalized states. Then

$$
\Delta A\,\Delta B\ge\frac12\big|\langle[A,B]\rangle\big|.
$$

**Equality:** either $\Delta A=0$ or $\Delta B=0$, or, if both are nonzero,

$$
\delta A|\psi\rangle=i\xi\,\delta B|\psi\rangle,\qquad\xi\in\mathbb R.
$$

> [!warning] T/F trap
> $[A,B]\ne0$ does **not** imply that $\langle[A,B]\rangle\ne0$ in every state, nor that the Robertson lower bound is always strictly positive.

#### 5. Tensor products and composite systems (§1.5)

$$
\begin{aligned}
\mathcal H_{12}&=\mathcal H_1\otimes\mathcal H_2,\\
\dim(V\otimes W)&=(\dim V)(\dim W),\\
(A\otimes B)(|u\rangle\otimes|v\rangle)&=A|u\rangle\otimes B|v\rangle,\\
(A\otimes B)(C\otimes D)&=AC\otimes BD,\\
[A\otimes I,I\otimes B]&=0,\\
(A\otimes B)_{i\alpha,j\beta}&=A_{ij}B_{\alpha\beta}.
\end{aligned}
$$

In the ordered basis $\{|00\rangle,|01\rangle,|10\rangle,|11\rangle\}$,

$$
(a|0\rangle+b|1\rangle)\otimes(c|0\rangle+d|1\rangle)
=\begin{pmatrix}ac\\ad\\bc\\bd\end{pmatrix}.
$$

A pure state is **entangled** if it cannot be written as a single tensor product of subsystem state vectors. E.g. $(|00\rangle+|11\rangle)/\sqrt2$.

#### 6. Density operators and partial trace (§1.6)

$$
\rho=\sum_i p_i|\psi_i\rangle\langle\psi_i|,\qquad
\rho^\dagger=\rho,\quad\operatorname{Tr}\rho=1,\quad\rho\ge0.
$$

$$
\begin{aligned}
P(\lambda)&=\operatorname{Tr}(\rho P_\lambda),\\
\langle O\rangle&=\operatorname{Tr}(\rho O),\\
\rho_\lambda&=\frac{P_\lambda\rho P_\lambda}{\operatorname{Tr}(\rho P_\lambda)},\\
\rho_1&=\operatorname{Tr}_2\rho
=\sum_b(I\otimes\langle b|)\rho(I\otimes|b\rangle),\\
\operatorname{Tr}[\rho(O\otimes I)]&=\operatorname{Tr}(\rho_1O).
\end{aligned}
$$

Component shortcut: $(\rho_1)_{ij}=\sum_b\rho_{ib,jb}$. For normalized pure states, $\rho^2=\rho$ and $\operatorname{Tr}\rho^2=1$; for genuinely mixed states, $\operatorname{Tr}\rho^2<1$.

**Pure reduced-state criterion:**

$$
\rho_1=|\phi\rangle\langle\phi|\quad\Longleftrightarrow\quad
\rho=|\phi\rangle\langle\phi|\otimes\rho_2.
$$

> [!example] Bell state partial trace
> $|\beta_{00}\rangle=(|00\rangle+|11\rangle)/\sqrt2$ is pure, but $\operatorname{Tr}_2(|\beta_{00}\rangle\langle\beta_{00}|)=I/2$ is mixed.

#### 7. Continuous position and momentum (§1.7)

$$
\begin{gathered}
\hat x|x\rangle=x|x\rangle,\quad
\langle x|y\rangle=\delta(x-y),\quad
I=\int dx\,|x\rangle\langle x|,\\
\psi(x)=\langle x|\psi\rangle,\quad
\langle\phi|\psi\rangle=\int dx\,\phi(x)^*\psi(x),\\
\langle x|A|\psi\rangle=\int dy\,\langle x|A|y\rangle\psi(y),\\
\int dx\,\delta(x-a)f(x)=f(a),\quad
\theta'(x)=\delta(x),\quad
\delta(x)=\frac1{2\pi}\int dk\,e^{ikx}.
\end{gathered}
$$

$$
[\hat x,\hat p]=i\hbar I,\qquad
\langle x|\hat p|\psi\rangle=-i\hbar\frac{d\psi(x)}{dx},\qquad
\langle x|p\rangle=\frac{e^{ipx/\hbar}}{\sqrt{2\pi\hbar}}.
$$

Fourier transform pair:

$$
\psi(x)=\frac1{\sqrt{2\pi\hbar}}\int dp\,e^{ipx/\hbar}\widetilde\psi(p),\qquad
\widetilde\psi(p)=\frac1{\sqrt{2\pi\hbar}}\int dx\,e^{-ipx/\hbar}\psi(x).
$$

For suitable $f$,

$$
\langle x|f(\hat x)|\psi\rangle=f(x)\psi(x),\quad
[\hat p,f(\hat x)]=-i\hbar f'(\hat x).
$$

> [!warning] Generalized states
> $|x\rangle$ and $|p\rangle$ are delta-normalized generalized eigenstates, not normalizable vectors in ordinary $L^2$. Plane-wave and delta identities are distributional.

#### 8. Homework-specific must-recites

**Bell basis:**

$$
\begin{aligned}
|\beta_{00}\rangle&=(|00\rangle+|11\rangle)/\sqrt2,\\
|\beta_{01}\rangle&=(|00\rangle-|11\rangle)/\sqrt2,\\
|\beta_{10}\rangle&=(|10\rangle+|01\rangle)/\sqrt2,\\
|\beta_{11}\rangle&=(|10\rangle-|01\rangle)/\sqrt2.
\end{aligned}
$$

**Teleportation expansion:**

$$
|\alpha\rangle_1|\beta_{00}\rangle_{23}
=\frac12\sum_{i,j=0}^1|\beta_{ij}\rangle_{12}\otimes Z^jX^i|\alpha\rangle_3.
$$

All four Bell outcomes have probability $1/4$; apply $X^iZ^j$ on qubit 3 to recover $|\alpha\rangle$.

**No cloning:** a putative universal $\operatorname{Clone}|\phi\rangle=|\phi\rangle\otimes|\phi\rangle$ is nonlinear. For an isometry copying two normalized states,

$$
\langle\phi|\psi\rangle=\langle\phi|\psi\rangle^2
\Rightarrow\langle\phi|\psi\rangle\in\{0,1\}.
$$

Distinct copied states are orthogonal, so at most $\dim V$ can be copied exactly. CNOT with a blank $|0\rangle$ copies $|0\rangle$ and $|1\rangle$.

#### 9. Self-test prompts

- [ ] Define Hilbert space, Hermitian, unitary, normal, projector, mixed state, eigenspace, entanglement.
- [ ] Write $X,Y,Z$ and all six $\pm1$ Pauli eigenstates.
- [ ] Explain why a determinant must vanish for an eigenvector to exist.
- [ ] State both the measurement probability and the *normalized* state update.
- [ ] Derive $\operatorname{Tr}_2$ of a Bell pair.
- [ ] State the uncertainty equality conditions, including zero-variance cases.
- [ ] Write the normalized $\langle x|p\rangle$ and Fourier transform conventions.
- [ ] Explain why arbitrary unknown pure states cannot be cloned.

See  and  for exam-length worked solutions.

---

## Part II — Worked lecture problems

#### Problem 1.2.1 — Vector-space identities

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

#### Problem 1.2.2 — Operators satisfy vector-space axioms

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

#### Problem 1.2.3 — Operator inner product

**Start:** To prove $(A,B)=\operatorname{Tr}(A^\dagger B)$ is an inner product, verify linearity, conjugate symmetry, and positivity.

$$
\begin{aligned}
(A,cB+dC)&=\operatorname{Tr}(A^\dagger(cB+dC))=c(A,B)+d(A,C),\\
(A,B)^*&=\operatorname{Tr}[(A^\dagger B)^\dagger]=\operatorname{Tr}(B^\dagger A)=(B,A),\\
(A,A)&=\sum_i\langle i|A^\dagger A|i\rangle=\sum_i\|A|i\rangle\|^2\ge0.
\end{aligned}
$$

Equality in the last line means $A|i\rangle=0$ for every basis ket, hence $A=0$. This establishes the inner product in finite dimensions.

#### Problem 1.2.4 — Six-part Pauli problem

##### (1) Determine $Z$

**Start:** Work in the eigenbasis, possible because $Z=Z^\dagger$.

$$
Z=\operatorname{diag}(\lambda_1,\lambda_2),\qquad Z^2=I\Rightarrow\lambda_i=\pm1.
$$

$\operatorname{Tr}Z=0$ gives $\lambda_1+\lambda_2=0$. Order the basis so

$$
\boxed{Z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.}
$$

##### (2) Determine $X$

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

##### (3) Construct $Y=iXZ$

$$
Y=i\begin{pmatrix}0&-1\\1&0\end{pmatrix}=\boxed{\begin{pmatrix}0&-i\\i&0\end{pmatrix}}.
$$

$$
Y^\dagger=-iZX=iXZ=Y,\qquad Y^2=-XZXZ=X^2Z^2=I,\qquad\operatorname{Tr}Y=0.
$$

##### (4) Orthogonal basis of operator space

Since all are Hermitian and traceless except $I$,

$$
\operatorname{Tr}(X)=\operatorname{Tr}(Y)=\operatorname{Tr}(Z)=0,
$$

and $XY=iZ$, $YZ=iX$, $ZX=iY$, cross inner products vanish. Also

$$
\operatorname{Tr}(I^2)=\operatorname{Tr}(X^2)=\operatorname{Tr}(Y^2)=\operatorname{Tr}(Z^2)=2.
$$

Thus $\operatorname{Tr}(\sigma_\mu^\dagger\sigma_\nu)=2\delta_{\mu\nu}$. Four nonzero orthogonal operators form a basis because $\dim\operatorname{Hom}(V,V)=2^2=4$. With $\frac12\operatorname{Tr}(A^\dagger B)$ they are orthonormal.

##### (5) Pauli commutators

$$
[X,Y]=iZ-(-iZ)=2iZ,\quad [Y,Z]=2iX,\quad[Z,X]=2iY.
$$

Reversed pairs have opposite signs; identical pairs commute. Hence

$$
\boxed{[\sigma_i,\sigma_j]=2i\sum_k\epsilon_{ijk}\sigma_k.}
$$

##### (6) General $2\times2$ Hermitian eigensystem

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

#### Problem 1.2.5 — Tensor-product bases and matrices

##### (1) Basis independence

Let $|e'_a\rangle=\sum_i S_{ia}|e_i\rangle$ and $|f'_b\rangle=\sum_j T_{jb}|f_j\rangle$ with invertible $S,T$. Bilinearity yields

$$
|e'_a\rangle\otimes|f'_b\rangle=\sum_{ij}S_{ia}T_{jb}|e_i\rangle\otimes|f_j\rangle.
$$

This is the invertible product basis change $S\otimes T$, with inverse $S^{-1}\otimes T^{-1}$. Thus the construction is basis-independent up to a canonical isomorphism.

##### (2) Tensor product of operator spaces

Using dual basis functionals (or ordinary bras for orthonormal bases), rank-one maps $|e'_a\rangle\langle e_i|$ and $|f'_b\rangle\langle f_j|$ form bases of the local operator spaces. Their product is

$$
 (|e'_a\rangle\langle e_i|)\otimes(|f'_b\rangle\langle f_j|)=|e'_af'_b\rangle\langle e_if_j|.
$$

These span all linear maps between product spaces, giving the finite-dimensional isomorphism

$$
\operatorname{Hom}(V\otimes W,V'\otimes W')\simeq\operatorname{Hom}(V,V')\otimes\operatorname{Hom}(W,W').
$$

##### (3) Matrix elements

$$
\boxed{\langle e_i f_\alpha|A\otimes B|e_j f_\beta\rangle=\langle e_i|A|e_j\rangle\langle f_\alpha|B|f_\beta\rangle=A_{ij}B_{\alpha\beta}.}
$$

#### Problem 1.3.1 — Measurements on $|\psi\rangle=a|0\rangle+b|1\rangle$

Assume $|a|^2+|b|^2=1$.

##### (1) Outcomes and probabilities

Eigenstates: $|x\pm\rangle=(|0\rangle\pm|1\rangle)/\sqrt2$ and $|y\pm\rangle=(|0\rangle\pm i|1\rangle)/\sqrt2$. Born's rule gives

| Observable | $P(+1)$ | $P(-1)$ |
|---|---|---|
| $Z$ | $\vert a\vert^2$ | $\vert b\vert^2$ |
| $X$ | $\vert a+b\vert^2/2$ | $\vert a-b\vert^2/2$ |
| $Y$ | $\vert a-ib\vert^2/2$ | $\vert a+ib\vert^2/2$ |

For example $\langle y+|\psi\rangle=(a-ib)/\sqrt2$. Remember to conjugate $i$ when forming $\langle y+|$.

##### (2) Expectations and polar coordinates

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

##### (3) Repeated $Z$ measurement

After $Z=+1$, the normalized state is $|0\rangle$. A second ideal $Z$ measurement gives $P(+1)=1$ and $P(-1)=0$.

##### (4) $Y=-1$ followed by $X$

Post-first-measurement: $|y-\rangle=(|0\rangle-i|1\rangle)/\sqrt2$.

$$
\langle x+|y-\rangle=\frac{1-i}{2},\qquad\langle x-|y-\rangle=\frac{1+i}{2}.
$$

Thus $\boxed{P(X=\pm1)=1/2}$.

#### Problem 1.4.1 — Equality in uncertainty relation

Set $|u\rangle=(A-\langle A\rangle)|\psi\rangle$, $|v\rangle=(B-\langle B\rangle)|\psi\rangle$. The proof uses

$$
\|u\|^2\|v\|^2\ge|\langle u|v\rangle|^2\ge[\operatorname{Im}\langle u|v\rangle]^2.
$$

Equality requires (i) $u,v$ linearly dependent, and (ii) the inner product purely imaginary. For nonzero deviations,

$$
\boxed{(A-\langle A\rangle)|\psi\rangle=i\xi(B-\langle B\rangle)|\psi\rangle,\quad\xi\in\mathbb R.}
$$

If either deviation vector is zero, equality also holds. Equivalently, with the sign convention $\eta=-\xi$, $(A+i\eta B)|\psi\rangle=\langle A+i\eta B\rangle|\psi\rangle$.

#### Problem 1.4.2 — Commutator identities

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

#### Problem 1.6.1 — Density formulas recover pure-state formulas

With normalized $\rho=|\psi\rangle\langle\psi|$,

$$
\operatorname{Tr}(\rho P_\lambda)=\langle\psi|P_\lambda|\psi\rangle,
$$

$$
\rho_\lambda=\frac{P_\lambda|\psi\rangle\langle\psi|P_\lambda}{\langle\psi|P_\lambda|\psi\rangle}=|\psi_\lambda\rangle\langle\psi_\lambda|,
$$

where $|\psi_\lambda\rangle=P_\lambda|\psi\rangle/\sqrt{\langle\psi|P_\lambda|\psi\rangle}$ for nonzero-probability outcomes. Also $\operatorname{Tr}(\rho O)=\langle\psi|O|\psi\rangle$. Thus all three formulas coincide with §1.3.

#### Problem 1.6.2 — Pure reduced state iff factorization

**($\Leftarrow$)** If $\rho=|\phi\rangle\langle\phi|\otimes\rho_2$,

$$
\operatorname{Tr}_2\rho=|\phi\rangle\langle\phi|\operatorname{Tr}\rho_2=|\phi\rangle\langle\phi|.
$$

**($\Rightarrow$)** Suppose $\rho_1=\operatorname{Tr}_2\rho=|\phi\rangle\langle\phi|$. Choose $|e_j\rangle\perp|\phi\rangle$. Then

$$
0=\langle e_j|\rho_1|e_j\rangle=\sum_b\langle e_jb|\rho|e_jb\rangle.
$$

Every summand is nonnegative since $\rho\ge0$, so each vanishes. Positive semidefiniteness implies $\rho|e_jb\rangle=0$ (because $\langle v|\rho|v\rangle=\|\sqrt\rho|v\rangle\|^2$). Thus $\rho$ has support only on $\operatorname{span}\{|\phi\rangle\}\otimes\mathcal H_2$ and is $|\phi\rangle\langle\phi|\otimes S$. Taking $\operatorname{Tr}_1$ gives $S=\rho_2$. Therefore $\boxed{\rho=|\phi\rangle\langle\phi|\otimes\rho_2}$.

#### Problem 1.7.1 — Step function and delta

For $x\ne0$, $\theta(x)=\int_{-\infty}^x\delta(y)\,dy$; hence $d\theta/dx=\delta(x)$ in the distributional sense. Integrate by parts:

$$
\int_a^bf(x)\delta(x)\,dx=[f(x)\theta(x)]_a^b-\int_a^b\theta(x)f'(x)\,dx.
$$

- $a<b<0$: both terms zero, result $0$.
- $a<0<b$: result $f(b)-\int_0^bf'(x)\,dx=f(0)$.
- $0<a<b$: result $f(b)-f(a)-\int_a^bf'(x)\,dx=0$.

#### Problem 1.7.2 — Equivalent definitions of $f(A)$

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

#### Problem 1.7.3 — Fourier relation implies canonical momentum properties

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

---

## Part III — Worked Homework 1

#### Question 1 — Quantum teleportation (60 marks)

##### Setup: Bell basis and operator actions

$X|0\rangle=|1\rangle$, $X|1\rangle=|0\rangle$, $Z|0\rangle=|0\rangle$, $Z|1\rangle=-|1\rangle$. With first/second qubit ordering:

$$
\begin{aligned}
|\beta_{00}\rangle&=\frac{|00\rangle+|11\rangle}{\sqrt2},&
|\beta_{01}\rangle&=\frac{|00\rangle-|11\rangle}{\sqrt2},\\
|\beta_{10}\rangle&=\frac{|10\rangle+|01\rangle}{\sqrt2},&
|\beta_{11}\rangle&=\frac{|10\rangle-|01\rangle}{\sqrt2}.
\end{aligned}
$$

These form an orthonormal basis. For $i,j\in\{0,1\}$, $X^2=Z^2=I$ and $XZ=-ZX$.

##### 1(a) — Verify Bell-state transformations

**First, apply $Z$ to either side of $|\beta_{00}\rangle$.**

$$
\begin{aligned}
(Z\otimes I)|\beta_{00}\rangle
&=\frac{Z|0\rangle|0\rangle+Z|1\rangle|1\rangle}{\sqrt2}\\
&=\frac{|00\rangle-|11\rangle}{\sqrt2}
=|\beta_{01}\rangle.
\end{aligned}
$$

$(I\otimes Z)|\beta_{00}\rangle$ gives the same vector because the two components $|00\rangle$ and $|11\rangle$ acquire the same respective signs.

**Now apply $X$.**

$$
(X\otimes I)|\beta_{00}\rangle
=\frac{|10\rangle+|01\rangle}{\sqrt2}
=|\beta_{10}\rangle
=(I\otimes X)|\beta_{00}\rangle.
$$

Thus

$$
\boxed{|\beta_{ij}\rangle=(X^i\otimes Z^j)|\beta_{00}\rangle=(X^iZ^j\otimes I)|\beta_{00}\rangle=(I\otimes Z^jX^i)|\beta_{00}\rangle.}
$$

The order $Z^jX^i$ on the last expression matters. For instance,

$$
 (X\otimes Z)|\beta_{00}\rangle=(|10\rangle-|01\rangle)/\sqrt2=|\beta_{11}\rangle.
$$

**Transform from any $|\beta_{kl}\rangle$.** Since

$$
|\beta_{kl}\rangle=(X^k\otimes Z^l)|\beta_{00}\rangle,
$$

we obtain

$$
\begin{aligned}
(X^{i-k}\otimes Z^{j-l})|\beta_{kl}\rangle
&=(X^i\otimes Z^j)|\beta_{00}\rangle\\
&=|\beta_{ij}\rangle.
\end{aligned}
$$

Exponents can be taken modulo 2, including negative exponents because $X^{-1}=X$ and $Z^{-1}=Z$.

##### 1(b) — Bell measurement of the first two qubits

**Given:** $|\alpha\rangle=a|0\rangle+b|1\rangle$, $|a|^2+|b|^2=1$, and

$$
|\Psi\rangle=|\alpha\rangle_1\otimes|\beta_{00}\rangle_{23}.
$$

Measure

$$
 O\otimes I_3,\qquad O=\sum_{i,j=0}^1(2i+j)|\beta_{ij}\rangle\langle\beta_{ij}|.
$$

**Approach:** Expand the three-qubit ket, rewrite the first two qubits in the Bell basis, then read off outcome probabilities from squared norms.

**Step 1 — Expand computationally.**

$$
|\Psi\rangle=\frac1{\sqrt2}(a|000\rangle+a|011\rangle+b|100\rangle+b|111\rangle).
$$

**Step 2 — Invert the Bell basis definitions.**

$$
\begin{aligned}
|00\rangle&=(|\beta_{00}\rangle+|\beta_{01}\rangle)/\sqrt2,\\
|11\rangle&=(|\beta_{00}\rangle-|\beta_{01}\rangle)/\sqrt2,\\
|10\rangle&=(|\beta_{10}\rangle+|\beta_{11}\rangle)/\sqrt2,\\
|01\rangle&=(|\beta_{10}\rangle-|\beta_{11}\rangle)/\sqrt2.
\end{aligned}
$$

Substitute these for the **first two** qubits in each term:

$$
\begin{aligned}
|\Psi\rangle=\frac12\big[&|\beta_{00}\rangle(a|0\rangle+b|1\rangle)
+|\beta_{01}\rangle(a|0\rangle-b|1\rangle)\\
&+|\beta_{10}\rangle(b|0\rangle+a|1\rangle)
+|\beta_{11}\rangle(b|0\rangle-a|1\rangle)\big].
\end{aligned}
$$

The ket after each Bell ket belongs to qubit 3. Recognize $Z|\alpha\rangle$, $X|\alpha\rangle$, and $ZX|\alpha\rangle$:

$$
\boxed{|\Psi\rangle=\frac12\sum_{i,j=0}^1|\beta_{ij}\rangle_{12}\otimes Z^jX^i|\alpha\rangle_3.}
$$

**Step 3 — Apply measurement projectors.** The observable's eigenvalue on $|\beta_{ij}\rangle$ is $\lambda=2i+j\in\{0,1,2,3\}$. The projector in the full space is

$$
P_{ij}=|\beta_{ij}\rangle\langle\beta_{ij}|\otimes I_3.
$$

Then

$$
 P_{ij}|\Psi\rangle=\frac12|\beta_{ij}\rangle\otimes Z^jX^i|\alpha\rangle.
$$

Since $Z^jX^i$ is unitary and the component has norm $1/2$,

$$
\boxed{p(2i+j)=\|P_{ij}|\Psi\rangle\|^2=\frac14.}
$$

**Step 4 — Normalize.** Divide the projected component by $1/2$:

$$
\boxed{|\phi(2i+j)\rangle=|\beta_{ij}\rangle_{12}\otimes Z^jX^i|\alpha\rangle_3.}
$$

| $\lambda$ | $i,j$ | Probability | Normalized conditional ket |
|---|---|---|---|
| $0$ | $0,0$ | $1/4$ | $\vert \beta_{00}\rangle\otimes\vert \alpha\rangle$ |
| $1$ | $0,1$ | $1/4$ | $\vert \beta_{01}\rangle\otimes Z\vert \alpha\rangle$ |
| $2$ | $1,0$ | $1/4$ | $\vert \beta_{10}\rangle\otimes X\vert \alpha\rangle$ |
| $3$ | $1,1$ | $1/4$ | $\vert \beta_{11}\rangle\otimes ZX\vert \alpha\rangle$ |

**Correction:** The third qubit is $Z^jX^i|\alpha\rangle$. Apply $(Z^jX^i)^{-1}=X^iZ^j$ to recover $|\alpha\rangle$.

> [!warning] Common grading mistakes
> The projector $P_{ij}$ contains an identity on qubit 3. The projected state has coefficient $1/2$; the normalized conditional state does not. The probability is $1/4$, not $1/2$.

##### 1(c) — Bell contraction, transpose, and initial $|\beta_{kl}\rangle$

**Part 1 — Prove the matrix-element identity.** We are asked to show

$$
 (\langle\beta_{00}|\otimes\langle i|)(I\otimes A\otimes I)(|j\rangle\otimes|\beta_{00}\rangle)=\frac12\langle j|A|i\rangle.
$$

Write the two Bell states as $|\beta_{00}\rangle=2^{-1/2}\sum_n|nn\rangle$ and its adjoint. Expand:

$$
\begin{aligned}
\text{LHS}
&=\frac12\sum_{m,n}
(\langle m|\langle m|\langle i|)
(I\otimes A\otimes I)(|j\rangle|n\rangle|n\rangle)\\
&=\frac12\sum_{m,n}\langle m|j\rangle\langle m|A|n\rangle\langle i|n\rangle\\
&=\frac12\sum_{m,n}\delta_{mj}A_{mn}\delta_{in}\\
&=\frac12 A_{ji}=\frac12\langle j|A|i\rangle.
\end{aligned}
$$

Because the indices are reversed, this is $\frac12 A^T$ in the $|0\rangle,|1\rangle$ basis. For $A=X^iZ^j$,

$$
 (X^iZ^j)^T=Z^jX^i,
$$

as $X^T=X$, $Z^T=Z$, and transposition reverses the order. Therefore

$$
\boxed{(\langle\beta_{00}|\otimes I)(I\otimes X^iZ^j\otimes I)(I\otimes|\beta_{00}\rangle)=\tfrac12Z^jX^i.}
$$

**Part 2 — General Bell resource $|\beta_{kl}\rangle$.** Use

$$
|\beta_{kl}\rangle=(I\otimes Z^lX^k)|\beta_{00}\rangle.
$$

For outcome $i,j$, write the projection amplitude on qubit 3 as

$$
\begin{aligned}
(\langle\beta_{ij}|\otimes I)(|\alpha\rangle\otimes|\beta_{kl}\rangle)
&=\frac12 Z^lX^kZ^jX^i|\alpha\rangle\\
&=\frac{(-1)^{kj}}2Z^{j+l}X^{i+k}|\alpha\rangle.
\end{aligned}
$$

The phase follows from moving $X^k$ past $Z^j$. Thus the **unnormalized** projected state is

$$
 \frac{(-1)^{kj}}2|\beta_{ij}\rangle\otimes Z^{j+l}X^{i+k}|\alpha\rangle,
$$

and, after normalization,

$$
\boxed{|\phi_{ij}^{(kl)}\rangle=(-1)^{kj}|\beta_{ij}\rangle\otimes Z^{j+l}X^{i+k}|\alpha\rangle,\qquad p_{ij}=\frac14.}
$$

Here the indices on Pauli powers are modulo 2. The minus sign is an overall phase, physically irrelevant but important for an *exact algebraic* equality.

##### 1(d) — Reversed and successive Bell measurements

**First task:** Measure $I\otimes O$ on $|\beta_{ij}\rangle_{12}\otimes|\alpha\rangle_3$, i.e. perform Bell measurement on qubits $2,3$. For outcome $\lambda=2m+n$,

$$
(I\otimes\langle\beta_{mn}|)(|\beta_{ij}\rangle\otimes|\alpha\rangle)
=\frac12 X^iZ^jX^mZ^n|\alpha\rangle,
$$

with the selected normalization/phase convention (global phases may be absorbed). Therefore each outcome has probability $1/4$ and the normalized state is

$$
\boxed{X^iZ^jX^mZ^n|\alpha\rangle_1\otimes|\beta_{mn}\rangle_{23}.}
$$

**Second task:** On the initial $|\alpha\rangle_1|\beta_{00}\rangle_{23}$, first measuring $O\otimes I$ with outcome $i,j$ gives

$$
|\beta_{ij}\rangle_{12}\otimes Z^jX^i|\alpha\rangle_3.
$$

Then measuring $I\otimes O$ with outcome $m,n$ gives the state of qubit 1 proportional to

$$
X^iZ^jX^mZ^nZ^jX^i|\alpha\rangle.
$$

Using $X^2=Z^2=I$ and $XZ=-ZX$, this is $\pm X^mZ^n|\alpha\rangle$. Hence, up to global phase, the final normalized state is

$$
\boxed{X^mZ^n|\alpha\rangle_1\otimes|\beta_{mn}\rangle_{23}.}
$$

Each stage has conditional outcome probability $1/4$; each ordered pair of outcomes has joint probability $1/16$.

> [!tip] Student exam strategy
> Label **123** above the three factors. Project only the two measured qubits. Keep a $1/2$ coefficient until normalization. Do not commute $X$ and $Z$ without recording a sign.

---

#### Question 2 — No-clone theorem and quantum Darwinism (40 marks)

##### 2(a) — Show the clone map is not linear

Given $\operatorname{Clone}|\phi\rangle=|\phi\rangle\otimes|\phi\rangle$ for every ket, compare scaling by $c$:

$$
\operatorname{Clone}(c|\phi\rangle)=c^2|\phi\phi\rangle,
$$

but a linear map would require

$$
c\operatorname{Clone}|\phi\rangle=c|\phi\phi\rangle.
$$

These disagree for generic $c$ (e.g. $c=2$). Hence the clone map is nonlinear and cannot be universal quantum evolution.

**Alternative superposition proof:**

$$
\begin{aligned}
\operatorname{Clone}(a|0\rangle+b|1\rangle)
&=a^2|00\rangle+ab|01\rangle+ab|10\rangle+b^2|11\rangle,\\
a\operatorname{Clone}|0\rangle+b\operatorname{Clone}|1\rangle&=a|00\rangle+b|11\rangle,
\end{aligned}
$$

which are generally different. (The problem defines the clone map on all vectors, so the scaling counterexample is legitimate.)

##### 2(b) — At most $\dim V$ perfectly cloned states

Given an isometry $A:V\to V\otimes V$ with $\langle A\alpha|A\beta\rangle=\langle\alpha|\beta\rangle$ and

$$
K=\{|\phi\rangle\ne0:A|\phi\rangle=|\phi\rangle\otimes|\phi\rangle\},
$$

show distinct members of $K$ are orthogonal.

**Step 1 — Normalization.** For $|\phi\rangle\in K$,

$$
\langle\phi|\phi\rangle=\langle A\phi|A\phi\rangle=\langle\phi|\phi\rangle^2.
$$

Since $|\phi\rangle\ne0$, its squared norm is $1$.

**Step 2 — Compare two copyable vectors.** Let $|\phi\rangle,|\psi\rangle\in K$. Then

$$
\begin{aligned}
\langle\phi|\psi\rangle&=\langle A\phi|A\psi\rangle\\
&=(\langle\phi|\otimes\langle\phi|)(|\psi\rangle\otimes|\psi\rangle)\\
&=\langle\phi|\psi\rangle^2.
\end{aligned}
$$

Let $c=\langle\phi|\psi\rangle$. Then $c^2=c$, so $c=0$ or $1$.

If $c=1$, the normalized kets are identical since $\|\phi-\psi\|^2=2-c-c^*=0$. If they are distinct, then $c=0$ and they are orthogonal.

**Step 3 — Dimension.** A $d$-dimensional space contains at most $d$ mutually orthogonal nonzero kets. Thus

$$
\boxed{|K|\le\dim V.}
$$

##### 2(c) — A qubit unitary copying the maximum number

For $\dim V=2$, part (b) gives $|K|\le2$. Choose the blank state $|\eta\rangle=|0\rangle$ and controlled-NOT

$$
\boxed{U=|0\rangle\langle0|\otimes I+|1\rangle\langle1|\otimes X.}
$$

In the $|00\rangle,|01\rangle,|10\rangle,|11\rangle$ basis,

$$
U=\begin{pmatrix}1&0&0&0\\0&1&0&0\\0&0&0&1\\0&0&1&0\end{pmatrix},\qquad U^\dagger U=I.
$$

Set $A=U(I\otimes|0\rangle)$. Then

$$
A|0\rangle=U|00\rangle=|00\rangle,\qquad A|1\rangle=U|10\rangle=|11\rangle.
$$

Both basis states are perfectly copied. But

$$
A(a|0\rangle+b|1\rangle)=a|00\rangle+b|11\rangle\ne(a|0\rangle+b|1\rangle)^{\otimes2}
$$

for generic $a,b$. Therefore the maximum $|K|=2$ is attained.

##### 2(d) — Explain the connection between measurement and copyable classical information

**Short-answer model response:**

> Arbitrary unknown quantum states cannot be cloned by linear, inner-product-preserving quantum evolution. Distinct mutually orthogonal states, however, can be distinguished and copied. A projective measurement produces a classical outcome associated with an eigenvalue, which can be recorded and copied without cloning the original arbitrary superposition. Repeating the same ideal projective measurement gives consistent outcomes for the corresponding eigenspace, whereas measurements of incompatible observables can disturb the state.

Be careful: a degenerate measurement outcome need not identify a unique pure eigenstate. It is the **classical outcome record**, not a universal copy of the pre-measurement state, that is copyable.

---

#### Exam rehearsal: one-line starting points

| Part | Immediate starting point |
|---|---|
| 1(a) | Apply $X$/$Z$ separately to each tensor factor in $\vert \beta_{00}\rangle$ |
| 1(b) | Expand $\vert \alpha\rangle\vert \beta_{00}\rangle$, then invert the Bell basis on qubits 1,2 |
| 1(c) | Write $\vert \beta_{00}\rangle=2^{-1/2}\sum_n\vert nn\rangle$ and contract Kronecker deltas |
| 1(d) | Label the qubits, use the Bell projection on qubits 2,3, track Pauli order |
| 2(a) | Test scalar linearity: $c^2$ versus $c$ |
| 2(b) | Isometry $\Rightarrow\langle\phi\vert \psi\rangle=\langle\phi\vert \psi\rangle^2$ |
| 2(c) | Use CNOT with blank $\vert 0\rangle$ |
| 2(d) | Differentiate copying a measurement's classical outcome from cloning the unknown ket |


---

## Final closed-book rehearsal

> [!todo] A full answer is not just a boxed result
> Each time you attempt a question, explicitly identify the relevant basis and operator, write the first equation, show the two or three transformations that do the actual work, and verify normalization or physical consistency.

- [ ] Pauli construction and the general $H=aI+\mathbf r\cdot\boldsymbol\sigma$ eigensystem, including a direct determinant.
- [ ] Measurement eigenvectors of $X,Y,Z$ and the normalized state after a sequence of measurements.
- [ ] Tensor-product action, trace, and basis conversions with correct operator order.
- [ ] Bell expansion for an unknown qubit and four Bell-measurement branches.
- [ ] General Bell-pair labels, transposition identity and successive measurements; check minus signs.
- [ ] Reduced density operator computed explicitly from a two-qubit ket.
- [ ] Pure reduced state implies factorization: explain the positivity step.
- [ ] Cauchy–Schwarz uncertainty proof and equality conditions.
- [ ] Delta function and Fourier normalization $1/\sqrt{2\pi\hbar}$.
- [ ] Derive $\hat p=-i\hbar\partial_x$, then $[\hat x,\hat p]=i\hbar I$.
- [ ] No-cloning bound from $c=c^2$ and the CNOT example.

> [!tip] Obsidian math
> Inline math uses `$...$`. Display math uses `$$` on a line by itself. Avoid placing display delimiters inside tables or callout titles. Use Reading view or Live Preview for rendered KaTeX.
