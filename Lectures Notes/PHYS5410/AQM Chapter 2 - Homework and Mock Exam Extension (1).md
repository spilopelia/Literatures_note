---
title: "AQM Chapter 2 — Homework and Mock Exam Extension"
tags: [AQM, chapter-2, chapter-4-1, midterm, long-questions]
---

# AQM Chapter 2 — Homework and Mock Exam Extension

> [!important] Exam boundary
> **Tested syllabus: Chapters 1–3 and Chapter 4 through §4.1 only.** HW3 Q1 and Q2 rely on angular-momentum rotations developed in **§4.2**, so their original angular-momentum content is **outside the stated scope**. Nevertheless, HW3 Q2(b)'s *method*—a time-dependent unitary change of picture—appears in §2.2 and has a close **§4.1 translation analogue**. This note places **original exam-scope mock questions first** and moves the optional HW3 angular-momentum material into a clearly labelled appendix with complete student-style solutions. Original mocks are not past examination questions.
>
> Sources: Tian Lan, *Advanced Quantum Mechanics*, §§2.1–2.3 and 4.1; *Homework 3*, Questions 1–2; accompanying handwritten HW3 solutions. See also [[AQM Chapter 2 - Long Question Revision]] for the numbered lecture problems.

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

Each problem is an **original practice problem**, not a prediction of the exact midterm. The proofs in lecture Problems 2.1.1, 2.1.2, 2.2.1 and 2.3.1 remain examinable, but the mocks deliberately emphasize **using** those methods in physical systems. Attempt each question without the solution first.

## Fully worked §2.2 example — three pictures, one two-level system

> [!important] Original mock example (not a lecture or homework question)
> A **closed-book, student-style** application of all three pictures. No §4.2 rotation operators are required; only Pauli matrices, operator exponentials, unitary transformations and measurements from Chapters 1–2.

### Question (40 marks)

A two-level system has

$$
H=H_0+V,\qquad H_0=\frac{\hbar\omega}{2}Z,\qquad V=\frac{\hbar g}{2}X,
$$

where $\omega,g$ are real, $|\psi(0)\rangle=|0\rangle$, and $X,Y,Z$ are Pauli operators. Define $\Omega=\sqrt{\omega^2+g^2}>0$.

**(a) (15 marks)** Solve the Schrödinger-picture evolution and obtain $P(Z=-1;t)$.

**(b) (10 marks)** Use the Heisenberg picture to calculate $\langle Z_H(t)\rangle$ in the *fixed initial state*, and show it gives the same probability.

**(c) (10 marks)** Derive the interaction-picture state equation and write the explicitly time-dependent interaction Hamiltonian $V_I(t)$.

**(d) (5 marks)** Verify directly, using the interaction-picture state, that the $Z$-measurement probability agrees with (a).

### Student-style worked solution

#### (a) Schrödinger picture: evolve the ket

**First write the matrix** in the $\{|0\rangle,|1\rangle\}$ basis. Recall $Z=\left(\begin{smallmatrix}1&0\\0&-1\end{smallmatrix}\right)$, $X=\left(\begin{smallmatrix}0&1\\1&0\end{smallmatrix}\right)$:

$$
H=\frac{\hbar}{2}\begin{pmatrix}\omega&g\\g&-\omega\end{pmatrix}.
$$

For constant $H$, $U(t)=e^{-iHt/\hbar}$. To evaluate it, **first square the matrix inside $H$**:

$$
\begin{aligned}
(\omega Z+gX)^2
&=\omega^2 Z^2+g^2X^2+\omega g(ZX+XZ)\\
&=(\omega^2+g^2)I=\Omega^2I,
\end{aligned}
$$

using $Z^2=X^2=I$ and $ZX=-XZ$. Thus, with $N=(\omega Z+gX)/\Omega$, we have $N^2=I$. Separate even and odd terms in the exponential series:

$$
\begin{aligned}
U(t)&=e^{-i\Omega tN/2}\\
&=\sum_{k=0}^\infty\frac{(-i\Omega t/2)^{2k}}{(2k)!}I
+\sum_{k=0}^\infty\frac{(-i\Omega t/2)^{2k+1}}{(2k+1)!}N\\
&=\cos\frac{\Omega t}{2}I-i\sin\frac{\Omega t}{2}N.
\end{aligned}
$$

