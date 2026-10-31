---
title: "AQM Chapter 2 — Homework and Mock Exam Extension"
tags: [AQM, chapter-2, chapter-4-1, midterm, long-questions]
---

# AQM Chapter 2 — Homework and Mock Exam Extension

> [!important] Exam boundary
> **Tested syllabus: Chapters 1–3 and Chapter 4 through §4.1 only.** HW3 Q1 and Q2 rely on angular-momentum rotations developed in **§4.2**, so their original angular-momentum content is **outside the stated scope**. Nevertheless, HW3 Q2(b)'s *method*—a time-dependent unitary change of picture—appears in §2.2 and has a close **§4.1 translation analogue**. This note places **original exam-scope mock questions first** and moves the optional HW3 angular-momentum material into a clearly labelled appendix with complete student-style solutions. Original mocks are not past examination questions.
>
> Sources: Tian Lan, *Advanced Quantum Mechanics*, §§2.1–2.3 and 4.1; *Homework 3*, Questions 1–2; accompanying handwritten HW3 solutions. The original numbered Chapter 2 lecture problems are included with full calculations in Part II below. [[AQM Chapter 2 - Long Question Revision]] remains a separate conceptual companion.

## Exam-scope map

| Material | Techniques worth learning | In scope? |
|---|---|---|
| HW3 Q1, angular-momentum rotation identity | Hadamard expansion; nested commutators | **Method yes; original rotation/§4.2 physics no** |
| HW3 Q2(a), classical rotating field | Vector rotations and changing frames | **No (§4.2)** |
| HW3 Q2(b)(i), rotating quantum frame | Product rule for $U'=W U$; transformed Hamiltonian | **Method yes; particular $J_z$ example no** |
| HW3 Q2(b)(ii), quantum/classical angular momentum | Heisenberg expectation, unitary conjugation | **Method yes; angular momentum application no** |
| HW4 Q1–2 | $SU(2)$; angular-momentum addition | **No (§§4.2–4.3)** |
| Mock 1: two-level dynamics | State evolution; relative phases; probabilities | **Yes (§2.1)** |
| Mock 2: moving potential / translation | Change of picture; momentum-generated translation | **Yes (§§2.2, 4.1)** |
| Mock 3: Heisenberg motion | Commutators and conservation | **Yes (§§2.2, 4.1)** |
| Mock 4: propagator and composition | Completeness, Gaussian phase, path integral | **Yes (§2.3)** |

---

# Part I — Original long-question mocks within §§2.1–2.3 and 4.1

Each problem is an **original practice problem**, not a prediction of the exact midterm. The original lecture Problems 2.1.1, 2.1.2, 2.2.1 and 2.3.1 are worked fully in Part II. The mocks emphasize **using** their methods in physical systems. Attempt each question without the solution first.

## Worked §2.2 example — three pictures with a noncommuting interaction

> [!important] How to use this example
> **First study:** why the matrix exponential and interaction-picture equation work. **In an exam:** use the shorter worked solution below, showing the actual matrix arithmetic, not assuming a special identity. The three picture calculations use the same system, but the mathematical object that evolves is different.
>
> This is an **original practice question**, not a past exam paper. The exercise goes beyond mere definitions; it is intended to make the lecture's §2.2 transformations concrete.

### Question (40 marks)

A two-level system is governed by

$$
H=H_0+V,\qquad H_0=\frac{\hbar\omega}{2}Z,\quad V=\frac{\hbar g}{2}X,
$$

where $\omega,g$ are nonzero real numbers and initially $|\psi(0)\rangle=|0\rangle$.

**(a) (15 marks)** Find the evolution operator by expanding its matrix exponential, then find $P(Z=-1;t)$ in the Schrödinger picture.

**(b) (8 marks)** Calculate the same probability in the Heisenberg picture by transforming its measurement projector.

**(c) (12 marks)** Derive the interaction-picture equation and explicitly calculate $V_I(t)$; do not assume $[H_0,V]=0$.

**(d) (5 marks)** Find the interaction-picture state from the transformed Schrödinger state, and check the measurement probability. Also state how the expectation $\langle Z\rangle_t$ is calculated in each picture.

### Worked solution — what to write in the exam

#### (a) Schrödinger picture

**1. Write $H$ and the evolution equation.** From $Z=\left(\begin{smallmatrix}1&0\\0&-1\end{smallmatrix}\right)$ and $X=\left(\begin{smallmatrix}0&1\\1&0\end{smallmatrix}\right)$,

$$
H=\frac{\hbar}{2}M,\qquad M=\begin{pmatrix}\omega&g\\g&-\omega\end{pmatrix},\qquad U(t)=e^{-iMt/2}.
$$

**2. Calculate the exponential, rather than quoting a formula.** Multiply $M$ by itself:

$$
\begin{aligned}
M^2&=\begin{pmatrix}\omega&g\\g&-\omega\end{pmatrix}
\begin{pmatrix}\omega&g\\g&-\omega\end{pmatrix}\\
&=\begin{pmatrix}\omega^2+g^2&\omega g-g\omega\\g\omega-\omega g&g^2+\omega^2\end{pmatrix}\\
&=(\omega^2+g^2)I=\Omega^2 I,\qquad \Omega=\sqrt{\omega^2+g^2}.
\end{aligned}
$$

Consequently $M^3=\Omega^2M$, $M^4=\Omega^4I$. Start with the **definition** of the exponential:

$$
\begin{aligned}
U(t)&=I-\frac{it}{2}M+\frac{(-it/2)^2}{2!}M^2+\frac{(-it/2)^3}{3!}M^3+\cdots\\
&=I\left[1-\frac{(\Omega t/2)^2}{2!}+\frac{(\Omega t/2)^4}{4!}-\cdots\right]\\
&\quad-i\frac{M}{\Omega}\left[\frac{\Omega t}{2}-\frac{(\Omega t/2)^3}{3!}+\cdots\right]\\
&=I\cos\frac{\Omega t}{2}-i\frac{M}{\Omega}\sin\frac{\Omega t}{2}.
\end{aligned}
$$

The last line uses the familiar Taylor series for $\cos$ and $\sin$, **not an additional memorized matrix identity**. Write $c=\cos(\Omega t/2)$ and $s=\sin(\Omega t/2)$. Substituting $M$:

$$
\begin{aligned}
U(t)&=c\begin{pmatrix}1&0\\0&1\end{pmatrix}-\frac{is}{\Omega}\begin{pmatrix}\omega&g\\g&-\omega\end{pmatrix}\\
&=\boxed{\begin{pmatrix}c-i\omega s/\Omega&-ig s/\Omega\\-ig s/\Omega&c+i\omega s/\Omega\end{pmatrix}}.
\end{aligned}
$$

**3. Evolve the initial ket and measure.** Since $|0\rangle=(1,0)^T$,

$$
|\psi_S(t)\rangle=U(t)|0\rangle=\begin{pmatrix}c-i\omega s/\Omega\\-ig s/\Omega\end{pmatrix}.
$$

The outcome $Z=-1$ corresponds to $|1\rangle=(0,1)^T$, so

$$
\boxed{P_S(Z=-1;t)=|\langle1|\psi_S(t)\rangle|^2=\frac{g^2}{\Omega^2}\sin^2\frac{\Omega t}{2}}.
$$

#### (b) Heisenberg picture

**1. Leave the state fixed, transform the projector.** The projector for $Z=-1$ is

$$
P_-=|1\rangle\langle1|=\begin{pmatrix}0&0\\0&1\end{pmatrix},\qquad P_{-,H}(t)=U^\dagger P_- U.
$$

**2. Calculate its expectation value in the original state.** We need only $U|0\rangle$ from (a), not the full product $U^\dagger P_-U$:

