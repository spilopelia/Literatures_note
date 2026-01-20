# Gaussian integrals, harmonic oscillators, equipartition, Wick’s theorem (summary)

## Basic definitions
$$
\beta \equiv \frac{1}{k_B T}
$$

Often one sets \(k_B=1\) (and sometimes \(\hbar=1\)), so \(\beta = 1/T\).

---

## Quantum harmonic oscillator (reset zero)
Energy levels (zero-point shifted away):
$$
E_n = n\omega,\qquad n=0,1,2,\dots
$$

Define
$$
\zeta \equiv e^{-\beta \omega}.
$$

Partition function:
$$
Z=\sum_{n=0}^{\infty} e^{-\beta n\omega}
=\sum_{n=0}^{\infty}\zeta^n
=\frac{1}{1-\zeta}.
$$

Derivative and internal energy:
$$
\frac{dZ}{d\beta}
=(1-\zeta)^{-2}\,(-\omega\zeta),
$$
$$
U \equiv -\frac{1}{Z}\frac{dZ}{d\beta}
=\frac{\omega\zeta}{1-\zeta}
=\frac{\omega}{e^{\beta\omega}-1}.
$$

Average occupation number:
$$
\langle n\rangle \equiv N(\omega,T)=\frac{1}{e^{\beta\omega}-1}.
$$

---

## High-temperature (classical) limit
Condition:
$$
\beta\omega=\frac{\hbar\omega}{k_B T}\ll 1.
$$

Approximate \(e^{\beta\omega}-1\simeq \beta\omega\):
$$
U=\frac{\omega}{e^{\beta\omega}-1}\approx \frac{\omega}{\beta\omega}=\frac{1}{\beta}=T
\quad (k_B=1).
$$

Heat capacity:
$$
C=\frac{dU}{dT}=1
\quad (k_B=1).
$$

Per particle / per mole statement:
$$
C = k_B \ \text{(per particle)},\qquad R = N_A k_B \ \text{(per mole)}.
$$

Equipartition theorem (classical):
$$
\text{each quadratic term contributes } \frac{1}{2}k_B T \text{ to } \langle E\rangle.
$$

---

## Low-temperature limit and Einstein temperature
Low-\(T\) (\(\beta\to\infty\)) approximation:
$$
U=\frac{\omega}{e^{\beta\omega}-1}\approx \omega e^{-\beta\omega}.
$$

Chain rule for heat capacity (using \(\beta=1/T\) with \(k_B=1\)):
$$
C=\frac{dU}{dT}=-\frac{1}{T^2}\frac{dU}{d\beta}.
$$

Einstein temperature:
$$
T_E \equiv \omega \equiv \frac{\hbar\omega}{k_B}.
$$

Low-\(T\) heat capacity scaling shown on slide:
$$
C \approx \left(\frac{T_E}{T}\right)^2 e^{-T_E/T}.
$$

---

## Heat capacities from degrees of freedom (examples)
Diatomic gas (typical qualitative values shown):
$$
C=\frac{3}{2}R,\qquad C=\frac{5}{2}R,\qquad C=\frac{7}{2}R.
$$

Dulong–Petit (solid, high \(T\)):
$$
C = 3R \quad \text{(per mole)}.
$$

Debye low-\(T\) behavior:
$$
C \propto T^3.
$$

---

## Classical oscillator partition function in phase space
Hamiltonian (single oscillator):
$$
H=\frac{1}{2}\left(\Pi^2+\omega^2\Phi^2\right).
$$

Classical replacement of the quantum sum by a phase-space integral:
$$
\sum_n \ \longrightarrow\ \int \frac{d\Phi\,d\Pi}{2\pi\hbar}.
$$

Classical partition function:
$$
Z=\int \frac{d\Phi\,d\Pi}{2\pi\hbar}\,
\exp\!\left[-\beta\left(\frac{\Pi^2}{2}+\frac{\omega^2\Phi^2}{2}\right)\right].
$$

