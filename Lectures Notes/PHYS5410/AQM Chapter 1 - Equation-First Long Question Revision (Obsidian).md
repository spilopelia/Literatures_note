---
title: "AQM Chapter 1 — Derivations and Long-Question Solutions"
aliases:
  - "AQM Chapter 1 Complete Revision"
tags:
  - AQM
  - quantum-mechanics
  - chapter-1
  - midterm
  - long-questions
---

# AQM Chapter 1 — Derivations and Long-Question Solutions

> [!info] Sources and scope
> Tian Lan, *Advanced Quantum Mechanics*, Chapter 1 (§§1.1–1.7), including every numbered lecture problem and all subparts of Homework 1. The midterm covers **Weeks 1–5**, so this note covers **Chapter 1 only**, not necessarily the entire examination. The updated assumption is that the paper uses **long questions**; the earlier MCQ/terminology breakdown is superseded.

> [!abstract] Navigation
> - [[#Part I — How to think through a long question|Part I — Derivations and study priorities]]
> - [[#Part II — Worked lecture problems|Part II — Lecture problems]]
> - [[#Part III — Worked Homework 1|Part III — Homework 1]]
> - [[#Final closed-book rehearsal|Closed-book rehearsal]]
>
> All equations use Obsidian's MathJax-compatible `$...$` (inline) and `$$...$$` (display) delimiters. Switch to Reading view or Live Preview to render them.


> [!important] Equation-first standard used throughout
> Do not replace an algebraic step with words such as “the sign comes from the bra” or “the state collapses.” Where a result depends on a conjugate, projection, operator order, or normalization, write the relevant equation and simplify it. A short explanation should follow the calculation, not replace it.

## How to use this note for long questions

1. **First pass — derivation map:** Learn the *starting equation* and reconstruct the key steps in Part I. Do not try to recite the entire formula catalogue.
2. **Second pass — closed-book reproduction:** For each problem in Parts II–III, cover the answer and write the solution yourself, including normalization, projectors and sign manipulations.
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
| Fourier / momentum                 | Insert $$I=\int dp\,\vert p\rangle\langle p\vert $$ and differentiate $e^{ipx/\hbar}$                                                     |
| No cloning                         | Apply inner-product preservation to two states before and after copying                                                                   |

---

## Part I — How to think through a long question

> [!important] Exam assumption and classification
> The exam is now understood to contain **long questions**. It is **not confirmed which equations the examiner will supply**. The categories below distinguish sensible *study effort*, not an official formula-sheet guarantee. Memorize only a small number of foundational definitions and matrices; practise deriving the rest. If a long identity is supplied in the question, your task is to recognize why and when to use it.

### 1. Three preparation categories

| Category | What to do | Examples |
|---|---|---|
| **Recall directly** | Know without looking; these are short foundations | Pauli matrices and actions; Hermitian/unitary; $[A,B]=AB-BA$; orthonormality and completeness; Born projector rule; tensor-product action |
| **Reconstruct the derivation** | Remember the *starting point* and 2–5 indispensable steps, not a disconnected final formula | General $2\times2$ eigensystem; uncertainty inequality; trace expectation; partial trace; $\hat p$ in $x$-space; Fourier eigenfunction; no-cloning |
| **Recognize/use when provided** | Know what the relationship means, dimensions, assumptions and where to substitute it; do not devote most revision time to verbatim recitation | General operator-function expansion, Schmidt decomposition and purification, full tensor-product basis-change proof, general commutator-of-powers identity |

> [!tip] Structure for written answers
> **Given → choose basis/representation → state the rule → perform calculation → normalize/check → conclude.** A short justification at each non-obvious transition is more valuable than repeating definitions unrelated to the question.

### 2. Pauli operators and measurement: recall the foundation; derive the rest

**Recall directly** ($Z$-eigenbasis $|0\rangle,|1\rangle$):

$$
X=\begin{pmatrix}0&1\\1&0\end{pmatrix},\quad
Y=\begin{pmatrix}0&-i\\i&0\end{pmatrix},\quad
Z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
$$

Useful actions: $X|0\rangle=|1\rangle$, $X|1\rangle=|0\rangle$, $Z|0\rangle=|0\rangle$, $Z|1\rangle=-|1\rangle$. Since $Y=iXZ$, $Y|0\rangle=i|1\rangle$, $Y|1\rangle=-i|0\rangle$. Also $X^2=Y^2=Z^2=I$ and $XZ=-ZX$.

**Recover an eigenstate rather than memorize six unrelated columns.** E.g. for $Y$,

$$
\det(Y-\lambda I)=\det\begin{pmatrix}-\lambda&-i\\i&-\lambda\end{pmatrix}=\lambda^2-1=0.
$$

For $\lambda=+1$, $(Y-I)(u,v)^T=0$ gives $iu-v=0$, so $v=iu$; normalization $|u|^2+|v|^2=1$ gives $u=1/\sqrt2$ up to phase:

$$
|y+\rangle=\frac{|0\rangle+i|1\rangle}{\sqrt2},\qquad
|y-\rangle=\frac{|0\rangle-i|1\rangle}{\sqrt2}.
$$

Similarly $|x\pm\rangle=(|0\rangle\pm|1\rangle)/\sqrt2$; $Z$ eigenstates are $|0\rangle,|1\rangle$.

**General Hermitian eigensystem: learn the path.** Any $2\times2$ Hermitian $H$ can be written

$$
H=aI+xX+yY+zZ
=\begin{pmatrix}a+z&x-iy\\x+iy&a-z\end{pmatrix}.
$$

Write $(x,y,z)=r(\sin\theta\cos\phi,\sin\theta\sin\phi,\cos\theta)$, giving

$$
H-\lambda I=\begin{pmatrix}
a-\lambda+r\cos\theta&r\sin\theta e^{-i\phi}\\
r\sin\theta e^{i\phi}&a-\lambda-r\cos\theta
\end{pmatrix}.
$$

The determinant is $(a-\lambda)^2-r^2=0$, hence $\lambda_\pm=a\pm r$. For $\lambda_+$, the first row gives

$$
(\cos\theta-1)u+\sin\theta e^{-i\phi}v=0
\ \Rightarrow\ v=e^{i\phi}\tan\frac\theta2\,u.
$$

Normalize: $u=\cos(\theta/2)$, $v=e^{i\phi}\sin(\theta/2)$. Repeat for $\lambda_-$ to find

$$
|+\rangle=\begin{pmatrix}\cos(\theta/2)\\e^{i\phi}\sin(\theta/2)\end{pmatrix},\qquad
|-\rangle=\begin{pmatrix}-e^{-i\phi}\sin(\theta/2)\\\cos(\theta/2)\end{pmatrix}.
$$

At $r=0$, $H=aI$ and every vector is an eigenvector. At $\theta=0,\pi$, obtain the eigenvectors directly from the matrix rather than divide by zero.

**From eigenvectors to measurement.** Recall the *projector* rule, including degeneracy:

$$
P(\lambda)=\langle\psi|P_\lambda|\psi\rangle,\qquad
|\psi_\lambda\rangle=\frac{P_\lambda|\psi\rangle}{\sqrt{P(\lambda)}}.
$$

**Derive the measurement amplitude; do not just quote the sign.** For $|\psi\rangle=a|0\rangle+b|1\rangle$, first take the adjoint of the $Y=+1$ eigenket:

$$
\begin{aligned}
|y+\rangle&=\frac{|0\rangle+i|1\rangle}{\sqrt2},\\
\langle y+|&=\frac{\langle0|-i\langle1|}{\sqrt2}.
\end{aligned}
$$

Then, using $\langle i|j\rangle=\delta_{ij}$,

$$
\begin{aligned}
\langle y+|\psi\rangle
&=\frac{(\langle0|-i\langle1|)(a|0\rangle+b|1\rangle)}{\sqrt2}\\
&=\frac{a\langle0|0\rangle+b\langle0|1\rangle-ia\langle1|0\rangle-ib\langle1|1\rangle}{\sqrt2}\\
&=\frac{a\langle0|0\rangle+b\langle0|1\rangle-ia\langle1|0\rangle-ib\langle1|1\rangle}{\sqrt2}\\
&=\frac{a-ib}{\sqrt2},\\
P(Y=+1)&=|\langle y+|\psi\rangle|^2=\frac{|a-ib|^2}{2}.
\end{aligned}
$$

**For successive measurements, calculate the state update rather than just state the rule.** Suppose the first result is $Y=-1$ (of nonzero probability). With $P_{y-}=|y-\rangle\langle y-|$,

$$
\begin{aligned}
|\psi_1\rangle
&=\frac{P_{y-}|\psi\rangle}{\sqrt{\langle\psi|P_{y-}|\psi\rangle}}\\
&=\frac{|y-\rangle\langle y-|\psi\rangle}{|\langle y-|\psi\rangle|}\\
&=\frac{a+ib}{|a+ib|}|y-\rangle
\sim|y-\rangle=\frac{|0\rangle-i|1\rangle}{\sqrt2}.
\end{aligned}
$$

Here $\sim$ denotes equality up to global phase. For the second measurement, use the **new state** $|\psi_1\rangle$, not $|\psi\rangle$:

$$
\begin{aligned}
P(X=+1\mid Y=-1)
&=|\langle x+|y-\rangle|^2\\
&=\left|\frac{(\langle0|+\langle1|)(|0\rangle-i|1\rangle)}2\right|^2\\
&=\left|\frac{1-i}{2}\right|^2=\frac12,\\
P(X=-1\mid Y=-1)
&=\left|\frac{(\langle0|-\langle1|)(|0\rangle-i|1\rangle)}2\right|^2\\
&=\left|\frac{1+i}{2}\right|^2=\frac12.
\end{aligned}
$$

### 3. Commutator and uncertainty: reconstruct from one inequality

**Recall:** $[A,B]=AB-BA$ and $[A,BC]=[A,B]C+B[A,C]$. The product rule is obtained by adding/subtracting $BAC$:

$$
ABC-BCA=(ABC-BAC)+(BAC-BCA).
$$

Set $\delta A=A-\langle A\rangle I$ and $|u\rangle=\delta A|\psi\rangle$, $|v\rangle=\delta B|\psi\rangle$. Then $\|u\|=\Delta A$, $\|v\|=\Delta B$. Cauchy–Schwarz and $|z|\ge|\operatorname{Im}z|$ yield

$$
(\Delta A)^2(\Delta B)^2\ge|\langle u|v\rangle|^2
\ge\left|\frac{\langle u|v\rangle-\langle v|u\rangle}{2i}\right|^2
=\frac14|\langle[A,B]\rangle|^2.
$$

So $\Delta A\Delta B\ge|\langle[A,B]\rangle|/2$. Equality (for both nonzero variances) requires $\delta A|\psi\rangle=i\xi\delta B|\psi\rangle$, real $\xi$. The Jacobi identity follows by expanding the three nested commutators and cancelling terms; see Problem 1.4.2.

### 4. Composite systems: identify the factor before calculating

**Recall** $(A\otimes B)(|u\rangle\otimes|v\rangle)=A|u\rangle\otimes B|v\rangle$ and $\dim(V\otimes W)=\dim V\dim W$. An operator on the first qubit is $A\otimes I$, not just $A$ when acting on the full space.

For the ordered basis $|00\rangle,|01\rangle,|10\rangle,|11\rangle$,

$$
(a|0\rangle+b|1\rangle)(c|0\rangle+d|1\rangle)
=ac|00\rangle+ad|01\rangle+bc|10\rangle+bd|11\rangle.
$$

To prove operators on different subsystems commute, act in either order on $|u\rangle|v\rangle$; both yield $A|u\rangle B|v\rangle$. For tensor-product matrix elements, apply the factors and use factorization of the inner product:

$$
\langle i\alpha|A\otimes B|j\beta\rangle
=\langle i|A|j\rangle\langle\alpha|B|\beta\rangle.
$$

### 5. Trace and density matrices: understand *why* two expectations coincide

**Recall:** for an orthonormal basis, $\operatorname{Tr}M=\sum_i\langle i|M|i\rangle$ and $\operatorname{Tr}(|a\rangle\langle b|)=\langle b|a\rangle$. The latter follows by inserting $I=\sum_i|i\rangle\langle i|$.

For a **pure state** $\rho=|\psi\rangle\langle\psi|$,

$$
\begin{aligned}
\operatorname{Tr}(\rho A)
&=\sum_i\langle i|\psi\rangle\langle\psi|A|i\rangle\\
&=\langle\psi|A\left(\sum_i|i\rangle\langle i|\right)|\psi\rangle\\
&=\langle\psi|A|\psi\rangle.
\end{aligned}
$$

So $\langle\psi|A|\psi\rangle$ and $\operatorname{Tr}(\rho A)$ are **the same expectation**, not two observables. Use the ket form for a given pure ket; use the trace form for a supplied density matrix or a **mixture** $\rho=\sum_k p_k|\psi_k\rangle\langle\psi_k|$.

**Worked two-level example:** $|\psi\rangle=(\sqrt3|0\rangle+|1\rangle)/2$, $Z=\operatorname{diag}(1,-1)$:

$$
\langle\psi|Z|\psi\rangle=\frac34-\frac14=\frac12,
\qquad
\rho=\frac14\begin{pmatrix}3&\sqrt3\\\sqrt3&1\end{pmatrix},
$$

$$
\operatorname{Tr}(\rho Z)=\operatorname{Tr}\frac14
\begin{pmatrix}3&-\sqrt3\\\sqrt3&-1\end{pmatrix}=\frac12.
$$

By contrast, an equal *mixture* of $|0\rangle$ and $|1\rangle$ has $\rho=I/2$; it is **not** the superposition $(|0\rangle+|1\rangle)/\sqrt2$. Their $X$ expectations are $0$ and $1$ respectively.

**Partial trace: learn one term, then apply linearity.** For two qubits,

$$
\operatorname{Tr}_2\left(|ab\rangle\langle cd|\right)
=|a\rangle\langle c|\underbrace{\langle d|b\rangle}_{\delta_{db}}
=\delta_{bd}|a\rangle\langle c|.
$$

The subscript **2 means discard subsystem 2**, retaining an operator on subsystem 1. This is *not* an ordinary trace: $4\times4\to2\times2$, not $4\times4\to$ scalar.

For $|\beta_{00}\rangle=(|00\rangle+|11\rangle)/\sqrt2$:

$$
\begin{aligned}
\rho&=\tfrac12\big(|00\rangle\langle00|+|00\rangle\langle11|
+|11\rangle\langle00|+|11\rangle\langle11|\big),\\
\operatorname{Tr}_2\rho&=\tfrac12\big(|0\rangle\langle0|+0+0+|1\rangle\langle1|\big)=I/2.
\end{aligned}
$$

A pure *total* state can thus have a mixed *reduced* state. Use the reduced state for observables local to system 1:

$$
\operatorname{Tr}[\rho(A\otimes I)]=\operatorname{Tr}[(\operatorname{Tr}_2\rho)A].
$$

For a matrix with entries $\rho_{ab,cd}$, the quick rule is $(\rho_1)_{ac}=\sum_b\rho_{ab,cb}$. The density-operator criteria $\rho^\dagger=\rho$, $\rho\ge0$, $\operatorname{Tr}\rho=1$ are worth recalling; use $\operatorname{Tr}\rho^2=1$ to test purity (finite-dimensional normalized states).

### 6. Position and momentum: one connected derivation rather than three memorized formulas

> [!important] What to learn
> **Do not try to memorize three isolated equations.** Learn two directions: (i) commutator + zero-momentum reference $\Rightarrow$ differential operator $\Rightarrow$ plane wave; (ii) given Fourier overlap $\Rightarrow$ differential operator $\Rightarrow$ commutator. The problem statement may supply a starting relation; identify *which direction* is being requested.

**Foundation:** begin with the continuous eigenbasis and completeness:

$$
\hat x|x\rangle=x|x\rangle,\qquad
\langle x|y\rangle=\delta(x-y),\qquad
I=\int dy\,|y\rangle\langle y|.
$$

For a function of the position operator, $f(\hat x)|y\rangle=f(y)|y\rangle$. Insert completeness instead of assuming its action on a wavefunction:

$$
\begin{aligned}
\langle x|f(\hat x)|\psi\rangle
&=\int dy\,\langle x|f(\hat x)|y\rangle\langle y|\psi\rangle\\
&=\int dy\,f(y)\delta(x-y)\psi(y)\\
&=f(x)\psi(x).
\end{aligned}
$$

This is why $f(\hat x)$ becomes multiplication by $f(x)$ **in the position representation**; it is not an identity between an operator and a number.

**Direction A — From $[\hat x,\hat p]=i\hbar I$ to a derivative.** First recall the commutator product rule $[A,BC]=[A,B]C+B[A,C]$. For example,

$$
\begin{aligned}
[\hat p,\hat x^2]&=[\hat p,\hat x]\hat x+\hat x[\hat p,\hat x]=-2i\hbar\hat x,\\
[\hat p,\hat x^3]&=[\hat p,\hat x^2]\hat x+\hat x^2[\hat p,\hat x]=-3i\hbar\hat x^2.
\end{aligned}
$$

Thus $[\hat p,\hat x^n]=-i\hbar n\hat x^{n-1}$. Applying this term by term to a suitable operator function $f(\hat x)=\sum_n c_n\hat x^n$ yields

$$
[\hat p,f(\hat x)]=-i\hbar f'(\hat x).
$$

Introduce the formal constant-wavefunction state $|\phi_0\rangle=\int dx\,|x\rangle$, so $\langle x|\phi_0\rangle=1$, with zero-momentum convention $\hat p|\phi_0\rangle=0$. A general wavefunction can formally be written $|\psi\rangle=\psi(\hat x)|\phi_0\rangle$. Then

$$
\begin{aligned}
\langle x|\hat p|\psi\rangle
&=\langle x|\hat p\psi(\hat x)|\phi_0\rangle\\
&=\langle x|\big(\psi(\hat x)\hat p-i\hbar\psi'(\hat x)\big)|\phi_0\rangle\\
&=-i\hbar\psi'(x)\underbrace{\langle x|\phi_0\rangle}_{1}\\
&=-i\hbar\frac{d\psi(x)}{dx}.
\end{aligned}
$$

**Direction A continued — Momentum eigenfunctions.** Take the momentum eigenvalue equation $\hat p|p\rangle=p|p\rangle$ and project onto $\langle x|$:

$$
-i\hbar\frac{d}{dx}\langle x|p\rangle=p\langle x|p\rangle
\quad\Rightarrow\quad
\frac{d\phi_p}{dx}=\frac{ip}{\hbar}\phi_p
\quad\Rightarrow\quad
\phi_p(x)=Ce^{ipx/\hbar}.
$$

The generalized normalization comes from inserting momentum completeness between two position states:

$$
\begin{aligned}
\delta(x-y)&=\langle x|y\rangle=\int dp\,\langle x|p\rangle\langle p|y\rangle\\
&=|C|^2\int dp\,e^{ip(x-y)/\hbar}\\
&=|C|^2(2\pi\hbar)\delta(x-y).
\end{aligned}
$$

Hence $|C|^2=(2\pi\hbar)^{-1}$. Choose $C>0$ as the phase convention:

$$
\langle x|p\rangle=\frac{e^{ipx/\hbar}}{\sqrt{2\pi\hbar}}.
$$

**Direction B — Given the Fourier overlap.** Insert momentum completeness:

$$
\begin{aligned}
\langle x|\hat p|\psi\rangle
&=\int dp\,p\langle x|p\rangle\langle p|\psi\rangle\\
&=-i\hbar\partial_x\int dp\,\langle x|p\rangle\langle p|\psi\rangle\\
&=-i\hbar\psi'(x).
\end{aligned}
$$

Now evaluate the commutator on *arbitrary* $\psi(x)$, remembering operator order:

$$
\begin{aligned}
\langle x|[\hat x,\hat p]|\psi\rangle
&=x(-i\hbar\psi')-(-i\hbar\partial_x)(x\psi)\\
&=-i\hbar x\psi'+i\hbar(\psi+x\psi')\\
&=i\hbar\psi(x).
\end{aligned}
$$

Thus $[\hat x,\hat p]=i\hbar I$. Finally, since $\langle x|\phi_0\rangle=1$, $\langle x|\hat p|\phi_0\rangle=-i\hbar\partial_x1=0$. This is the flow of Lecture Problem **1.7.3**.

**Delta and Fourier only when required:** $\theta'(x)=\delta(x)$, $\int dx\,f(x)\delta(x-a)=f(a)$, and $\delta(s)=\int dk\,e^{iks}/(2\pi)$ (distributionally). The Fourier pair follows by inserting $I=\int dp\,|p\rangle\langle p|$; no need to memorize it separately if you know $\langle x|p\rangle$.

### 7. Homework motifs: know the construction, not just the final state

**Bell basis** (short enough to recall, but it can be rebuilt):

$$
\begin{aligned}
|\beta_{00}\rangle&=(|00\rangle+|11\rangle)/\sqrt2,\\
|\beta_{01}\rangle&=(|00\rangle-|11\rangle)/\sqrt2,\\
|\beta_{10}\rangle&=(|10\rangle+|01\rangle)/\sqrt2,\\
|\beta_{11}\rangle&=(|10\rangle-|01\rangle)/\sqrt2.
\end{aligned}
$$

**Teleportation is a basis rewrite, then a projection.** Expand $|\alpha\rangle_1|\beta_{00}\rangle_{23}$ in the computational basis, use the inverse Bell-basis identities on qubits $1,2$, group terms, and obtain

$$
|\alpha\rangle_1|\beta_{00}\rangle_{23}
=\frac12\sum_{ij}|\beta_{ij}\rangle_{12}\otimes Z^jX^i|\alpha\rangle_3.
$$

Each outcome has probability $1/4$; the normalized third-qubit state is $Z^jX^i|\alpha\rangle$. The correction is $X^iZ^j$. For generalized Bell resources, remember $XZ=-ZX$ before rearranging powers.

**No-cloning is inner-product preservation, not a memorized slogan.** If an isometry copies $|\phi\rangle$ and $|\psi\rangle$,

$$
\langle\phi|\psi\rangle=\langle\phi\phi|\psi\psi\rangle
=(\langle\phi|\psi\rangle)^2,
$$

so distinct normalized states must be orthogonal. At most $\dim V$ such states exist. CNOT with a blank $|0\rangle$ achieves two for a qubit.

### 8. Study checklist — can you start these without notes?

- [ ] Starting from $Y$, derive $|y\pm\rangle$ and normalize them.
- [ ] Starting from a general Hermitian $2\times2$ matrix, derive $a\pm r$ and the normalized spinors.
- [ ] Starting from a measured outcome $\lambda$, compute the projector, probability and post-measurement state.
- [ ] Starting from Cauchy–Schwarz, derive the uncertainty bound and equality condition.
- [ ] Starting from the definition of trace, prove $\operatorname{Tr}(|\psi\rangle\langle\psi|A)=\langle\psi|A|\psi\rangle$.
- [ ] Starting from $|ab\rangle\langle cd|$, derive the $\operatorname{Tr}_2$ rule; trace out one qubit of a Bell pair.
- [ ] Starting from $[\hat x,\hat p]$ and $|\phi_0\rangle$, derive the momentum differential operator and plane wave.
- [ ] Starting from $\langle x|p\rangle$, derive $[\hat x,\hat p]$ using the product rule.
- [ ] Starting from three product kets, reconstruct a Bell measurement and all four conditional states.
- [ ] Starting from isometry, derive the no-cloning bound.

---

## Part II — Worked lecture problems

### Problem 1.2.1 — Vector-space identities

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

### Problem 1.2.2 — Operators satisfy vector-space axioms

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

### Problem 1.2.3 — Operator inner product

**Start:** To prove $(A,B)=\operatorname{Tr}(A^\dagger B)$ is an inner product, verify linearity, conjugate symmetry, and positivity.

$$
\begin{aligned}
(A,cB+dC)&=\operatorname{Tr}(A^\dagger(cB+dC))=c(A,B)+d(A,C),\\
(A,B)^*&=\operatorname{Tr}[(A^\dagger B)^\dagger]=\operatorname{Tr}(B^\dagger A)=(B,A),\\
(A,A)&=\sum_i\langle i|A^\dagger A|i\rangle=\sum_i\|A|i\rangle\|^2\ge0.
\end{aligned}
$$

Equality in the last line means $A|i\rangle=0$ for every basis ket, hence $A=0$. This establishes the inner product in finite dimensions.

### Problem 1.2.4 — Six-part Pauli problem

#### (1) Determine $Z$

**Start:** Work in the eigenbasis, possible because $Z=Z^\dagger$.

$$
Z=\operatorname{diag}(\lambda_1,\lambda_2),\qquad Z^2=I\Rightarrow\lambda_i=\pm1.
$$

$\operatorname{Tr}Z=0$ gives $\lambda_1+\lambda_2=0$. Order the basis so

$$
\boxed{Z=\begin{pmatrix}1&0\\0&-1\end{pmatrix}.}
$$

#### (2) Determine $X$

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

#### (3) Construct $Y=iXZ$

$$
Y=i\begin{pmatrix}0&-1\\1&0\end{pmatrix}=\boxed{\begin{pmatrix}0&-i\\i&0\end{pmatrix}}.
$$

$$
Y^\dagger=-iZX=iXZ=Y,\qquad Y^2=-XZXZ=X^2Z^2=I,\qquad\operatorname{Tr}Y=0.
$$

#### (4) Orthogonal basis of operator space

Since all are Hermitian and traceless except $I$,

$$
\operatorname{Tr}(X)=\operatorname{Tr}(Y)=\operatorname{Tr}(Z)=0,
$$

and $XY=iZ$, $YZ=iX$, $ZX=iY$, cross inner products vanish. Also

$$
\operatorname{Tr}(I^2)=\operatorname{Tr}(X^2)=\operatorname{Tr}(Y^2)=\operatorname{Tr}(Z^2)=2.
$$

Thus $\operatorname{Tr}(\sigma_\mu^\dagger\sigma_\nu)=2\delta_{\mu\nu}$. Four nonzero orthogonal operators form a basis because $\dim\operatorname{Hom}(V,V)=2^2=4$. With $\frac12\operatorname{Tr}(A^\dagger B)$ they are orthonormal.

#### (5) Pauli commutators

$$
[X,Y]=iZ-(-iZ)=2iZ,\quad [Y,Z]=2iX,\quad[Z,X]=2iY.
$$

Reversed pairs have opposite signs; identical pairs commute. Hence

$$
\boxed{[\sigma_i,\sigma_j]=2i\sum_k\epsilon_{ijk}\sigma_k.}
$$

#### (6) General $2\times2$ Hermitian eigensystem

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

### Problem 1.2.5 — Tensor-product bases and matrices

#### (1) Basis independence

Let $|e'_a\rangle=\sum_i S_{ia}|e_i\rangle$ and $|f'_b\rangle=\sum_j T_{jb}|f_j\rangle$ with invertible $S,T$. Bilinearity yields

$$
|e'_a\rangle\otimes|f'_b\rangle=\sum_{ij}S_{ia}T_{jb}|e_i\rangle\otimes|f_j\rangle.
$$

This is the invertible product basis change $S\otimes T$, with inverse $S^{-1}\otimes T^{-1}$. Thus the construction is basis-independent up to a canonical isomorphism.

#### (2) Tensor product of operator spaces

Using dual basis functionals (or ordinary bras for orthonormal bases), rank-one maps $|e'_a\rangle\langle e_i|$ and $|f'_b\rangle\langle f_j|$ form bases of the local operator spaces. Their product is

$$
 (|e'_a\rangle\langle e_i|)\otimes(|f'_b\rangle\langle f_j|)=|e'_af'_b\rangle\langle e_if_j|.
$$

These span all linear maps between product spaces, giving the finite-dimensional isomorphism

$$
\operatorname{Hom}(V\otimes W,V'\otimes W')\simeq\operatorname{Hom}(V,V')\otimes\operatorname{Hom}(W,W').
$$

#### (3) Matrix elements

$$
\boxed{\langle e_i f_\alpha|A\otimes B|e_j f_\beta\rangle=\langle e_i|A|e_j\rangle\langle f_\alpha|B|f_\beta\rangle=A_{ij}B_{\alpha\beta}.}
$$

### Problem 1.3.1 — Measurements on $|\psi\rangle=a|0\rangle+b|1\rangle$

Assume $|a|^2+|b|^2=1$.

#### (1) Outcomes and probabilities

Eigenstates: $|x\pm\rangle=(|0\rangle\pm|1\rangle)/\sqrt2$ and $|y\pm\rangle=(|0\rangle\pm i|1\rangle)/\sqrt2$. Born's rule gives

| Observable | $P(+1)$ | $P(-1)$ |
|---|---|---|
| $Z$ | $\vert a\vert^2$ | $\vert b\vert^2$ |
| $X$ | $\vert a+b\vert^2/2$ | $\vert a-b\vert^2/2$ |
| $Y$ | $\vert a-ib\vert^2/2$ | $\vert a+ib\vert^2/2$ |

For the $Y=+1$ entry, **take the adjoint and expand the inner product**, rather than memorizing the sign:

$$
\begin{aligned}
\langle y+|&=\frac{\langle0|-i\langle1|}{\sqrt2},\\
\langle y+|\psi\rangle
&=\frac{(\langle0|-i\langle1|)(a|0\rangle+b|1\rangle)}{\sqrt2}\\
&=\frac{a\langle0|0\rangle+b\langle0|1\rangle-ia\langle1|0\rangle-ib\langle1|1\rangle}{\sqrt2}\\
&=\frac{a-ib}{\sqrt2},\\
P(Y=+1)&=\frac{|a-ib|^2}{2}.
\end{aligned}
$$

Likewise $\langle y-|=(\langle0|+i\langle1|)/\sqrt2$, so $P(Y=-1)=|a+ib|^2/2$.

#### (2) Expectations and polar coordinates

$$
\begin{aligned}
\langle Z\rangle&=|a|^2-|b|^2,\\
\langle X\rangle&=a^*b+b^*a,\\
\langle Y\rangle&=-ia^*b+ib^*a.
\end{aligned}
$$

These expectations follow from multiplying the Pauli matrices into the column $(a,b)^T$; explicitly, for $Y$,

$$
\begin{aligned}
\langle Y\rangle
&=(a^*,b^*)\begin{pmatrix}0&-i\\i&0\end{pmatrix}\begin{pmatrix}a\\b\end{pmatrix}\\
&=(a^*,b^*)\begin{pmatrix}-ib\\ia\end{pmatrix}=-ia^*b+ib^*a.
\end{aligned}
$$

The Bloch-vector length is

$$
\begin{aligned}
r^2&=(|a|^2-|b|^2)^2+(a^*b+b^*a)^2+[-i(a^*b-b^*a)]^2\\
&=(|a|^2-|b|^2)^2+4|a^*b|^2\\
&=(|a|^2+|b|^2)^2=1.
\end{aligned}
$$

From $\langle Z\rangle=\cos\theta$ and $\langle X\rangle+i\langle Y\rangle=\sin\theta e^{i\phi}$, choose global phase so $a\ge0$:

$$
\boxed{|\psi\rangle=\cos\frac\theta2|0\rangle+e^{i\phi}\sin\frac\theta2|1\rangle.}
$$

#### (3) Repeated $Z$ measurement

Recall that the post-measurement state is $P_+|\psi\rangle/\sqrt{\langle\psi|P_+|\psi\rangle}$, not the original ket. The first outcome $Z=+1$ has projector $P_+=|0\rangle\langle0|$. The normalized conditional state is

$$
\begin{aligned}
|\psi_1\rangle
&=\frac{P_+|\psi\rangle}{\sqrt{\langle\psi|P_+|\psi\rangle}}
=\frac{|0\rangle\langle0|(a|0\rangle+b|1\rangle)}{|a|}\\
&=\frac{a}{|a|}|0\rangle\sim|0\rangle.
\end{aligned}
$$

The next $Z$ measurement therefore yields

$$
P(Z=+1\mid Z=+1)=|\langle0|0\rangle|^2=1,\qquad
P(Z=-1\mid Z=+1)=|\langle1|0\rangle|^2=0.
$$

#### (4) $Y=-1$ followed by $X$

For the first result, $P_{y-}=|y-\rangle\langle y-|$, where $|y-\rangle=(|0\rangle-i|1\rangle)/\sqrt2$. Using $\langle y-|=(\langle0|+i\langle1|)/\sqrt2$,

$$
\begin{aligned}
|\psi_1\rangle
&=\frac{|y-\rangle\langle y-|\psi\rangle}{|\langle y-|\psi\rangle|}\\
&=\frac{a+ib}{|a+ib|}|y-\rangle\sim |y-\rangle.
\end{aligned}
$$

The first outcome is possible only when $a+ib\ne0$. Its phase cancels from every probability. For the subsequent $X$ measurement, the normalized eigenbras are $\langle x\pm|=(\langle0|\pm\langle1|)/\sqrt2$. Therefore,

$$
\begin{aligned}
P(X=+1\mid Y=-1)
&=\left|\frac{(\langle0|+\langle1|)(|0\rangle-i|1\rangle)}2\right|^2
=\left|\frac{1-i}2\right|^2=\frac12,\\
P(X=-1\mid Y=-1)
&=\left|\frac{(\langle0|-\langle1|)(|0\rangle-i|1\rangle)}2\right|^2
=\left|\frac{1+i}2\right|^2=\frac12.
\end{aligned}
$$

Both statements are conditional on the first outcome having nonzero probability.

### Problem 1.4.1 — Equality in uncertainty relation

Set $|u\rangle=(A-\langle A\rangle)|\psi\rangle$, $|v\rangle=(B-\langle B\rangle)|\psi\rangle$. The proof uses

$$
\|u\|^2\|v\|^2\ge|\langle u|v\rangle|^2\ge[\operatorname{Im}\langle u|v\rangle]^2.
$$

Equality requires (i) $u,v$ linearly dependent, and (ii) the inner product purely imaginary. For nonzero deviations,

$$
\boxed{(A-\langle A\rangle)|\psi\rangle=i\xi(B-\langle B\rangle)|\psi\rangle,\quad\xi\in\mathbb R.}
$$

If either deviation vector is zero, equality also holds. Equivalently, with the sign convention $\eta=-\xi$, $(A+i\eta B)|\psi\rangle=\langle A+i\eta B\rangle|\psi\rangle$.

### Problem 1.4.2 — Commutator identities

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

### Problem 1.6.1 — Recover pure-state measurement rules from density operators

**Approach:** Start with $\rho=|\psi\rangle\langle\psi|$ and reuse $\operatorname{Tr}(|u\rangle\langle v|A)=\langle v|A|u\rangle$ (proved by inserting completeness). For normalized $|\psi\rangle$:

**Probability**

$$
P(\lambda)=\operatorname{Tr}(\rho P_\lambda)
=\operatorname{Tr}(|\psi\rangle\langle\psi|P_\lambda)
=\langle\psi|P_\lambda|\psi\rangle.
$$

**Conditional state** (only if $P(\lambda)>0$)

$$
\begin{aligned}
\rho_\lambda
&=\frac{P_\lambda\rho P_\lambda}{\operatorname{Tr}(\rho P_\lambda)}\\
&=\frac{P_\lambda|\psi\rangle\langle\psi|P_\lambda}{\langle\psi|P_\lambda|\psi\rangle}
=|\psi_\lambda\rangle\langle\psi_\lambda|,
\end{aligned}
$$

where $|\psi_\lambda\rangle=P_\lambda|\psi\rangle/\sqrt{\langle\psi|P_\lambda|\psi\rangle}$ and $P_\lambda^\dagger=P_\lambda$.

**Expectation**

$$
\operatorname{Tr}(\rho O)=\operatorname{Tr}(|\psi\rangle\langle\psi|O)=\langle\psi|O|\psi\rangle.
$$

So the trace expressions are the **same physical measurement rules** for pure states; trace notation also covers mixtures.

### Problem 1.6.2 — Pure reduced state iff factorization

**Question:** Prove $\operatorname{Tr}_2\rho=|\phi\rangle\langle\phi|$ iff $\rho=|\phi\rangle\langle\phi|\otimes\rho_2$ for an arbitrary bipartite density operator.

> [!note] Following the official-solution method
> The official solution uses **Schmidt decomposition** for a pure total state and **purification** for a general mixed total state. These are the relevant tools to *recognize if supplied*. The following is an equally valid direct positivity proof, requiring less extra machinery; the official route is summarized afterward.

**($\Leftarrow$) Product implies pure reduced state.** If $\rho=|\phi\rangle\langle\phi|\otimes\rho_2$, then by $\operatorname{Tr}_2(A\otimes B)=A\operatorname{Tr}B$,

$$
\operatorname{Tr}_2\rho=|\phi\rangle\langle\phi|\operatorname{Tr}\rho_2=|\phi\rangle\langle\phi|.
$$

**($\Rightarrow$) Pure reduced state implies product.** Suppose $\rho_1=|\phi\rangle\langle\phi|$. Complete $|\phi\rangle$ to an orthonormal basis $\{|\phi\rangle,|e_j\rangle\}$ of system 1. Since $\langle e_j|\phi\rangle=0$,

$$
0=\langle e_j|\rho_1|e_j\rangle
=\sum_b\langle e_jb|\rho|e_jb\rangle.
$$

Each summand is nonnegative ($\rho\ge0$), so each is zero. Positivity implies $\langle v|\rho|v\rangle=\|\sqrt\rho|v\rangle\|^2=0\Rightarrow\rho|v\rangle=0$. Thus $\rho|e_jb\rangle=0$ for all $j,b$; by Hermiticity the corresponding rows also vanish. Therefore the support of $\rho$ lies entirely in $\operatorname{span}\{|\phi\rangle\}\otimes\mathcal H_2$, forcing

$$
\rho=|\phi\rangle\langle\phi|\otimes S.
$$

Trace out subsystem 1 to identify $S=\operatorname{Tr}_1\rho=\rho_2$. Hence the claimed factorization.

**Official solution's alternative:** For a pure total state use $|\Psi\rangle=\sum_j\sqrt{p_j}|\phi_j\rangle|\chi_j\rangle$ (Schmidt decomposition). Then $\rho_1=\sum_jp_j|\phi_j\rangle\langle\phi_j|$ has rank one iff exactly one $p_j=1$, so $|\Psi\rangle$ factorizes. For mixed $\rho$, purify to $|\Phi\rangle_{123}$ with $\operatorname{Tr}_3|\Phi\rangle\langle\Phi|=\rho_{12}$; the reduced state on 1 is still rank one, so $|\Phi\rangle=|\phi\rangle_1|\chi\rangle_{23}$. Tracing out 3 yields $\rho_{12}=|\phi\rangle\langle\phi|\otimes\rho_2$.

### Problem 1.7.1 — Step function and delta

For $x\ne0$, $\theta(x)=\int_{-\infty}^x\delta(y)\,dy$; hence $d\theta/dx=\delta(x)$ in the distributional sense. Integrate by parts:

$$
\int_a^bf(x)\delta(x)\,dx=[f(x)\theta(x)]_a^b-\int_a^b\theta(x)f'(x)\,dx.
$$

For $a<b<0$, $\theta(x)=0$ throughout the interval, so

$$
\int_a^bf(x)\delta(x)\,dx=0-0=0.
$$

For $a<0<b$, $\theta(a)=0$ and $\theta(b)=1$, hence

$$
\begin{aligned}
\int_a^bf(x)\delta(x)\,dx
&=f(b)-\int_0^bf'(x)\,dx\\
&=f(b)-[f(b)-f(0)]=f(0).
\end{aligned}
$$

For $0<a<b$, $\theta(x)=1$ throughout, and

$$
\begin{aligned}
\int_a^bf(x)\delta(x)\,dx
&=f(b)-f(a)-\int_a^bf'(x)\,dx\\
&=f(b)-f(a)-[f(b)-f(a)]=0.
\end{aligned}
$$

### Problem 1.7.2 — Equivalent definitions of $f(A)$

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

### Problem 1.7.3 — Fourier relation implies canonical momentum properties

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

### Question 1 — Quantum teleportation (60 marks)

#### Setup: Bell basis and operator actions

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

#### 1(a) — Verify Bell-state transformations

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

#### 1(b) — Bell measurement of the first two qubits

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

#### 1(c) — Bell contraction, transpose, and initial $|\beta_{kl}\rangle$

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

#### 1(d) — Reversed and successive Bell measurements

**First task:** Measure $I\otimes O$ on $|\beta_{ij}\rangle_{12}\otimes|\alpha\rangle_3$, i.e. perform Bell measurement on qubits $2,3$. For outcome $\lambda=2m+n$,

$$
(I\otimes\langle\beta_{mn}|)(|\beta_{ij}\rangle\otimes|\alpha\rangle)
=\frac12 X^iZ^jX^mZ^n|\alpha\rangle,
$$

up to an outcome-dependent global phase; the physical conditional state is unaffected. Its norm is $1/2$ since the Pauli factors are unitary. Therefore each outcome has probability $1/4$ and the normalized state is

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

### Question 2 — No-clone theorem and quantum Darwinism (40 marks)

#### 2(a) — Show the clone map is not linear

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

#### 2(b) — At most $\dim V$ perfectly cloned states

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

#### 2(c) — A qubit unitary copying the maximum number

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

#### 2(d) — Explain the connection between measurement and copyable classical information

**Short-answer model response:**

> Arbitrary unknown quantum states cannot be cloned by linear, inner-product-preserving quantum evolution. Distinct mutually orthogonal states, however, can be distinguished and copied. A projective measurement produces a classical outcome associated with an eigenvalue, which can be recorded and copied without cloning the original arbitrary superposition. Repeating the same ideal projective measurement gives consistent outcomes for the corresponding eigenspace, whereas measurements of incompatible observables can disturb the state.

Be careful: a degenerate measurement outcome need not identify a unique pure eigenstate. It is the **classical outcome record**, not a universal copy of the pre-measurement state, that is copyable.

---

### Exam rehearsal: one-line starting points

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