$$
\begin{aligned}
P_-U|0\rangle&=\begin{pmatrix}0&0\\0&1\end{pmatrix}\begin{pmatrix}c-i\omega s/\Omega\\-ig s/\Omega\end{pmatrix}=\begin{pmatrix}0\\-ig s/\Omega\end{pmatrix},\\
\langle0|U^\dagger&=\left(U|0\rangle\right)^\dagger=\begin{pmatrix}c+i\omega s/\Omega&i g s/\Omega\end{pmatrix},\\
P_H(Z=-1;t)&=\langle0|U^\dagger P_-U|0\rangle\\
&=\begin{pmatrix}c+i\omega s/\Omega&i g s/\Omega\end{pmatrix}\begin{pmatrix}0\\-ig s/\Omega\end{pmatrix}\\
&=\boxed{\frac{g^2}{\Omega^2}s^2}.
\end{aligned}
$$

This is a genuine Heisenberg-picture measurement: $|0\rangle$ is fixed while $P_-$ evolves. **If a question instead asks for the Heisenberg equation of motion**, start from $\dot O_H=(i/\hbar)[H_H,O_H]$ and calculate the commutators. Do not switch methods without explaining why.

#### (c) Interaction picture

**1. Identify the freely evolving part.**

$$
U_0(t)=e^{-iH_0t/\hbar}=\begin{pmatrix}e^{-i\omega t/2}&0\\0&e^{i\omega t/2}\end{pmatrix},\qquad |\psi_I\rangle=U_0^\dagger|\psi_S\rangle.
$$

**2. Derive the equation if requested.** Differentiate the *product* and substitute $i\hbar|\dot\psi_S\rangle=(H_0+V)|\psi_S\rangle$:

$$
\begin{aligned}
i\hbar\frac{d}{dt}|\psi_I\rangle
&=i\hbar\dot U_0^\dagger|\psi_S\rangle+U_0^\dagger i\hbar|\dot\psi_S\rangle\\
&=-H_0U_0^\dagger|\psi_S\rangle+U_0^\dagger(H_0+V)|\psi_S\rangle\\
&=U_0^\dagger V|\psi_S\rangle\\
&=(U_0^\dagger VU_0)|\psi_I\rangle.
\end{aligned}
$$

The free terms cancel because $U_0^\dagger$ commutes with $H_0$. Thus $i\hbar|\dot\psi_I\rangle=V_I|\psi_I\rangle$ with $V_I=U_0^\dagger VU_0$. For a **calculation question** where this evolution equation has already been established in lectures, state it directly; the derivative above is for a proof question or first-time understanding.

**3. Multiply the matrices to find $V_I(t)$.**

$$
\begin{aligned}
V_I(t)&=\frac{\hbar g}{2}\begin{pmatrix}e^{i\omega t/2}&0\\0&e^{-i\omega t/2}\end{pmatrix}
\begin{pmatrix}0&1\\1&0\end{pmatrix}
\begin{pmatrix}e^{-i\omega t/2}&0\\0&e^{i\omega t/2}\end{pmatrix}\\
&=\boxed{\frac{\hbar g}{2}\begin{pmatrix}0&e^{i\omega t}\\e^{-i\omega t}&0\end{pmatrix}}.
\end{aligned}
$$

Note $V_I(t)$ depends on time even though $V$ does not. **Do not** infer $U_I=e^{-iVt/\hbar}$: here $[H_0,V]\ne0$.

#### (d) Measurement in the interaction picture

**1. Transform state and measured observable consistently.** Using (a),

$$
\begin{aligned}
|\psi_I(t)\rangle&=U_0^\dagger U|0\rangle\\
&=\begin{pmatrix}e^{i\omega t/2}(c-i\omega s/\Omega)\\e^{-i\omega t/2}(-ig s/\Omega)\end{pmatrix}.
\end{aligned}
$$

Also $Z_I=U_0^\dagger ZU_0=Z$ because the matrices are diagonal (verify by multiplying if asked).

**2. Measure $Z=-1$.**

$$
\begin{aligned}
P_I(Z=-1;t)&=|\langle1|\psi_I(t)\rangle|^2\\
&=\left|e^{-i\omega t/2}\left(-\frac{ig}{\Omega}s\right)\right|^2\\
&=\boxed{\frac{g^2}{\Omega^2}\sin^2\frac{\Omega t}{2}}.
\end{aligned}
$$

**3. If the question asks for the expectation value instead of one probability**, calculate the operator expectation, not an individual projector. In Schrödinger picture:

$$
\begin{aligned}
\langle Z\rangle_t
&=\langle\psi_S(t)|Z|\psi_S(t)\rangle\\
&=\begin{pmatrix}c+i\omega s/\Omega & igs/\Omega\end{pmatrix}
\begin{pmatrix}1&0\\0&-1\end{pmatrix}
\begin{pmatrix}c-i\omega s/\Omega\\-igs/\Omega\end{pmatrix}\\
&=\left(c+i\frac{\omega s}{\Omega}\right)
\left(c-i\frac{\omega s}{\Omega}\right)
-\left(i\frac{gs}{\Omega}\right)\left(-i\frac{gs}{\Omega}\right)\\
&=c^2+\frac{\omega^2-g^2}{\Omega^2}s^2
=1-\frac{2g^2}{\Omega^2}\sin^2\frac{\Omega t}{2}.
\end{aligned}
$$

In Heisenberg picture use the fixed initial ket and transformed observable:

$$
\begin{aligned}
\langle Z\rangle_t
&=\langle0|Z_H(t)|0\rangle
=\langle0|U^\dagger ZU|0\rangle\\
&=\begin{pmatrix}c+i\omega s/\Omega & igs/\Omega\end{pmatrix}
\begin{pmatrix}1&0\\0&-1\end{pmatrix}
\begin{pmatrix}c-i\omega s/\Omega\\-igs/\Omega\end{pmatrix}\\
&=1-2g^2s^2/\Omega^2.
\end{aligned}
$$

In interaction picture, first evaluate $Z_I=U_0^\dagger ZU_0=Z$, then:

$$
\begin{aligned}
\langle Z\rangle_t
&=\langle\psi_I(t)|Z_I|\psi_I(t)\rangle\\
&=|e^{i\omega t/2}(c-i\omega s/\Omega)|^2
-|e^{-i\omega t/2}(-igs/\Omega)|^2\\
&=1-2g^2s^2/\Omega^2.
\end{aligned}
$$

The alternative relation $\langle Z\rangle=(+1)P_++(-1)P_-=1-2P_-$ is derived by probability weighting the eigenvalues $+1,-1$; it is *specific to this observable*, not a formula to memorize for arbitrary $O$.

The three answers agree because their states and operators are transformed consistently. We have **not independently solved** the time-dependent interaction-picture equation in (d); we obtained its solution from the exact Schrödinger evolution through the definition of the interaction picture. If the examiner specifically demands an independent solution of $i\hbar|\dot\psi_I\rangle=V_I|\psi_I\rangle$, that requires solving the coupled coefficient equations instead.

### Exam-use version — steps to reproduce

| Picture | Necessary steps for this type of question |
|---|---|
| Schrödinger | Write $H$ as a matrix → compute $U$ by familiar eigenvectors or the **demonstrated** exponential series → apply $U$ to $|\psi_0\rangle$ → use Born's rule |
| Heisenberg | Identify the requested observable/projector → calculate $U^\dagger O U$ (or its expectation directly) in the fixed initial state → simplify |
| Interaction | Identify $H_0$ → compute $U_0$ → calculate $V_I=U_0^\dagger VU_0$ → solve the transformed equation if required → transform the measured observable → calculate probability |

> [!note] One-time proof versus exam working
> Understand the product-rule derivation of the interaction-picture equation and the power-series definition of the exponential once. In subsequent questions, **show why the method applies** (for example, calculate $M^2$) and include enough intermediate algebra to reconstruct the result. Never quote a special matrix identity, solution ansatz, or differential-equation form that has not already been established.