Now apply it to the initial state. Since $Z|0\rangle=|0\rangle$ and $X|0\rangle=|1\rangle$,

$$
\begin{aligned}
|\psi_S(t)\rangle
&=\left[\cos\frac{\Omega t}{2}I
-i\sin\frac{\Omega t}{2}\frac{\omega Z+gX}{\Omega}\right]|0\rangle\\
&=\underbrace{\left(\cos\frac{\Omega t}{2}-i\frac{\omega}{\Omega}\sin\frac{\Omega t}{2}\right)}_{a(t)}|0\rangle
+\underbrace{\left(-i\frac{g}{\Omega}\sin\frac{\Omega t}{2}\right)}_{b(t)}|1\rangle.
\end{aligned}
$$

**Measure $Z=-1$.** Its eigenstate is $|1\rangle$, so the Born rule gives

$$
\boxed{P_S(Z=-1;t)=|\langle1|\psi_S(t)\rangle|^2=|b(t)|^2
=\frac{g^2}{\Omega^2}\sin^2\frac{\Omega t}{2}.}
$$

As a check, $|a(t)|^2+|b(t)|^2=\cos^2(\Omega t/2)+(\omega^2+g^2)\sin^2(\Omega t/2)/\Omega^2=1$.

#### (b) Heisenberg picture: evolve the observable

**Do not evolve the state again.** Here $|\psi_H\rangle=|0\rangle$ and

$$
Z_H(t)=U^\dagger(t)ZU(t),\qquad
\langle Z_H(t)\rangle=\langle0|U^\dagger ZU|0\rangle.
$$

Set $U|0\rangle=a|0\rangle+b|1\rangle$ from part (a). Because $Z|0\rangle=|0\rangle$ and $Z|1\rangle=-|1\rangle$,

$$
\begin{aligned}
\langle Z_H\rangle
&=(a^*\langle0|+b^*\langle1|)Z(a|0\rangle+b|1\rangle)\\
&=(a^*\langle0|+b^*\langle1|)(a|0\rangle-b|1\rangle)\\
&=|a|^2-|b|^2=1-2|b|^2\\
&=\boxed{1-\frac{2g^2}{\Omega^2}\sin^2\frac{\Omega t}{2}}.
\end{aligned}
$$

For an observable with eigenvalues $+1,-1$, $\langle Z\rangle=P(+1)-P(-1)=1-2P(-1)$. Therefore,

$$
P_H(Z=-1;t)=\frac{1-\langle Z_H(t)\rangle}{2}
=\boxed{\frac{g^2}{\Omega^2}\sin^2\frac{\Omega t}{2}}.
$$

This agrees with (a). The Heisenberg expression is *the same calculation reorganized*: $\langle0|U^\dagger ZU|0\rangle=\langle\psi_S(t)|Z|\psi_S(t)\rangle$.

#### (c) Interaction picture: remove the $H_0$ evolution

Define $U_0(t)=e^{-iH_0t/\hbar}=e^{-i\omega tZ/2}$ and the interaction state $|\psi_I(t)\rangle=U_0^\dagger(t)|\psi_S(t)\rangle$.

**Differentiate the full product** (the step frequently omitted in short solutions):

$$
\begin{aligned}
i\hbar\frac{d}{dt}|\psi_I\rangle
&=i\hbar\dot U_0^\dagger|\psi_S\rangle
+U_0^\dagger i\hbar\frac{d}{dt}|\psi_S\rangle\\
&=-H_0U_0^\dagger|\psi_S\rangle+U_0^\dagger(H_0+V)|\psi_S\rangle\\
&=U_0^\dagger V|\psi_S\rangle
=\underbrace{U_0^\dagger VU_0}_{V_I(t)}|\psi_I\rangle.
\end{aligned}
$$

The free terms cancel because $H_0$ commutes with $U_0$. Thus $i\hbar\partial_t|\psi_I\rangle=V_I(t)|\psi_I\rangle$.

