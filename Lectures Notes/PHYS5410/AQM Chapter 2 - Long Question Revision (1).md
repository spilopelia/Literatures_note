---
title: AQM Chapter 2 — Long Question Revision
tags: [AQM, chapter-2, long-questions, midterm]
---

# AQM Chapter 2 — Long Question Revision

> [!info] Source and scope
> Tian Lan, *Advanced Quantum Mechanics*, Chapter 2, §§2.1–2.3 (lecture-note printed pages 23–30). All numbered Chapter 2 lecture problems are solved below: **2.1.1, 2.1.2, 2.2.1(a–c), and 2.3.1**. HW2 mostly revisits Chapter 1; its complete solutions are in [[AQM Chapter 1 - Homework 2 Extension]].

## Part I — Connected derivation map

### 1. From unitary evolution to the Hamiltonian (§2.1)

**Recall:** a unitary operator satisfies $U^\dagger U=I$, preserving $\langle\psi|\psi\rangle$. For $U(s,t)$, $U(t,t)=I$ and $U(r,s)U(s,t)=U(r,t)$. The notes distinguish state evolution $U_\psi$ and operator evolution $U_O$:

$$
|\psi(t)\rangle=U_\psi(t)|\psi\rangle,\qquad O(t)=U_O^\dagger(t)OU_O(t).
$$

Their *relative* evolution is $U(t)=U_O(t)U_\psi(t)$, since

$$
\langle\psi(t)|O(t)|\psi(t)\rangle
=\langle\psi|U_\psi^\dagger U_O^\dagger O U_O U_\psi|\psi\rangle
=\langle\psi|U^\dagger O U|\psi\rangle.
$$

**Generator derivation.** Write $U(t+\delta t,t)=I+K(t)\delta t+o(\delta t)$, with $K(t)=\left.\partial_sU(s,t)\right|_{s=t}$. Unitarity gives

$$
\begin{aligned}
I&=U(t+\delta t,t)U^\dagger(t+\delta t,t)\\
 &=I+\bigl(K+K^\dagger\bigr)\delta t+o(\delta t),
\end{aligned}
$$

so $K^\dagger=-K$ and $H(t)=i\hbar K(t)$ is Hermitian. Since $U(t+\delta t)=U(t+\delta t,t)U(t)$,

$$
\boxed{i\hbar\frac{dU(t)}{dt}=H(t)U(t).}
$$

If $H$ is constant, $U(t)=e^{-iHt/\hbar}$. For an energy eigenvector $H|E\rangle=E|E\rangle$,

$$
U(t)|E\rangle=\sum_{n\ge0}\frac{(-it/\hbar)^n}{n!}H^n|E\rangle=e^{-iEt/\hbar}|E\rangle.
$$

Thus its energy probability distribution is unchanged. For time-dependent noncommuting $H(t)$, **later times act on the left**:

$$
U(t)=\mathcal T\exp\left[-\frac{i}{\hbar}\int_0^t H(s)\,ds\right]
=\lim_{N\to\infty}e^{-iH(t_N)\Delta t/\hbar}\cdots e^{-iH(t_1)\Delta t/\hbar}.
$$