### If the Hamiltonian matrix is not traceless

Do **not** apply the above $M^2=\Omega^2I$ simplification blindly. For a general *Hermitian* $2\times2$ matrix $M$, the student-friendly method that always works is:

1. Find its eigenvalues from $\det(M-\lambda I)=0$.
2. Find and normalize the corresponding eigenvectors from $(M-\lambda I)|v\rangle=0$.
3. Expand the **given initial state** in that orthonormal eigenbasis, $|\psi(0)\rangle=\sum_j c_j|v_j\rangle$, with $c_j=\langle v_j|\psi(0)\rangle$.
4. Evolve each energy component using the eigenvalue equation: $|\psi(t)\rangle=\sum_j c_je^{-iE_jt/\hbar}|v_j\rangle$. Calculate only the amplitude actually requested.

This avoids constructing the whole matrix exponential when unnecessary. If you do choose to remove its identity part, *show the decomposition* $M=\frac{\operatorname{Tr}M}{2}I+N$ first. The scalar identity contributes only a common phase; it does not affect probabilities. Both approaches begin from established Chapter 1 methods, not a special formula to memorize.

---

## Mock 1 — Time evolution and sequential measurement (40 marks; §2.1)

A qubit has the time-independent Hamiltonian $H=\frac{\hbar\Omega}{2}Z$, with $Z|0\rangle=|0\rangle$, $Z|1\rangle=-|1\rangle$, and initial state $|\psi(0)\rangle=(|0\rangle+|1\rangle)/\sqrt2$.

**(a) (10 marks)** Derive $U(t)$ and $|\psi(t)\rangle$ without assuming that the state is an energy eigenstate.

**(b) (10 marks)** Find $P(X=+1;t)$ and $P(X=-1;t)$ using the eigenstates of $X$.

**(c) (10 marks)** Evaluate $\langle X\rangle_t$ and $\langle Y\rangle_t$ directly from $|\psi(t)\rangle$, and explain why the state changes physically even though the energy probabilities stay constant.

**(d) (10 marks)** Suppose $X$ is measured at $t=\pi/(2\Omega)$ and the result is $+1$. Write the normalized post-measurement state and find the probability of subsequently measuring $Z=+1$ immediately afterwards.

### Worked solution — Mock 1

**(a)** Recall $U(t)=e^{-iHt/\hbar}$ for constant $H$. Since $H|0\rangle=(\hbar\Omega/2)|0\rangle$ and $H|1\rangle=-(\hbar\Omega/2)|1\rangle$,

$$
\begin{aligned}
U(t)|0\rangle&=e^{-i\Omega t/2}|0\rangle,\\
U(t)|1\rangle&=e^{i\Omega t/2}|1\rangle.
\end{aligned}
$$

By linearity,

$$
\boxed{|\psi(t)\rangle=\frac1{\sqrt2}\big(e^{-i\Omega t/2}|0\rangle+e^{i\Omega t/2}|1\rangle\big).}
$$

The equivalent expression $e^{-i\Omega t/2}(|0\rangle+e^{i\Omega t}|1\rangle)/\sqrt2$ makes the evolving **relative phase** apparent.

**(b)** Recall $|x\pm\rangle=(|0\rangle\pm|1\rangle)/\sqrt2$. The measurement amplitude is

$$
\begin{aligned}
\langle x+|\psi(t)\rangle
&=\frac12(e^{-i\Omega t/2}+e^{i\Omega t/2})=\cos\frac{\Omega t}{2},\\
\langle x-|\psi(t)\rangle
&=\frac12(e^{-i\Omega t/2}-e^{i\Omega t/2})=-i\sin\frac{\Omega t}{2}.
\end{aligned}
$$

Therefore

$$
\boxed{P(X=+1;t)=\cos^2\frac{\Omega t}{2},\qquad P(X=-1;t)=\sin^2\frac{\Omega t}{2}.}
$$

Check: the probabilities add to 1.

**(c)** Use $X|0\rangle=|1\rangle$, $X|1\rangle=|0\rangle$, $Y|0\rangle=i|1\rangle$, $Y|1\rangle=-i|0\rangle$. Writing $a=e^{-i\Omega t/2}/\sqrt2$, $b=e^{i\Omega t/2}/\sqrt2$,

$$
\begin{aligned}
\langle X\rangle_t&=a^*b+b^*a=\frac12(e^{i\Omega t}+e^{-i\Omega t})=\boxed{\cos\Omega t},\\
\langle Y\rangle_t&=-i a^*b+i b^*a=\boxed{\sin\Omega t}.
\end{aligned}
$$

Each energy eigenstate still occurs with probability $1/2$; the *relative phase* between these energy components changes the outcomes of measuring $X$ or $Y$.

**(d)** The outcome $X=+1$ projects onto $P_+=|x+\rangle\langle x+|$. At $t=\pi/(2\Omega)$, $\Omega t/2=\pi/4$. From (b),

$$
\langle x+|\psi(t)\rangle=\cos(\pi/4)=1/\sqrt2,
\qquad P(X=+1)=|1/\sqrt2|^2=1/2.
$$

Because $P_+|\psi(t)\rangle=|x+\rangle\langle x+|\psi(t)\rangle=|x+\rangle/\sqrt2$, the normalized post-measurement state is

$$
\begin{aligned}
|\psi_+\rangle&=\frac{P_+|\psi(t)\rangle}{\sqrt{\langle\psi(t)|P_+|\psi(t)\rangle}}\\
&=e^{i\alpha}|x+\rangle
\ \sim\frac{|0\rangle+|1\rangle}{\sqrt2},
\end{aligned}
$$

where $e^{i\alpha}$ is an irrelevant global phase. At $\Omega t=\pi/2$, this branch has nonzero probability $1/2$. The immediate next outcome $Z=+1$ has

$$
\boxed{P(Z=+1\mid X=+1)=|\langle0|x+\rangle|^2=\frac12.}
$$

---

## Mock 2 — HW3-style *translation* change of picture (40 marks; §§2.2, 4.1)

A particle moves in a one-dimensional potential translating at constant speed $v$:

$$
H(t)=\frac{\hat p^2}{2m}+V(\hat x-vt).
$$

The evolution operator satisfies $i\hbar\dot U=H(t)U$ and $U(0)=I$. Assume $V$ is a sufficiently regular real function of position. Define

$$
W(t)=e^{iv t\hat p/\hbar},\qquad U'(t)=W(t)U(t).
$$

**(a) (10 marks)** Use $[\hat x,\hat p]=i\hbar$ and the Hadamard formula to calculate $W\hat xW^\dagger$ and $W\hat pW^\dagger$. Deduce $WV(\hat x-vt)W^\dagger$.

**(b) (15 marks)** Differentiate $U'=WU$ and derive its Hamiltonian $H'$. Show $H'$ is time-independent.

**(c) (10 marks)** Find $U'(t)$ and express $U(t)$ as a product of exponentials. Explain why the two exponentials should not generally be merged.

**(d) (5 marks)** If $V=0$, show directly that the result reduces to free-particle evolution.

### Worked solution — Mock 2

**(a)** Put $A=ivt\hat p/\hbar$. Recall $e^A B e^{-A}=B+[A,B]+\cdots$. For $B=\hat x$,

$$
[A,\hat x]=\frac{ivt}{\hbar}[\hat p,\hat x]=\frac{ivt}{\hbar}(-i\hbar)=vt I.
$$

As $[A,vt I]=0$, higher commutators vanish:

$$
\boxed{W\hat xW^\dagger=\hat x+vt,\qquad W\hat pW^\dagger=\hat p.}
$$

Consequently, using the power-series/spectral functional calculus for $V$,

