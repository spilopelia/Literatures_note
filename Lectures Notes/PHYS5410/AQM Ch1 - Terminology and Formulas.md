---
tags: [AQM, quantum-mechanics, chapter-1, midterm, formula-sheet]
aliases: [AQM Chapter 1 Formula Sheet]
---

# AQM Chapter 1 — Terminology and Formulas

> [!info] Scope and exam format
> **Chapter 1, §§1.1–1.7** of Tian Lan's *Advanced Quantum Mechanics*. The whiteboard indicates a 90-minute, 40-mark exam covering weeks 1–5: MCQ 12, true/false 2, terminology 11, short questions 15 (five at 3 marks). The week range does **not** imply that Chapter 1 is the whole exam.
>
> Companion notes: [[AQM Ch1 - Lecture Problems]] · [[AQM Ch1 - Homework 1]]

## 1. Postulates and quantum states (§§1.1, 1.3)

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

## 2. Linear algebra (§1.2)

### Fundamental vocabulary

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

### Recite these identities

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

### Pauli matrices — memorize exactly

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

## 3. Measurements of a qubit (§1.3)

For normalized $|\psi\rangle=a|0\rangle+b|1\rangle$:

| Measurement | $P(+1)$ | $P(-1)$ |
|---|---|---|
| $Z$ | $\vert a\vert ^2$ | $\vert b\vert ^2$ |
| $X$ | $\vert a+b\vert ^2/2$ | $\vert a-b\vert ^2/2$ |
| $Y$ | $\vert a-ib\vert ^2/2$ | $\vert a+ib\vert ^2/2$ |

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

## 4. Commutators and uncertainty (§1.4)

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

## 5. Tensor products and composite systems (§1.5)

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

## 6. Density operators and partial trace (§1.6)

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

## 7. Continuous position and momentum (§1.7)

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

## 8. Homework-specific must-recites

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

## 9. Self-test prompts

- [ ] Define Hilbert space, Hermitian, unitary, normal, projector, mixed state, eigenspace, entanglement.
- [ ] Write $X,Y,Z$ and all six $\pm1$ Pauli eigenstates.
- [ ] Explain why a determinant must vanish for an eigenvector to exist.
- [ ] State both the measurement probability and the *normalized* state update.
- [ ] Derive $\operatorname{Tr}_2$ of a Bell pair.
- [ ] State the uncertainty equality conditions, including zero-variance cases.
- [ ] Write the normalized $\langle x|p\rangle$ and Fourier transform conventions.
- [ ] Explain why arbitrary unknown pure states cannot be cloned.

See [[AQM Ch1 - Lecture Problems]] and [[AQM Ch1 - Homework 1]] for exam-length worked solutions.