Do not replace this with an ordinary exponential unless $[H(t),H(t')]=0$ for all times. The notes also define $i\hbar\dot U_\psi=H_\psi U_\psi$ and $i\hbar\dot U_O=U_O H_O$, from which

$$
\boxed{U_O^\dagger H U_O=H_\psi+H_O.}
$$

**Memorize:** unitarity; generator definition; evolution equation. **Derive:** skew-Hermitian derivative, time ordering, energy phase.

### 2. Dynamical pictures (§2.2)

These are alternative placements of the *same relative evolution* between states and observables.

| Picture | State | Operator | Evolution equation |
|---|---|---|---|
| Schrödinger | $|\psi_S(t)\rangle=U(t)|\psi_0\rangle$ | $O_S=O$ | $i\hbar\partial_t|\psi_S\rangle=H|\psi_S\rangle$ |
| Heisenberg | $|\psi_H\rangle=|\psi_0\rangle$ | $O_H=U^\dagger O U$ | $\dot O_H=(i/\hbar)[U^\dagger H U,O_H]$ |
| Interaction | $|\psi_I\rangle=e^{iH_ft/\hbar}U|\psi_0\rangle$ | $O_I=e^{iH_ft/\hbar}Oe^{-iH_ft/\hbar}$ | $i\hbar\partial_t|\psi_I\rangle=H_{i,I}|\psi_I\rangle$ |

For the Heisenberg equation, differentiate **all factors** (note $\dot U=-iHU/\hbar$, $\dot U^\dagger=iU^\dagger H/\hbar$):

$$
\begin{aligned}
\dot O_H&=\dot U^\dagger OU+U^\dagger O\dot U\\
&=\frac{i}{\hbar}U^\dagger HOU-\frac{i}{\hbar}U^\dagger OHU\\
&=\frac{i}{\hbar}[U^\dagger H U,U^\dagger O U].
\end{aligned}
$$

For $H=H_f+H_i(t)$, let $U_f=e^{-iH_ft/\hbar}$ and $|\psi_I\rangle=U_f^\dagger|\psi_S\rangle$. Then

$$
\begin{aligned}
i\hbar\partial_t|\psi_I\rangle
&= -H_f U_f^\dagger|\psi_S\rangle+U_f^\dagger H|\psi_S\rangle\\
&=U_f^\dagger H_i U_f|\psi_I\rangle,
\end{aligned}
$$

so $H_{i,I}=e^{iH_ft/\hbar}H_i(t)e^{-iH_ft/\hbar}$. In every picture the measured expectation is the same:

$$
\langle\psi_S(t)|O|\psi_S(t)\rangle
=\langle\psi_0|O_H(t)|\psi_0\rangle.
$$

**Operator-exponential toolkit:** $[A,B]=AB-BA$; $\operatorname{ad}_A(B)=[A,B]$; commuting-exponential rule; Hadamard conjugation and special BCH formula. Their proofs are in Problem 2.2.1. HW2 Q1 supplies a useful prerequisite on $\operatorname{ad}$.

### Worked three-picture example (separate exam-style exercise)

The fully worked two-level example is in [[AQM Chapter 2 - Homework and Mock Exam Extension#Fully worked §2.2 example — three pictures, one two-level system]]. It develops the same probability in all pictures using explicit matrices, derivative steps and normalization.

### 3. From short-time propagators to the path integral (§2.3)

Insert position completeness $I=\int dx\,|x\rangle\langle x|$ between consecutive short-time propagators:

$$
\begin{aligned}
K(x_f,T;x_i,0)&=\langle x_f|U(T)|x_i\rangle\\
&=\int dx_1\cdots dx_{N-1}\prod_{j=1}^{N}\langle x_j|U(t_j,t_{j-1})|x_{j-1}\rangle.
\end{aligned}
$$

For the free particle, insert momentum completeness and use $\langle x|p\rangle=(2\pi\hbar)^{-1/2}e^{ipx/\hbar}$:

$$
\begin{aligned}
K_0(x',T;x,0)&=\frac1{2\pi\hbar}\int dp\,
\exp\left[\frac i\hbar\left(p(x'-x)-\frac{p^2T}{2m}\right)\right]\\
&=\sqrt{\frac{m}{2\pi i\hbar T}}\exp\left[\frac i\hbar\frac{m(x'-x)^2}{2T}\right].
\end{aligned}
$$

The exponent is the classical **action** for the straight path, $S=\int_0^T (m\dot x^2/2)dt$. The general expression is

$$
\boxed{K(x_f,T;x_i,0)=\int_{x(0)=x_i}^{x(T)=x_f}\!\mathcal D x\,e^{iS[x]/\hbar}.}
$$

The normalization of each short-time factor is absorbed into the measure $\mathcal D x$. When $\hbar\to0$, neighboring paths with rapidly different $S$ cancel; paths around $\delta S=0$ reinforce, connecting to classical mechanics. **Derive:** the short-time kernel in Problem 2.3.1; do not memorize the path integral as a rule without understanding the inserted identities.

## Part II — Worked Chapter 2 lecture problems

### Problem 2.1.1 — Explicitly time-dependent operators

**Given:** $A_t(t)=U_O^\dagger(t)A_tU_O(t)$, where the middle $A_t$ has explicit time dependence. **Find:** its differential equation.

Differentiate by the product rule. With $i\hbar\dot U_O=U_OH_O$ and therefore $\dot U_O=-(i/\hbar)U_OH_O$, $\dot U_O^\dagger=(i/\hbar)H_OU_O^\dagger$,

$$
\begin{aligned}
\frac{d A_t(t)}{dt}
&=\dot U_O^\dagger A_tU_O+U_O^\dagger\frac{dA_t}{dt}U_O+U_O^\dagger A_t\dot U_O\\
&=\frac{i}{\hbar}H_O A_t(t)-\frac{i}{\hbar}A_t(t)H_O+U_O^\dagger\frac{dA_t}{dt}U_O\\
&=\boxed{\frac{i}{\hbar}[H_O,A_t(t)]+\left(\frac{\partial A}{\partial t}\right)_{\rm explicit,picture}}.
\end{aligned}
$$

Here $(\partial A/\partial t)_{\rm explicit,picture}:=U_O^\dagger(dA_t/dt)U_O$. **Check:** for $U_O=I$ only explicit change remains; for $dA_t/dt=0$ this reduces to the lecture Heisenberg-type equation. The printed model answer uses a shorthand $\partial A_t/\partial t$ for the transformed explicit derivative; the definition matters.

### Problem 2.1.2 — Canonical quantization and operator-order ambiguity

**Given:** the classical monomials $x^ap^b$ and $[\hat x,\hat p]=i\hbar I$. Different quantum orderings must be **Hermitian**. We compare operators having the same commuting classical limit, restricting to real ordering coefficients as in the supplied model solution.

**(a) Total degree $a+b<4$.** For $xp$ Hermiticity selects the symmetric combination:

$$
\widehat{xp}=\tfrac12(\hat x\hat p+\hat p\hat x).
$$

For $x^2p$, the distinct monomial orderings are $x^2p$, $xpx$, $px^2$; since $[x,p]=i\hbar$,

$$
\begin{aligned}
x^2p&=x(px+i\hbar)=xpx+i\hbar x,\\
px^2&=(xp-i\hbar)x=xpx-i\hbar x,\\
\frac{x^2p+px^2}{2}&=xpx.
\end{aligned}
$$

Thus all real Hermitian combinations $a(x^2p+px^2)+(1-2a)xpx$ collapse to $xpx$. Similarly $\tfrac12(xp^2+p^2x)=pxp$. Pure powers $x^n,p^n$ are unambiguous. **Result:** no ordering ambiguity below degree 4 (with the stated real-coefficient convention).

**(b) Total degree $4$.** For $x^3p$ and $xp^3$, symmetric orderings coincide by the same commutator argument. For $x^2p^2$, use the Hermitian orderings

$$
\begin{aligned}
H_1&=\tfrac12(x^2p^2+p^2x^2), &H_2&=\tfrac12(xpxp+pxpx),\\
H_3&=xp^2x, &H_4&=px^2p.
\end{aligned}
$$

(Here hats are suppressed.) From $[x,p^2]=2i\hbar p$, $[x^2,p]=2i\hbar x$:

$$
\begin{aligned}
H_1-H_3&=\tfrac12\bigl(x[x,p^2]+[p^2,x]x\bigr)
=i\hbar[x,p]=-\hbar^2I,\\
H_2-H_3&=\tfrac12\bigl(xp[x,p]+[p,x]px\bigr)
=\tfrac{i\hbar}{2}[x,p]=-\tfrac{\hbar^2}{2}I,\\
H_4-H_3&=px^2p-xp^2x=0.
\end{aligned}
$$

Every difference is a multiple of $I$. Adding $cI$ to $H$ changes $U(t)$ by the global phase $e^{-ict/\hbar}$, not transition probabilities. Hence the ambiguity is an **energy-zero shift**.

**(c) Total degree $>4$.** A counterexample suffices. Compare two Hermitian orderings for $x^3p^2$:

$$
H_1=\tfrac12(x^3p^2+p^2x^3),\qquad
H_2=\tfrac12(x^2p^2x+xp^2x^2).
$$

Apply $[x^n,p]=ni\hbar x^{n-1}$ and $[x^n,p^2]=ni\hbar(x^{n-1}p+px^{n-1})$:

$$
H_1-H_2=i\hbar[x^2,p]=-2\hbar^2 x.
$$

This is **not** a constant multiple of $I$; it changes the physical operator. The lecture model answer's general construction gives the same conclusion. **Exam point:** compare Hermitian orderings, not an arbitrary non-Hermitian pair.

### Problem 2.2.1 — Three operator exponential identities

**(a) Commuting $A,B$.** Expand both exponentials (the order may be rearranged because $AB=BA$):

$$
\begin{aligned}
e^Ae^B&=\sum_{n,m\ge0}\frac{A^nB^m}{n!m!}
=\sum_{k\ge0}\frac1{k!}\sum_{n=0}^k\binom{k}{n}A^nB^{k-n}\\
&=\sum_{k\ge0}\frac{(A+B)^k}{k!}=\boxed{e^{A+B}}.
\end{aligned}
$$

In particular $e^{-A}e^A=I$.

**(b) Hadamard formula.** Set $F(r)=e^{rA}Be^{-rA}$ and differentiate both exponentials:

$$
\begin{aligned}
F'(r)&=Ae^{rA}Be^{-rA}-e^{rA}Be^{-rA}A\\
&=[A,F(r)],\qquad F(0)=B.
\end{aligned}
$$

Successive derivatives give $F^{(n)}(0)=\operatorname{ad}_A^n(B)$. Taylor-expand at $r=0$ and set $r=1$:

$$
\boxed{e^ABe^{-A}=B+[A,B]+\frac1{2!}[A,[A,B]]+\frac1{3!}[A,[A,[A,B]]]+\cdots.}
$$

Equivalently, $e^AB=(e^{\operatorname{ad}_A}B)e^A$. Note that the derivative is $F'=\operatorname{ad}_A F$, **not** $r\operatorname{ad}_A F$ (a minor typo in one alternative line of the supplied solution).

**(c) Special BCH.** Assume $C=[A,B]$ commutes with $A$ and $B$. Define $G(r)=e^{rA}e^{rB}e^{-r(A+B)}$. Differentiate:

$$
\begin{aligned}
G'(r)
&=e^{rA}e^{rB}\bigl(e^{-rB}Ae^{rB}-A\bigr)e^{-r(A+B)}\\
&=e^{rA}e^{rB}\bigl(r[A,B]\bigr)e^{-r(A+B)}\\
&=rC\,G(r).
\end{aligned}
$$

The second line follows from Hadamard: $e^{-rB}Ae^{rB}=A+r[A,B]$ (higher nested commutators vanish). Since $C$ commutes with all factors, solve $G'=rCG$, $G(0)=I$:

$$
G(r)=e^{r^2C/2},\qquad \boxed{e^Ae^B=e^{[A,B]/2}e^{A+B}}.
$$

Only use this simplified BCH identity when the stated nested commutators vanish.

### Problem 2.3.1 — Short-time propagator and classical Lagrangian

**Given:** $H=p^2/(2m)+V(x)$ and a small $\delta t$. **Show:** the short-time kernel has phase $S/\hbar$ with $S=[\frac12m((x'-x)/\delta t)^2-V(x)]\delta t$.

Using first-order Trotter splitting (errors are higher order under suitable smoothness assumptions),

$$
\begin{aligned}
K(x',\delta t;x,0)
&=\langle x'|e^{-iH\delta t/\hbar}|x\rangle\\
&\simeq \langle x'|e^{-ip^2\delta t/(2m\hbar)}e^{-iV(x)\delta t/\hbar}|x\rangle\\
&=e^{-iV(x)\delta t/\hbar}\int dp\,\langle x'|p\rangle e^{-ip^2\delta t/(2m\hbar)}\langle p|x\rangle\\
&=\frac{e^{-iV(x)\delta t/\hbar}}{2\pi\hbar}\int dp\,
 e^{\frac i\hbar[p(x'-x)-p^2\delta t/(2m)]}.
\end{aligned}
$$

Complete the square, with $\Delta x=x'-x$:

$$
p\Delta x-\frac{p^2\delta t}{2m}
=-\frac{\delta t}{2m}\left(p-\frac{m\Delta x}{\delta t}\right)^2+\frac{m\Delta x^2}{2\delta t}.
$$

The Gaussian momentum integral yields

$$
\boxed{K\simeq\sqrt{\frac{m}{2\pi i\hbar\delta t}}\,
\exp\left\{\frac i\hbar\left[\frac{m(x'-x)^2}{2\delta t}-V(x)\delta t\right]\right\}.}
$$

Its phase is $e^{iS/\hbar}$, with $S=L\delta t$ and $L=\frac12m\dot x^2-V(x)$, where $\dot x=(x'-x)/\delta t$. **Crucial qualification:** the lecture's $\sim e^{iS/\hbar}$ suppresses the **position-independent short-time normalization factor**; equality without that prefactor would be incorrect. Multiplying short-time kernels and integrating over intermediate positions gives the path integral.

## Part III — Long-question exam rehearsal

1. Reproduce unitarity $\Rightarrow$ skew-Hermitian generator $\Rightarrow$ Schrödinger equation, and explain why time ordering is necessary.
2. Derive the Heisenberg and interaction-picture equations by differentiating their defining transformations.
3. Derive the $x^2p$ ordering identity and the $x^2p^2$ constant shifts. Explain how degree $5$ differs.
4. Prove Hadamard and special BCH starting with parameter-dependent products; state exact commutator assumptions.
5. Derive the short-time kernel: insert $|p\rangle\langle p|$, complete the square, interpret $S$, and identify the discarded prefactor.

> [!note] Cross-chapter links
> HW2 Q1 uses $\operatorname{ad}_A$ and Jacobi for Problem 2.2.1. HW2 Q3 uses $e^{-iap/\hbar}$ as a translation and connects gauge phase changes with the kinetic Hamiltonian in §2.1. See [[AQM Chapter 1 - Homework 2 Extension]].