To **calculate** $V_I$ rather than just name it, use the diagonal matrices

$$
U_0^\dagger=\begin{pmatrix}e^{i\omega t/2}&0\\0&e^{-i\omega t/2}\end{pmatrix},\qquad
U_0=\begin{pmatrix}e^{-i\omega t/2}&0\\0&e^{i\omega t/2}\end{pmatrix}.
$$

Multiplying them on the two sides of $X$,

$$
\begin{aligned}
U_0^\dagger XU_0
&=\begin{pmatrix}0&e^{i\omega t}\\e^{-i\omega t}&0\end{pmatrix}\\
&=\cos(\omega t)X-\sin(\omega t)Y.
\end{aligned}
$$

The last equality follows from $X=\left(\begin{smallmatrix}0&1\\1&0\end{smallmatrix}\right)$ and $Y=\left(\begin{smallmatrix}0&-i\\i&0\end{smallmatrix}\right)$: the upper-right element is $\cos\omega t+i\sin\omega t$. Therefore,

$$
\boxed{V_I(t)=\frac{\hbar g}{2}\left[\cos(\omega t)X-\sin(\omega t)Y\right].}
$$

Although $H$ is constant, $V_I(t)$ depends on time: the *picture* changes which part carries the time dependence. One must not automatically write $U_I=e^{-i\int V_I dt/\hbar}$ without time ordering.

#### (d) Interaction picture: verify the measurement

Because $Z$ commutes with $U_0(t)$,

$$
Z_I(t)=U_0^\dagger ZU_0=Z.
$$

We can obtain the interaction-picture state without solving the new differential equation again:

$$
\begin{aligned}
|\psi_I(t)\rangle
&=e^{i\omega tZ/2}(a|0\rangle+b|1\rangle)\\
&=e^{i\omega t/2}a|0\rangle+e^{-i\omega t/2}b|1\rangle.
\end{aligned}
$$

Therefore,

$$
\begin{aligned}
P_I(Z=-1;t)
&=|\langle1|\psi_I(t)\rangle|^2\\
&=|e^{-i\omega t/2}b|^2=|b|^2\\
&=\boxed{\frac{g^2}{\Omega^2}\sin^2\frac{\Omega t}{2}}.
\end{aligned}
$$

**Final comparison:** Schrödinger evolves the ket $U|0\rangle$; Heisenberg evolves the measured operator $U^\dagger ZU$; interaction evolves both the ket and operator relative to $H_0$. Every picture yields exactly the same $P(Z=-1;t)$.

### What to reproduce closed-book

1. Write $H$ in a suitable basis; solve $U=e^{-iHt/\hbar}$ and calculate one probability.
2. **Heisenberg:** keep $|\psi(0)\rangle$ fixed, insert $U^\dagger M U$, and show the equality of expectation values algebraically.
3. **Interaction:** define $U_0$, differentiate $U_0^\dagger|\psi_S\rangle$ by the product rule, cancel $H_0$, and explicitly conjugate the interaction $V_I=U_0^\dagger VU_0$.
4. Apply the **same physical observable** in all pictures, transforming it when necessary. Never combine pictures' states and operators inconsistently.

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

**(d)** The outcome $X=+1$ projects onto $P_+=|x+\rangle\langle x+|$. The normalized post-measurement state is

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

Since $\dot W=(iv\hat p/\hbar)W$,

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

**(b)** Integrate momentum first:

$$
\hat p_H(t)=\hat p-FtI.
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

The remaining oscillatory Gaussian, with the usual convergence prescription, is $\int dp\,e^{-iT(p-m\Delta x/T)^2/(2m\hbar)}=\sqrt{2\pi m\hbar/(iT)}$. Combining this with $1/(2\pi\hbar)$ yields the prefactor below. Thus the explicit result is

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

# Part II — Closed-book practice and pitfalls

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

First solve Mock 1 (time evolution and measurement), then Mock 3 (commutator equations), then Mock 2 (picture change using spatial translation), and finally Mock 4 (propagator). The original HW3 rotations are optional enrichment only, while the original Chapter 2 proofs remain in [[AQM Chapter 2 - Long Question Revision]].

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

