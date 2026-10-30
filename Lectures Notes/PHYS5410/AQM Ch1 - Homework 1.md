---
tags: [AQM, quantum-mechanics, chapter-1, homework-1, midterm]
aliases: [AQM Homework 1 Exam Solutions]
---

# AQM Homework 1 — Exam-length Worked Solutions

> [!info] Source and style
> Based on the uploaded official *Homework 1* (Question 1: quantum teleportation, 60 marks; Question 2: no-cloning / quantum Darwinism, 40 marks), with cross-checks against the handwritten submission. Follow the **question's exact qubit ordering**, keep global-phase conventions explicit, and normalize post-measurement states. Companion: [[AQM Ch1 - Terminology and Formulas]] · [[AQM Ch1 - Lecture Problems]].

## Question 1 — Quantum teleportation (60 marks)

### Setup: Bell basis and operator actions

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

### 1(a) — Verify Bell-state transformations

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

### 1(b) — Bell measurement of the first two qubits

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

### 1(c) — Bell contraction, transpose, and initial $|\beta_{kl}\rangle$

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

$$\begin{aligned}
(\langle\beta_{ij}|\otimes I)(|\alpha\rangle\otimes|\beta_{kl}\rangle)
&=\frac12 Z^lX^kZ^jX^i|\alpha\rangle\\
&=\frac{(-1)^{kj}}2Z^{j+l}X^{i+k}|\alpha\rangle.
\end{aligned}$$

The phase follows from moving $X^k$ past $Z^j$. Thus the **unnormalized** projected state is

$$
 \frac{(-1)^{kj}}2|\beta_{ij}\rangle\otimes Z^{j+l}X^{i+k}|\alpha\rangle,
$$

and, after normalization,

$$
\boxed{|\phi_{ij}^{(kl)}\rangle=(-1)^{kj}|\beta_{ij}\rangle\otimes Z^{j+l}X^{i+k}|\alpha\rangle,\qquad p_{ij}=\frac14.}
$$

Here the indices on Pauli powers are modulo 2. The minus sign is an overall phase, physically irrelevant but important for an *exact algebraic* equality.

### 1(d) — Reversed and successive Bell measurements

**First task:** Measure $I\otimes O$ on $|\beta_{ij}\rangle_{12}\otimes|\alpha\rangle_3$, i.e. perform Bell measurement on qubits $2,3$. For outcome $\lambda=2m+n$,

$$ (I\otimes\langle\beta_{mn}|)(|\beta_{ij}\rangle\otimes|\alpha\rangle)
=\frac12 X^iZ^jX^mZ^n|\alpha\rangle,$$

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

## Question 2 — No-clone theorem and quantum Darwinism (40 marks)

### 2(a) — Show the clone map is not linear

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

$$\begin{aligned}
\operatorname{Clone}(a|0\rangle+b|1\rangle)
&=a^2|00\rangle+ab|01\rangle+ab|10\rangle+b^2|11\rangle,\\
a\operatorname{Clone}|0\rangle+b\operatorname{Clone}|1\rangle&=a|00\rangle+b|11\rangle,
\end{aligned}$$

which are generally different. (The problem defines the clone map on all vectors, so the scaling counterexample is legitimate.)

### 2(b) — At most $\dim V$ perfectly cloned states

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

$$\begin{aligned}
\langle\phi|\psi\rangle&=\langle A\phi|A\psi\rangle\\
&=(\langle\phi|\otimes\langle\phi|)(|\psi\rangle\otimes|\psi\rangle)\\
&=\langle\phi|\psi\rangle^2.
\end{aligned}$$

Let $c=\langle\phi|\psi\rangle$. Then $c^2=c$, so $c=0$ or $1$.

If $c=1$, the normalized kets are identical since $\|\phi-\psi\|^2=2-c-c^*=0$. If they are distinct, then $c=0$ and they are orthogonal.

**Step 3 — Dimension.** A $d$-dimensional space contains at most $d$ mutually orthogonal nonzero kets. Thus

$$
\boxed{|K|\le\dim V.}
$$

### 2(c) — A qubit unitary copying the maximum number

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

### 2(d) — Explain the connection between measurement and copyable classical information

**Short-answer model response:**

> Arbitrary unknown quantum states cannot be cloned by linear, inner-product-preserving quantum evolution. Distinct mutually orthogonal states, however, can be distinguished and copied. A projective measurement produces a classical outcome associated with an eigenvalue, which can be recorded and copied without cloning the original arbitrary superposition. Repeating the same ideal projective measurement gives consistent outcomes for the corresponding eigenspace, whereas measurements of incompatible observables can disturb the state.

Be careful: a degenerate measurement outcome need not identify a unique pure eigenstate. It is the **classical outcome record**, not a universal copy of the pre-measurement state, that is copyable.

---

## Exam rehearsal: one-line starting points

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

See [[AQM Ch1 - Terminology and Formulas]] for the memorization sheet and [[AQM Ch1 - Lecture Problems]] for all chapter exercises.