$$
WV(\hat x-vt)W^\dagger
=V(W\hat xW^\dagger-vt)=\boxed{V(\hat x)}.
$$

**(b)** First apply the product rule, exactly as in the handwritten HW3 solution:

$$
\begin{aligned}
i\hbar\dot U'
&=i\hbar\dot WU+i\hbar W\dot U\\
&=i\hbar\dot WW^\dagger U'+WHW^\dagger U'.
\end{aligned}
$$

Differentiate the exponential using its series (the generator $\hat p$ is constant):

$$
\begin{aligned}
\dot W
&=\frac{d}{dt}\sum_{n=0}^{\infty}\frac{(ivt\hat p/\hbar)^n}{n!}\\
&=\frac{iv\hat p}{\hbar}\sum_{n=1}^{\infty}\frac{(ivt\hat p/\hbar)^{n-1}}{(n-1)!}\\
&=\frac{iv\hat p}{\hbar}W.
\end{aligned}
$$

Thus,

$$
i\hbar\dot WW^\dagger=-v\hat p.
$$

Also, from (a),

$$
WHW^\dagger=\frac{\hat p^2}{2m}+V(\hat x).
$$

Therefore

$$
\boxed{i\hbar\dot U'=H'U',\qquad H'=\frac{\hat p^2}{2m}+V(\hat x)-v\hat p.}
$$

The result has no explicit time dependence.

**(c)** Because $H'$ is constant and $U'(0)=I$,