Factorization and Gaussian evaluation (as written on slide, with \(\hbar=1\) and \(k_B=1\) conventions implicit):
$$
Z=\frac{1}{2\pi}\left(\int d\Phi\,e^{-\beta\omega^2\Phi^2/2}\right)
\left(\int d\Pi\,e^{-\beta\Pi^2/2}\right)
=\frac{1}{\beta\omega}=\frac{T}{\omega}.
$$

---

## Gaussian moments: direct integral + Gamma function
Define even-moment integral:
$$
I_{2n}=\int d\Phi\,\Phi^{2n}e^{-\alpha\Phi^2/2},
\qquad x=\frac{\alpha\Phi^2}{2}.
$$

After substitution (form shown on slide):
$$
I_{2n}=\left(\frac{2}{\alpha}\right)^{n+1/2}
\int_0^\infty dx\,x^{-1/2}\,x^n\,e^{-x}.
$$

Gamma function recall:
$$
\Gamma(n+1)=\int_0^\infty dx\,x^n e^{-x}.
$$

---

## Gaussian moments: “Method 2” differentiation trick
Basic Gaussian scaling:
$$
\int d\Phi\,e^{-\alpha\Phi^2/2}=A\,\alpha^{-1/2},
\qquad \alpha=\beta K.
$$

Using differentiation (as indicated by \(-2\,d/d\alpha\)):
$$
\int d\Phi\,\Phi^2 e^{-\alpha\Phi^2/2}=A\,\alpha^{-3/2},
$$
$$
\int d\Phi\,\Phi^4 e^{-\alpha\Phi^2/2}=3A\,\alpha^{-5/2},
$$
$$
\int d\Phi\,\Phi^6 e^{-\alpha\Phi^2/2}=(5\cdot 3)A\,\alpha^{-7/2}.
$$

Thermal even moments (heuristic form shown):
$$
\langle \Phi^2\rangle=\frac{T}{K},
\qquad
\langle \Phi^{2n}\rangle = C_{2n}\left(\frac{T}{K}\right)^n.
$$

Coefficients:
$$
C_2=1,\quad C_4=3\cdot 1,\quad C_6=5\cdot 3\cdot 1,\quad \dots
$$
$$
C_{2n}=(2n-1)!!.
$$

Odd moments vanish for an even Gaussian weight:
$$
\langle \Phi^{2n+1}\rangle = 0.
$$

---

## Generating function (single variable)
Define:
$$
Z(J)=e^{W(J)}=\int d\Phi\,\exp\!\left(-\frac{\alpha}{2}\Phi^2+J\Phi\right).
$$

Moments from derivatives (evaluate at \(J=0\)):
$$
\langle \Phi^{2n}\rangle
=Z^{-1}\left(\frac{d}{dJ}\right)^{2n}Z
=e^{-W(J)}\left(\frac{d}{dJ}\right)^{2n}e^{W(J)}\Bigg|_{J=0}.
$$

Complete the square:
$$
-\frac{\alpha}{2}\Phi^2+J\Phi
=-\frac{\alpha}{2}\left(\Phi-\frac{J}{\alpha}\right)^2+\frac{J^2}{2\alpha}
\equiv -\frac{\alpha}{2}\eta^2+\frac{J^2}{2\alpha}.
$$

Result:
$$
Z(J)=Z_0\exp\!\left(\frac{J^2}{2\alpha}\right),
\qquad
W(J)=W_0+\frac{J^2}{2\alpha}.
$$

---

## Wick’s theorem / combinatorics (single source \(J\))
Label derivatives:
$$
\left(\frac{d}{dJ}\right)^{2n}=d_1 d_2 \cdots d_{2n}.
$$

Notation:
$$
W_1=d_1W,\qquad W_{1,2}=d_1d_2W,\qquad W_{1,2,3}=d_1d_2d_3W,\ \dots
$$

Examples shown:
$$
d_1 e^W = W_1 e^W,
$$
$$
d_2d_1 e^W=(W_{1,2}+W_1W_2)e^W,
$$
$$
d_3d_2d_1 e^W=(W_{1,2}W_3+W_{1,3}W_2+W_1W_{2,3}+W_1W_2W_3)e^W.
$$

For four derivatives:
$$
e^{-W}\left(\frac{d}{dJ}\right)^4 e^W
= W_{1,2}W_{3,4}+W_{1,3}W_{2,4}+W_{1,4}W_{2,3}.
$$

Pairing shorthand:
$$
(1,2,3,4)=(1,2)(3,4)+(1,3)(2,4)+(1,4)(2,3).
$$

In the Gaussian case \(W(J)=W_0+\frac{J^2}{2\alpha}\), so:
$$
W_{1,2}=\left(\frac{d}{dJ}\right)^2\left(\frac{J^2}{2\alpha}\right)=\frac{1}{\alpha}=\frac{T}{K}.
$$

Hence:
$$
\langle \Phi^4\rangle = 3\left(\frac{T}{K}\right)^2.
$$

General Gaussian pairing rule:
$$
\langle \Phi_{i_1}\Phi_{i_2}\cdots \Phi_{i_{2n}}\rangle
=\sum_{\text{pairings}} \prod_{\text{pairs }(a,b)} \langle \Phi_{i_a}\Phi_{i_b}\rangle.
$$

---

## Many oscillators (matrix form)
Coordinates \(\Phi_1,\dots,\Phi_N\) and quadratic Hamiltonian term:
$$
H=\cdots+\frac{1}{2}K_{ij}\Phi_i\Phi_j.
$$

Expectation value definition:
$$
\langle \Phi_{i_1}\Phi_{i_2}\cdots\rangle
\equiv
\frac{\int D\Phi\,(\Phi_{i_1}\Phi_{i_2}\cdots)\,e^{-\beta H}}
{\int D\Phi\,e^{-\beta H}}.
$$

Measure shorthand:
$$
D\Phi=d\Phi_1\,d\Phi_2\cdots d\Phi_N.
$$

Introduce sources \(J=(J_1,\dots,J_N)\):
$$
Z(J)=e^{W(J)}=\int D\Phi\,\exp\!\left(-\beta H+J_i\Phi_i\right).
$$

Correlators from derivatives (evaluate at \(J=0\)):
$$
\langle \Phi_{i_1}\Phi_{i_2}\cdots\rangle
=
e^{-W(J)}
\left(\frac{\partial}{\partial J_{i_1}}\frac{\partial}{\partial J_{i_2}}\cdots\right)
e^{W(J)}\Bigg|_{J=0}.
$$

Complete the square (slide form):
$$
-\left(\frac{\beta}{2}\right)K_{ij}\Phi_i\Phi_j + J_i\Phi_i
=
-\left(\frac{\beta}{2}\right)K_{ij}\eta_i\eta_j + \left(\frac{1}{2\beta}\right)L_{ij}J_iJ_j,
$$
$$
\eta_i=\Phi_i+\left(\frac{1}{2\beta}\right)L_{im}J_m,
$$
$$
L_{ij}K_{jk}=\delta_{ik}.
$$

Therefore \(L=K^{-1}\) and (using \(T=1/\beta\) with \(k_B=1\)):
$$
W(J)=\frac{T}{2}L_{ij}J_iJ_j.
$$

Two-point function:
$$
\langle \Phi_i\Phi_j\rangle = T\,L_{ij}=T\,(K^{-1})_{ij}.
$$

Higher even moments: sum over pairings built from \(\langle \Phi_i\Phi_j\rangle\).

---

## Measure / Jacobian analogy (2D plane)
Cartesian vs polar area element:
$$
d\mu=dx\,dy=r\,dr\,d\phi\neq dr\,d\phi.
$$

(Nontrivial Jacobians mean a “constant measure” is not guaranteed under arbitrary coordinate changes.)