$$
\boxed{U'(t)=e^{-iH't/\hbar},\qquad U(t)=e^{-ivt\hat p/\hbar}e^{-iH't/\hbar}.}
$$

Do not combine the exponentials for general $V$: since $[\hat p,V(\hat x)]\ne0$, $\hat p$ generally does not commute with $H'$.

**(d)** If $V=0$, then $H'=\hat p^2/(2m)-v\hat p$, whose two terms commute. Therefore

$$
\begin{aligned}
U(t)&=e^{-ivt\hat p/\hbar}e^{-i[\hat p^2/(2m)-v\hat p]t/\hbar}\\
&=e^{-i\hat p^2t/(2m\hbar)},
\end{aligned}
$$

as required.

**Why this is the correct §4.1 analogue:** HW3 changes to a co-rotating frame generated by $J_z$; here we change to a co-translating frame generated by $p$. The derivation method is identical but only §4.1 symmetry is used.

---

## Mock 3 — Heisenberg equations and symmetry (40 marks; §§2.2, 4.1)

For a particle in one dimension, let

$$
H=\frac{\hat p^2}{2m}+F\hat x,
$$

where $F$ is a real constant and $[\hat x,\hat p]=i\hbar$.

**(a) (15 marks)** Find the Heisenberg equations for $\hat x_H(t)$ and $\hat p_H(t)$, showing the commutators used.

**(b) (10 marks)** Solve the operator equations with $\hat x_H(0)=\hat x$ and $\hat p_H(0)=\hat p$.

**(c) (10 marks)** Find $\langle\hat x\rangle_t$ and $\langle\hat p\rangle_t$ for an arbitrary normalized initial state, expressed in terms of initial expectation values.

**(d) (5 marks)** Is momentum conserved? What changes when $F=0$, and how does this connect to the spatial-translation generator in §4.1?

### Worked solution — Mock 3

**(a)** Recall $\dot O_H=(i/\hbar)[H_H,O_H]$ for no explicit operator time dependence. For constant $H$, $H_H=H$; equivalently compute the commutators before unitary conjugation:

$$
\begin{aligned}
[H,\hat x]&=\frac1{2m}[\hat p^2,\hat x]+F[\hat x,\hat x]\\
&=\frac1{2m}\{\hat p[\hat p,\hat x]+[\hat p,\hat x]\hat p\}\\
&=-\frac{i\hbar}{m}\hat p,\\
[H,\hat p]&=F[\hat x,\hat p]=i\hbar F.
\end{aligned}
$$

Thus

$$
\boxed{\frac{d\hat x_H}{dt}=\frac{\hat p_H}{m},\qquad \frac{d\hat p_H}{dt}=-F I.}
$$

**(b)** Integrate momentum first, using $\dot p_H=-FI$ and $p_H(0)=p$:

$$
\begin{aligned}
p_H(t)-p_H(0)&=\int_0^t(-F I)\,ds=-Ft I,\\
p_H(t)&=p-Ft I.
\end{aligned}
$$

Then substitute into $\dot{\hat x}_H=\hat p_H/m$:

$$
\begin{aligned}
\hat x_H(t)&=\hat x+\frac1m\int_0^t(\hat p-FsI)\,ds\\
&=\boxed{\hat x+\frac{\hat p}{m}t-\frac{F}{2m}t^2I}.
\end{aligned}
$$

**(c)** Take expectation values in the fixed initial state $|\psi(0)\rangle$:

$$
\boxed{\begin{aligned}
\langle\hat p\rangle_t&=\langle\hat p\rangle_0-Ft,\\
\langle\hat x\rangle_t&=\langle\hat x\rangle_0+\frac{\langle\hat p\rangle_0}{m}t-\frac{Ft^2}{2m}.
\end{aligned}}
$$

**(d)** For $F\ne0$, $[H,\hat p]=i\hbar F\ne0$, so momentum is not conserved. If $F=0$, then $[H,\hat p]=0$ and $\langle\hat p\rangle_t$ is constant. In §4.1 the unitary translation is $T(a)=e^{-ia\hat p/\hbar}$; invariance under translations means $T(a)^\dagger HT(a)=H$, equivalent to $[H,\hat p]=0$ for a continuous translation group.

---

## Mock 4 — Propagator with a constant energy shift (40 marks; §2.3)

Let $H=\hat p^2/(2m)+V_0 I$ for constant real $V_0$, and let $T>0$.

**(a) (10 marks)** Starting from momentum completeness, find $K(x_f,T;x_i,0)=\langle x_f|e^{-iHT/\hbar}|x_i\rangle$ in terms of the free-particle propagator.

**(b) (10 marks)** Use the classical Lagrangian $L=m\dot x^2/2-V_0$ to calculate the action of the straight classical trajectory connecting the endpoints. Verify its appearance in the phase of $K$.

**(c) (15 marks)** Insert a complete position basis at time $t$, with $0<t<T$, to state and explain the composition identity for $K$. Explain which position is integrated and why.

**(d) (5 marks)** Does adding $V_0I$ change probabilities for measurements on an evolved, normalized state? Justify the answer using the evolution operator.

### Worked solution — Mock 4

**(a)** Since $V_0I$ commutes with $\hat p^2/(2m)$,

$$
\begin{aligned}
K&=e^{-iV_0T/\hbar}\langle x_f|e^{-i\hat p^2T/(2m\hbar)}|x_i\rangle\\
&=\frac{e^{-iV_0T/\hbar}}{2\pi\hbar}\int_{-\infty}^{\infty}dp\,
\exp\left[\frac i\hbar\left(p(x_f-x_i)-\frac{p^2T}{2m}\right)\right].
\end{aligned}
$$

To avoid skipping the Gaussian calculation, set $\Delta x=x_f-x_i$ and write

$$
 p\Delta x-\frac{p^2T}{2m}
=-\frac{T}{2m}\left(p-\frac{m\Delta x}{T}\right)^2+\frac{m(\Delta x)^2}{2T}.
$$

Now substitute $q=p-m\Delta x/T$. The remaining integral is an oscillatory Gaussian. Using the Gaussian integral

$$
\int_{-\infty}^{\infty}e^{-aq^2}\,dq=\sqrt{\frac{\pi}{a}},
$$

with $a=iT/(2m\hbar)$ (understood with the usual convergence prescription), we obtain

$$
\begin{aligned}
\int_{-\infty}^{\infty}dq\,e^{-iTq^2/(2m\hbar)}
&=\sqrt{\frac{\pi}{iT/(2m\hbar)}}
=\sqrt{\frac{2\pi m\hbar}{iT}},\\
\frac{1}{2\pi\hbar}\sqrt{\frac{2\pi m\hbar}{iT}}
&=\sqrt{\frac{m}{2\pi i\hbar T}}.
\end{aligned}
$$

The Gaussian with complex $a$ is defined by adding an arbitrarily small positive damping term and taking its limit; this technical justification need not be repeated in each exam calculation.

Hence the full kernel is

$$
\boxed{K=\sqrt{\frac{m}{2\pi i\hbar T}}\exp\left[\frac i\hbar\left(\frac{m(x_f-x_i)^2}{2T}-V_0T\right)\right].}
$$

**(b)** The classical straight path is $x(t)=x_i+(x_f-x_i)t/T$, with constant $\dot x=(x_f-x_i)/T$. Then

$$
\begin{aligned}
S_{\rm cl}&=\int_0^T \left(\frac12m\dot x^2-V_0\right)dt\\
&=\boxed{\frac{m(x_f-x_i)^2}{2T}-V_0T}.
\end{aligned}
$$

This is exactly the exponent's action in part (a).

**(c)** Begin with the **evolution composition law**:

$$
U(T,0)=U(T,t)U(t,0).
$$

Insert position completeness between the two factors:

$$
\begin{aligned}
K(x_f,T;x_i,0)
&=\langle x_f|U(T,t)\left(\int dx\,|x\rangle\langle x|\right)U(t,0)|x_i\rangle\\
&=\boxed{\int_{-\infty}^{\infty}dx\,K(x_f,T;x,t)K(x,t;x_i,0)}.
\end{aligned}
$$

The intermediate position $x$ is **not measured or specified**, so its quantum amplitudes must be integrated before taking any modulus square. Endpoints $x_i,x_f$ remain fixed.

**(d)** For any initial normalized state $|\psi_0\rangle$,

$$
|\psi(T)\rangle=e^{-iV_0T/\hbar}e^{-i\hat p^2T/(2m\hbar)}|\psi_0\rangle.
$$

The extra factor is a global phase. It cancels from $\langle\psi(T)|M|\psi(T)\rangle$ and all measurement probabilities; thus a constant potential offset is unobservable in these dynamics.

---

# Part II — Original Chapter 2 lecture problems, with worked derivations

> [!important] Source and status
> These are **the numbered exercises in the supplied lecture-solution PDF**, not original mocks. The worked calculations below are expanded from that source, making omitted algebra explicit. In Problem 2.1.2 we choose **real ordering coefficients**, as the supplied handwritten lecture solution does; the exam answer should state that simplifying assumption when used. The lecture's order-four comparisons use units $\hbar=1$, whereas we keep $\hbar$ visible below.

## Lecture Problem 2.1.1 — Operator with explicit time dependence

**Question.** An observable $A_t$ depends explicitly on $t$ even before quantum evolution. If

$$
A_H(t)=U^\dagger(t)A_tU(t),\qquad i\hbar\dot U=H(t)U,
$$

derive its equation of motion.

**Step 1 — Differentiate all three factors.**

$$
\frac{dA_H}{dt}
=\dot U^\dagger A_tU+U^\dagger\frac{\partial A_t}{\partial t}U+U^\dagger A_t\dot U.
$$

**Step 2 — Obtain both derivatives of $U$.** The Schrödinger equation gives

$$
\dot U=-\frac{i}{\hbar}HU.
$$

Take the Hermitian adjoint and use $H^\dagger=H$:

$$
\dot U^\dagger=(\dot U)^\dagger=\frac{i}{\hbar}U^\dagger H.
$$

**Step 3 — Substitute and group the commutator.**

$$
\begin{aligned}
\frac{dA_H}{dt}
&=\frac{i}{\hbar}U^\dagger HA_tU
+U^\dagger\frac{\partial A_t}{\partial t}U
-\frac{i}{\hbar}U^\dagger A_tHU\\
&=\frac{i}{\hbar}U^\dagger(HA_t-A_tH)U
+U^\dagger\frac{\partial A_t}{\partial t}U.
\end{aligned}
$$

Insert $UU^\dagger=I$ between operators to establish
$U^\dagger[H,A_t]U=[U^\dagger HU,U^\dagger A_tU]$.
Defining $H_H=U^\dagger HU$, we obtain

$$
\boxed{\frac{dA_H}{dt}=\frac{i}{\hbar}[H_H,A_H]
+U^\dagger\frac{\partial A_t}{\partial t}U.}
$$

**Check:** when $\partial A_t/\partial t=0$, the last term vanishes and we recover the usual Heisenberg equation. A time-dependent **Hamiltonian** does not invalidate this equation; it changes $U(t)$ and $H_H(t)$.

## Lecture Problem 2.1.2 — Canonical quantization and operator ordering

**Question.** A classical Hamiltonian contains monomials $x^ap^b$. Quantization must make the operator Hermitian even though $[x,p]=i\hbar$. Show why Hermitian operator ordering is unique below degree four, differs at most by a constant at degree four, and has physically relevant ambiguity above degree four.

**Preparation — Two commutator calculations used repeatedly:**

$$
\begin{aligned}
[x,p^2]&=[x,p]p+p[x,p]=2i\hbar p,\\
[x^2,p]&=x[x,p]+[x,p]x=2i\hbar x.
\end{aligned}
$$

These follow by expanding $[A,BC]=[A,B]C+B[A,C]$. We will not assume a generic ordering theorem.

**(a) Degrees less than four.** Pure powers of $x$ or $p$ have no ordering issue. For $xp$, Hermiticity relates coefficients of $xp$ and $px$; with real coefficients and correct classical limit, the choice is

$$
\frac12(xp+px).
$$

For $x^2p$, a general real Hermitian ordering can be written

$$
H_a=a x^2p+(1-2a)xpx+a px^2.
$$

Subtract $xpx$ and show the dependence on $a$ cancels:

$$
\begin{aligned}
H_a-xpx
&=a(x^2p-2xpx+px^2)\\
&=a\{x(xp-px)+(px-xp)x\}\\
&=a\{x[x,p]+[p,x]x\}\\
&=a\{i\hbar x-i\hbar x\}=0.
\end{aligned}
$$

Thus $H_a=xpx$. The $xp^2$ case follows by directly comparing $pxp$ with its symmetrized variants:

$$
\begin{aligned}
xp^2-2pxp+p^2x
&=(xp-px)p+p(px-xp)\\
&=[x,p]p+p[p,x]=i\hbar p-i\hbar p=0.
\end{aligned}
$$

**(b) Degree four.** For $x^2p^2$, compare four Hermitian possibilities:

$$
\begin{aligned}
H_1&=\tfrac12(x^2p^2+p^2x^2),\\
H_2&=\tfrac12(xpxp+pxpx),\\
H_3&=xp^2x,\qquad H_4=px^2p.
\end{aligned}
$$

We need to calculate their differences, not merely state that they are constants.

First,

$$
\begin{aligned}
H_1-H_3
&=\tfrac12(x^2p^2+p^2x^2-2xp^2x)\\
&=\tfrac12\{x(xp^2-p^2x)+(p^2x-xp^2)x\}\\
&=\tfrac12\{x[x,p^2]+[p^2,x]x\}\\
&=\tfrac12(2i\hbar xp-2i\hbar px)\\
&=i\hbar[x,p]=(i\hbar)^2=-\hbar^2 I.
\end{aligned}
$$

Next,

$$
\begin{aligned}
H_2-H_3
&=\tfrac12(xpxp+pxpx-2xp^2x)\\
&=\tfrac12\{xp(xp-px)+(px-xp)px\}\\
&=\tfrac12\{xp[x,p]+[p,x]px\}\\
&=\tfrac{i\hbar}{2}(xp-px)=-\tfrac{\hbar^2}{2}I.
\end{aligned}
$$

Finally, use $px^2p=(px)(xp)$ and $xp^2x=(xp)(px)$, so

$$
\begin{aligned}
H_4-H_3&=[px,xp]\\
&=p[x,xp]+[p,xp]x\\
&=p(x[x,p])+([p,x]p)x\\
&=i\hbar px-i\hbar px=0.
\end{aligned}
$$

For $x^3p$, compare $\tfrac12(x^3p+px^3)$ with $\tfrac12(xpx^2+x^2px)$; their difference is

$$
\begin{aligned}
\frac12\{x^3p+px^3-xpx^2-x^2px\}
&=\tfrac12\{x^2[x,p]+[p,x]x^2\}=0.
\end{aligned}
$$

The $xp^3$ calculation is analogous. Thus the degree-four ambiguity is at most a multiple of $I$: it shifts all energies equally and does not change measurement probabilities.

**(c) Degree greater than four — counterexample.** Use the classical monomial $x^3p^2$ of degree five. Two Hermitian orderings are

$$
K_1=\tfrac12(x^3p^2+p^2x^3),\qquad
K_2=\tfrac12(x^2p^2x+xp^2x^2).
$$

Subtract and regroup:

$$
\begin{aligned}
K_1-K_2
&=\tfrac12\{x^2(xp^2-p^2x)+(p^2x-xp^2)x^2\}\\
&=\tfrac12[x^2,[x,p^2]]\\
&=\tfrac12[x^2,2i\hbar p]\\
&=i\hbar[x^2,p]\\
&=i\hbar(2i\hbar x)=-2\hbar^2x.
\end{aligned}
$$

The difference depends on the position operator, so it is **not** just a constant energy shift.

## Lecture Problem 2.2.1 — Three operator-exponential identities

The lecture explicitly asks for proofs. The starting point is the definition of the exponential and ordinary differentiation, not memorized BCH formulas.

### (a) If $[A,B]=0$, prove $e^Ae^B=e^{A+B}$

$$
\begin{aligned}
e^Ae^B
&=\left(\sum_{n=0}^\infty\frac{A^n}{n!}\right)
\left(\sum_{m=0}^\infty\frac{B^m}{m!}\right)\\
&=\sum_{k=0}^\infty\sum_{n=0}^{k}\frac{A^nB^{k-n}}{n!(k-n)!}\\
&=\sum_{k=0}^\infty\frac1{k!}
\sum_{n=0}^k\binom{k}{n}A^nB^{k-n}\\
&=\sum_{k=0}^\infty\frac{(A+B)^k}{k!}=e^{A+B}.
\end{aligned}
$$

The binomial step requires $AB=BA$. In particular, $e^Ae^{-A}=I$ because $A$ commutes with $-A$.

### (b) Prove the Hadamard formula

Introduce an auxiliary real variable $r$ and define

$$
f(r)=e^{rA}Be^{-rA}.
$$

Differentiate with the product rule:

$$
\begin{aligned}
f'(r)
&=Ae^{rA}Be^{-rA}-e^{rA}Be^{-rA}A\\
&=e^{rA}(AB-BA)e^{-rA}\\
&=e^{rA}[A,B]e^{-rA}.
\end{aligned}
$$

Differentiate a second time:

$$
\begin{aligned}
f''(r)
&=e^{rA}(A[A,B]-[A,B]A)e^{-rA}\\
&=e^{rA}[A,[A,B]]e^{-rA}.
\end{aligned}
$$

Once more,

$$
f'''(r)=e^{rA}[A,[A,[A,B]]]e^{-rA}.
$$

At $r=0$, the exponentials are $I$, giving

$$
f(0)=B,\quad f'(0)=[A,B],\quad
f''(0)=[A,[A,B]],\quad f'''(0)=[A,[A,[A,B]]].
$$

Now use the **ordinary Taylor expansion of $f$ around zero**:

$$
\begin{aligned}
f(r)
&=f(0)+rf'(0)+\frac{r^2}{2!}f''(0)+\frac{r^3}{3!}f'''(0)+\cdots\\
&=B+r[A,B]+\frac{r^2}{2!}[A,[A,B]]
+\frac{r^3}{3!}[A,[A,[A,B]]]+\cdots.
\end{aligned}
$$

Set $r=1$:

$$
\boxed{e^ABe^{-A}=B+[A,B]+\tfrac12[A,[A,B]]+\cdots.}
$$

The formula is useful **when the nested commutators are easy to calculate**. In the Heisenberg picture it is a tool for finding $U^\dagger OU$, not a replacement for that picture.

### (c) Special BCH: if $[A,B]$ commutes with both $A$ and $B$

Define $C=[A,B]$, with $[A,C]=[B,C]=0$, and

$$
G(r)=e^{rA}e^{rB}e^{-r(A+B)}.
$$

Differentiate, retaining the order of all factors:

$$
\begin{aligned}
G'(r)
&=Ae^{rA}e^{rB}e^{-r(A+B)}
+e^{rA}Be^{rB}e^{-r(A+B)}\\
&\quad-e^{rA}e^{rB}(A+B)e^{-r(A+B)}\\
&=e^{rA}\{Ae^{rB}+Be^{rB}-e^{rB}(A+B)\}e^{-r(A+B)}\\
&=e^{rA}(Ae^{rB}-e^{rB}A)e^{-r(A+B)}.
\end{aligned}
$$

We need to evaluate $e^{rB}Ae^{-rB}$. From part (b),

$$
\begin{aligned}
e^{rB}Ae^{-rB}
&=A+r[B,A]+\frac{r^2}{2!}[B,[B,A]]+\cdots\\
&=A-rC
\end{aligned}
$$

because $[B,C]=0$. Therefore $e^{rB}A=(A-rC)e^{rB}$, and

$$
\begin{aligned}
G'(r)
&=e^{rA}\{Ae^{rB}-(A-rC)e^{rB}\}e^{-r(A+B)}\\
&=rC\,e^{rA}e^{rB}e^{-r(A+B)}=rCG(r).
\end{aligned}
$$

Since $G(0)=I$ and $C$ is independent of $r$, solve by differentiation of $e^{-r^2C/2}G(r)$:

$$
\begin{aligned}
\frac{d}{dr}[e^{-r^2C/2}G(r)]
&=-rCe^{-r^2C/2}G(r)+e^{-r^2C/2}rCG(r)=0.
\end{aligned}
$$

Thus $e^{-r^2C/2}G(r)=I$, meaning $G(r)=e^{r^2C/2}$. Set $r=1$:

$$
G(1)=e^Ae^Be^{-(A+B)}=e^{C/2}.
$$

Multiply on the right by $e^{A+B}$:

$$
\boxed{e^Ae^B=e^{[A,B]/2}e^{A+B}.}
$$

This special BCH identity is **not valid for arbitrary noncommuting operators**; its stated commutation assumptions are essential.

## Lecture Problem 2.3.1 — Short-time propagator from momentum completeness

**Question.** For $H=p^2/(2m)+V(x)$ and a small positive $\delta t$, find the leading short-time position kernel $K(x',\delta t;x,0)$ and identify the classical Lagrangian in the phase.

**Step 1 — First-order evolution.** The exponential is

$$
e^{-iH\delta t/\hbar}
=I-\frac{i\delta t}{\hbar}\left(\frac{p^2}{2m}+V\right)+O(\delta t^2).
$$

The product of the separate kinetic and potential exponentials has exactly the same constant and first-order terms:

$$
\begin{aligned}
e^{-ip^2\delta t/(2m\hbar)}e^{-iV\delta t/\hbar}
&=\left[I-\frac{i\delta t}{\hbar}\frac{p^2}{2m}+O(\delta t^2)\right]
\left[I-\frac{i\delta t}{\hbar}V+O(\delta t^2)\right]\\
&=I-\frac{i\delta t}{\hbar}\left(\frac{p^2}{2m}+V\right)+O(\delta t^2).
\end{aligned}
$$

Thus the two exponentials can be used as a **short-time approximation**, even though kinetic and potential operators do not generally commute.

**Step 2 — Act with $V(x)$ on $|x\rangle$ and insert momentum completeness.**

$$
\begin{aligned}
K&=\langle x'|e^{-iH\delta t/\hbar}|x\rangle\\
&\simeq\langle x'|e^{-ip^2\delta t/(2m\hbar)}|x\rangle
 e^{-iV(x)\delta t/\hbar}\\
&=\int_{-\infty}^{\infty}dp\,
\langle x'|p\rangle e^{-ip^2\delta t/(2m\hbar)}\langle p|x\rangle
 e^{-iV(x)\delta t/\hbar}.
\end{aligned}
$$

Recall the position representation of a momentum eigenstate:

$$
\langle x|p\rangle=\frac{e^{ipx/\hbar}}{\sqrt{2\pi\hbar}},\quad
\langle p|x\rangle=\frac{e^{-ipx/\hbar}}{\sqrt{2\pi\hbar}}.
$$

Therefore

$$
K\simeq\frac{e^{-iV(x)\delta t/\hbar}}{2\pi\hbar}
\int_{-\infty}^{\infty}dp\,
\exp\!\left[\frac{i}{\hbar}\left(p(x'-x)-\frac{p^2\delta t}{2m}\right)\right].
$$

**Step 3 — Complete the square and evaluate the Gaussian.** Put $\Delta x=x'-x$:

$$
\begin{aligned}
p\Delta x-\frac{p^2\delta t}{2m}
&=-\frac{\delta t}{2m}\left[p^2-\frac{2m\Delta x}{\delta t}p\right]\\
&=-\frac{\delta t}{2m}
\left(p-\frac{m\Delta x}{\delta t}\right)^2
+\frac{m(\Delta x)^2}{2\delta t}.
\end{aligned}
$$

Shift $q=p-m\Delta x/\delta t$. Directly apply the Gaussian integral $\int_{-\infty}^{\infty}e^{-aq^2}dq=\sqrt{\pi/a}$ with $a=i\delta t/(2m\hbar)$, understood with the convergence prescription already noted in Mock 4:

$$
\begin{aligned}
\int_{-\infty}^{\infty}dq\,e^{-i\delta t q^2/(2m\hbar)}
&=\sqrt{\frac{\pi}{i\delta t/(2m\hbar)}}\\
&=\sqrt{\frac{2\pi m\hbar}{i\delta t}}.
\end{aligned}
$$

The prefactor from momentum completeness is $1/(2\pi\hbar)$, hence

$$
\frac{1}{2\pi\hbar}
\sqrt{\frac{2\pi m\hbar}{i\delta t}}
=\sqrt{\frac{m}{2\pi i\hbar\delta t}}.
$$

Collecting prefactors and phases,

$$
\boxed{
K(x',\delta t;x,0)\simeq
\sqrt{\frac{m}{2\pi i\hbar\delta t}}
\exp\!\left[\frac{i}{\hbar}
\left(\frac{m(x'-x)^2}{2\delta t}-V(x)\delta t\right)\right].
}
$$

**Step 4 — Identify the classical action in the exponential.** On this short interval, the straight-segment velocity is approximated by $\dot x=(x'-x)/\delta t$, so

$$
\begin{aligned}
L&=\tfrac12m\dot x^2-V(x)
=\frac{m}{2}\left(\frac{x'-x}{\delta t}\right)^2-V(x),\\
S&=L\delta t
=\frac{m(x'-x)^2}{2\delta t}-V(x)\delta t.
\end{aligned}
$$

Thus $K\simeq\sqrt{m/(2\pi i\hbar\delta t)}\,e^{iS/\hbar}$. The lecture writes the **phase relation** $K\sim e^{iS/\hbar}$; the Gaussian prefactor is necessary if the question asks for the complete leading-order kernel.

---

# Part III — Closed-book practice and pitfalls

## Exam recognition map

| Question wording | First line you should write |
|---|---|
| “Find time-dependent measurement probability” | $|\psi(t)\rangle=U(t)|\psi_0\rangle$, then $P=|\langle m|\psi(t)\rangle|^2$ |
| “Change to a moving picture/frame” | $U'=WU$, then $i\hbar\dot U'=(i\hbar\dot WW^\dagger+WHW^\dagger)U'$ |
| “Transform position by translation” | $T(a)=e^{-ia\hat p/\hbar}$, then the first Hadamard commutator |
| “Find how an observable changes with time” | $\dot O_H=(i/\hbar)[H_H,O_H]$ (plus an explicit derivative if present) |
| “Is momentum conserved?” | Calculate $[H,\hat p]$ and connect with translation invariance |
| “Find a propagator” | $K=\langle x_f|U|x_i\rangle$; insert $I=\int dp|p\rangle\langle p|$ |
| “Split the propagator at intermediate time” | $U(T,0)=U(T,t)U(t,0)$ and insert $I=\int dx|x\rangle\langle x|$ |

## High-value checks

1. **Generator sign:** $T(a)=e^{-ia\hat p/\hbar}$ sends $|x\rangle\mapsto|x+a\rangle$, but $T(a)\hat xT(a)^\dagger=\hat x-a$; equivalently $T(a)^\dagger\hat xT(a)=\hat x+a$. Do not conflate state translation with operator conjugation order.
2. **When changing picture:** the additional term $i\hbar\dot WW^\dagger$ is essential; it is not always zero even if $W$ is unitary.
3. **Never combine operator exponentials** unless you have checked commutation (or have supplied a valid BCH correction).
4. **Measurement:** compute amplitudes first and then square; after a measurement, update and normalize the state before predicting the next result.
5. **Propagator:** keep the free-particle Gaussian prefactor when asked for the *full* kernel, even if the lecture focuses mainly on its phase.
6. **Boundary:** §§4.2–4.3 angular momentum and group representation theory should not consume your Chapter 2 revision time if the stated exam cutoff is §4.1.

## Suggested rehearsal sequence

First solve Mock 1 (time evolution and measurement), then Mock 3 (commutator equations), then Mock 2 (picture change using spatial translation), and finally Mock 4 (propagator). The original HW3 rotations are optional enrichment only, and then practise the original numbered Chapter 2 problems in Part II.

---

# Appendix — Original HW3 worked solutions (outside the §4.1 cutoff)

## Source-derived HW3 rotation exercises

> [!warning] These solutions are **enrichment outside the stated exam boundary**, not required Chapter 2 revision. They are retained to demonstrate why the simpler Chapter 2/§4.1 mock problems use the same working pattern.

### Original HW3 Q1 — Hadamard formula for rotations (30 marks, optional)

**Question.** Given $[\hat J_i,\hat J_j]=i\hbar\sum_k\epsilon_{ijk}\hat J_k$, show that

$$
e^{-i\beta\hat{\mathbf J}\cdot\mathbf n/\hbar}
(\hat{\mathbf J}\cdot\mathbf a)
e^{i\beta\hat{\mathbf J}\cdot\mathbf n/\hbar}
=\hat{\mathbf J}\cdot R(\mathbf n,\beta)\mathbf a.
$$

**Step 1 — Set up the handwritten-solution method.** Put

$$
A=-\frac{i\beta}{\hbar}\hat{\mathbf J}\cdot\mathbf n,\qquad
B=\hat{\mathbf J}\cdot\mathbf a.
$$

Recall the Hadamard formula

$$
e^ABe^{-A}=B+[A,B]+\frac1{2!}[A,[A,B]]+\cdots.
$$

**Step 2 — Evaluate the first commutator.** The angular-momentum algebra gives, for ordinary real vectors $\mathbf u,\mathbf v$,

$$
\begin{aligned}
[\hat{\mathbf J}\cdot\mathbf u,\hat{\mathbf J}\cdot\mathbf v]
&=\sum_{ij}u_iv_j[\hat J_i,\hat J_j]\\
&=i\hbar\sum_{ijk}u_iv_j\epsilon_{ijk}\hat J_k\\
&=i\hbar\hat{\mathbf J}\cdot(\mathbf u\times\mathbf v).
\end{aligned}
$$

Therefore

$$
[A,B]=\beta\hat{\mathbf J}\cdot(\mathbf n\times\mathbf a).
$$

**Step 3 — Repeat the same commutator.**

$$
\begin{aligned}
[A,[A,B]]&=\beta^2\hat{\mathbf J}\cdot[\mathbf n\times(\mathbf n\times\mathbf a)],\\
\operatorname{ad}_A^k B&=\beta^k\hat{\mathbf J}\cdot(\mathbf n\times)^k\mathbf a.
\end{aligned}
$$

Split $\mathbf a=\mathbf a_{\parallel}+\mathbf a_{\perp}$, with $\mathbf a_{\parallel}=(\mathbf n\cdot\mathbf a)\mathbf n$. Since $\mathbf n$ has unit norm,

$$
\mathbf n\times(\mathbf n\times\mathbf a)
=(\mathbf n\cdot\mathbf a)\mathbf n-\mathbf a=-\mathbf a_{\perp}.
$$

Further powers alternate between $\mathbf n\times\mathbf a$ and $-\mathbf a_\perp$. The series sums to

$$
\begin{aligned}
e^ABe^{-A}
&=\hat{\mathbf J}\cdot\bigl[\mathbf a_{\parallel}
+\mathbf a_{\perp}\cos\beta
+(\mathbf n\times\mathbf a)\sin\beta\bigr]\\
&=\boxed{\hat{\mathbf J}\cdot R(\mathbf n,\beta)\mathbf a}.
\end{aligned}
$$

**Exam transfer:** You do **not** need the rotational cross-product calculation for §4.1. Learn the easier analogous identity $e^{-ia\hat p/\hbar}\hat x e^{ia\hat p/\hbar}=\hat x-a$ from the single commutator $[\hat x,\hat p]=i\hbar$.

### Original HW3 Q2(a) — Classical rotating field (60-mark problem, part (a), optional)

The classical setup is $\mathbf B(t)=R(\mathbf z,\omega t)\mathbf B_0$, and $\dot{\mathbf J}=\gamma\mathbf J\times\mathbf B$. The student approach is to define $\mathbf J'=R(\mathbf z,-\omega t)\mathbf J$, then use $\partial_\beta R(\mathbf n,\beta)\mathbf a=\mathbf n\times R(\mathbf n,\beta)\mathbf a$ and $R(\mathbf a\times\mathbf b)=(R\mathbf a)\times(R\mathbf b)$. It yields

$$
\begin{aligned}
\dot{\mathbf J}'
&=-\omega\mathbf z\times\mathbf J'+\gamma\mathbf J'\times\mathbf B_0\\
&=-\mathbf J'\times(\omega\mathbf z+\gamma\mathbf B_0).
\end{aligned}
$$

If $\omega_B\mathbf k=\omega\mathbf z+\gamma\mathbf B_0$, the solution with $\mathbf J'(0)=\mathbf j$ is

$$
\boxed{\mathbf J'(t)=R(\mathbf k,-\omega_B t)\mathbf j}.
$$

The full cross-product/index proof belongs to §4.2 and is not needed for the stated midterm.

### Original HW3 Q2(b)(i) — Rotating-frame Hamiltonian (optional original; essential technique)

**Given**

$$
H(t)=-\gamma\hat{\mathbf J}\cdot R(\mathbf z,\omega t)\mathbf B_0,
\qquad i\hbar\dot U=H(t)U,
$$

with $U(0)=I$. Define

$$
U'(t)=W(t)U(t),\qquad W(t)=e^{i\omega t\hat J_z/\hbar}.
$$

**Step 1 — Differentiate the *product*, before simplifying anything:**

$$
\begin{aligned}
i\hbar\dot U'
&=i\hbar\dot W U+i\hbar W\dot U\\
&=-\omega\hat J_z WU+WHU\\
&=\left[-\omega\hat J_z+WHW^\dagger\right]U'.
\end{aligned}
$$

Thus the general transformed Hamiltonian formula is

$$
\boxed{H'=WHW^\dagger+i\hbar\dot W W^\dagger.}
$$

**Step 2 — Apply Q1's rotation identity.** Since $W=e^{i\omega t\hat J_z/\hbar}$,

$$
W(\hat{\mathbf J}\cdot\mathbf b)W^\dagger
=\hat{\mathbf J}\cdot R(\mathbf z,-\omega t)\mathbf b.
$$

Taking $\mathbf b=R(\mathbf z,\omega t)\mathbf B_0$,

$$
WHW^\dagger=-\gamma\hat{\mathbf J}\cdot\mathbf B_0.
$$

Therefore

$$
\boxed{H'=-\omega\hat J_z-\gamma\hat{\mathbf J}\cdot\mathbf B_0
=-\hat{\mathbf J}\cdot(\omega\mathbf z+\gamma\mathbf B_0).}
$$

**Step 3 — Now solve.** Because $H'$ is independent of time,

$$
\begin{aligned}
U'(t)&=e^{-iH't/\hbar},\\
U(t)&=W^\dagger(t)U'(t)
=\boxed{e^{-i\omega t\hat J_z/\hbar}e^{-iH't/\hbar}}.
\end{aligned}
$$

**Student memory chain:** *define $U'=WU$ → product rule → replace $\dot U$ → insert $W^\dagger W$ → identify $H'$ → simplify → exponentiate only after $H'$ is constant.* The main §4.1 mock below repeats exactly this sequence with translations instead of rotations.

### Original HW3 Q2(b)(ii) — Quantum/classical correspondence (optional original)

Starting from $U=W^\dagger e^{-iH't/\hbar}$ and $\hat{\mathbf J}_H(t)=U^\dagger\hat{\mathbf J}U$, repeated use of Q1 produces the operator version of a rotated vector. Let $\omega_B\mathbf k=\omega\mathbf z+\gamma\mathbf B_0$. As $-H'=\omega_B\hat{\mathbf J}\cdot\mathbf k$,

$$
\begin{aligned}
\hat{\mathbf J}_H(t)\cdot\mathbf n
&=U^\dagger(t)(\hat{\mathbf J}\cdot\mathbf n)U(t)\\
&=\hat{\mathbf J}\cdot\left[R(\mathbf k,\omega_Bt)R(\mathbf z,-\omega t)\mathbf n\right].
\end{aligned}
$$

For an initial state satisfying $\langle\hat{\mathbf J}\rangle=\mathbf j$, this gives

$$
\begin{aligned}
\langle\hat{\mathbf J}_H(t)\cdot\mathbf n\rangle
&=\mathbf j\cdot R(\mathbf k,\omega_Bt)R(\mathbf z,-\omega t)\mathbf n\\
&=\left[R(\mathbf z,\omega t)R(\mathbf k,-\omega_Bt)\mathbf j\right]\cdot\mathbf n\\
&=\boxed{\mathbf J_{\rm classical}(t)\cdot\mathbf n}.
\end{aligned}
$$

We used $R^T=R^{-1}$ to shift rotations between the two vectors in the dot product. This is a *§4.2 example* of the same general Heisenberg-picture principle tested directly by Mock 3.

---

