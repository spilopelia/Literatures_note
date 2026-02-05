

## 0) Setup, conventions, and goal

Small source condition:
$$
a \ll \lambda = \frac{2\pi c}{\omega}.
$$

Harmonic time dependence:
$$
\mathbf J(\mathbf r,t)=\mathbf J(\mathbf r)\,e^{-i\omega t},\qquad
\mathbf A(\mathbf r,t)=\mathbf A(\mathbf r)\,e^{-i\omega t}.
$$

Define
$$
k=\frac{\omega}{c},\qquad \hat{\mathbf n}=\frac{\mathbf r}{r},\qquad \mathbf k=k\hat{\mathbf n}.
$$

Goal:
$$
\frac{dP}{d\Omega}\ \text{in the radiation zone } (r\to\infty).
$$

---

## 1) Qualitative estimates (E1/M1/E2)

### 1.1 Dipole moment and scaling

Oscillating point charge along \(z\):
$$
z(t)=a\,e^{-i\omega t},\qquad p(t)=p\,e^{-i\omega t},\qquad p=qa.
$$

Electrostatic energy scale and light-crossing time:
$$
E \sim \frac{q^2}{4\pi\epsilon_0 a},\qquad t\sim \frac{a}{c},\qquad
P\sim \frac{E}{t}\sim \frac{q^2}{4\pi\epsilon_0 a}\cdot\frac{c}{a}.
$$

Radiation requires acceleration; for harmonic motion, \(\partial_t^2\sim \omega^2\), and intensity \(\propto E^2\), so \(\propto \omega^4\):
$$
P(E1)\sim \frac{1}{4\pi\epsilon_0}\frac{\omega^4 p^2}{c^3}.
$$

### 1.2 Angular pattern

For an oscillating dipole along \(z\), radiation pattern:
$$
\frac{dP}{d\Omega}\propto \sin^2\theta.
$$

### 1.3 Magnetic dipole (M1) scaling

Magnetic dipole \(\mu\) introduces extra powers of \(1/c\):
$$
P(M1)\sim \frac{1}{4\pi\epsilon_0}\frac{\omega^4\mu^2}{c^5},
\qquad
P(M1)\sim P(E1)\Big(\frac{v}{c}\Big)^2.
$$

### 1.4 Electric quadrupole (E2) scaling

Quadrupole suppressed by extra \((ka)^2\):
$$
P(E2)\sim \frac{q^2}{4\pi\epsilon_0 a}\cdot\frac{c}{a}\cdot\Big(\frac{2\pi a}{\lambda}\Big)^6.
$$

---

## 2) Wave equation for \(\mathbf A\) and radiation-zone field relations

Vector potential equation:
$$
\Big(-\nabla^2+c^{-2}\partial_t^2\Big)\mathbf A=\mu_0\mathbf J.
$$

Assume harmonic time dependence; then
$$
\Big[-\nabla^2+\Big(\frac{\omega}{c}\Big)^2\Big]\mathbf A(\mathbf r)=\mu_0\mathbf J(\mathbf r).
$$

Radiation-zone relations (keep only leading \(1/r\) terms and transverse parts):
$$
\mathbf E=-\partial_t\mathbf A=i\omega \mathbf A,
$$
$$
\mathbf B=\nabla\times\mathbf A\approx ik\,\hat{\mathbf n}\times \mathbf A.
$$

---

## 3) Green’s function for Helmholtz operator

Define the Green’s function \(G\) by
$$
\Big[-\nabla^2+\Big(\frac{\omega}{c}\Big)^2\Big]G(\mathbf r)=\delta^3(\mathbf r).
$$

Then the solution is
$$
\mathbf A(\mathbf r)=\mu_0\int G(\mathbf r-\mathbf s)\,\mathbf J(\mathbf s)\,d^3s.
$$

### 3.1 Position-space derivation (radial ODE)

For \(r>0\), with \(G=G(r)\):
$$
\frac{1}{r^2}\frac{d}{dr}\Big(r^2\frac{dG}{dr}\Big)+\Big(\frac{\omega}{c}\Big)^2G=0.
$$

Let
$$
G(r)=\frac{H(r)}{r}.
$$

Then
$$
\frac{d^2H}{dr^2}+\Big(\frac{\omega}{c}\Big)^2H=0
\quad\Rightarrow\quad
H(r)=Ae^{i\omega r/c}+Be^{-i\omega r/c}.
$$

Outgoing-wave condition (with \(e^{-i\omega t}\) convention) keeps \(e^{+i\omega r/c}\):
$$
B=0.
$$

Delta-function normalization fixes \(A=1/(4\pi)\), giving
$$
G(r)=\frac{1}{4\pi}\frac{e^{i\omega r/c}}{r}
=\frac{1}{4\pi}\frac{e^{ikr}}{r}.
$$

### 3.2 Momentum-space derivation (Fourier + contour)

Fourier space gives
$$
(k^2-\omega^2)\,\tilde G(\mathbf k)=1
\quad\Rightarrow\quad
\tilde G(\mathbf k)=\frac{1}{k^2-\omega^2}.
$$

Inverse transform:
$$
G(\mathbf r)=\int \frac{d^3k}{(2\pi)^3}\,\frac{e^{i\mathbf k\cdot \mathbf r}}{k^2-\omega^2}.
$$

Choose \(\mathbf r\) as polar axis in \(\mathbf k\)-space and do angular integrals:
$$
\int_{-1}^{1}e^{ikr u}\,du=\frac{e^{ikr}-e^{-ikr}}{ikr}.
$$

Hence
$$
G(r)=\frac{1}{4\pi}\frac{1}{2ir}\int_0^\infty \frac{e^{ikr}-e^{-ikr}}{k^2-\omega^2}\,k\,dk.
$$

Turn it into an integral over \((-\infty,\infty)\):
$$
G(r)=\frac{1}{4\pi}\frac{1}{2ir}\int_{-\infty}^{\infty}\frac{e^{ikr}}{k^2-\omega^2}\,k\,dk
\equiv \frac{1}{4\pi}\frac{1}{2ir}\,I.
$$

Poles at \(k=\pm\omega\). For outgoing waves and \(r>0\), close in the upper half-plane and choose detours so the \(+\omega\) pole contributes. The residue at \(k=\omega\) is
$$
\operatorname{Res}\Big(\frac{k\,e^{ikr}}{(k-\omega)(k+\omega)},k=\omega\Big)
=\left.\frac{k}{k+\omega}e^{ikr}\right|_{k=\omega}=\frac12 e^{i\omega r}.
$$

Thus
$$
I=2\pi i\cdot \frac12 e^{i\omega r}=\pi i\,e^{i\omega r},
$$
and substituting back gives
$$
G(r)=\frac{1}{4\pi}\frac{e^{ikr}}{r}.
$$

---

## 4) Radiation-zone approximation for \(\mathbf A\)

Exact form:
$$
A_i(\mathbf r)=\frac{\mu_0}{4\pi}\int \frac{e^{ik|\mathbf r-\mathbf s|}}{|\mathbf r-\mathbf s|}\,J_i(\mathbf s)\,d^3s.
$$

Radiation zone: keep only \(1/r\) in the prefactor,
$$
\frac{1}{|\mathbf r-\mathbf s|}\approx \frac{1}{r}.
$$

Expand the phase for \(r\gg s\):
$$
|\mathbf r-\mathbf s|=\sqrt{r^2-2\mathbf r\cdot\mathbf s+s^2}
= r\sqrt{1-2\frac{\hat{\mathbf n}\cdot\mathbf s}{r}+\frac{s^2}{r^2}}
\approx r-\hat{\mathbf n}\cdot\mathbf s,
$$
so
$$
k|\mathbf r-\mathbf s|\approx kr-\mathbf k\cdot\mathbf s.
$$

Therefore
$$
A_i(\mathbf r)=\frac{\mu_0}{4\pi}\frac{e^{ikr}}{r}\int e^{-i\mathbf k\cdot\mathbf s}J_i(\mathbf s)\,d^3s
=\frac{\mu_0}{4\pi}\frac{e^{ikr}}{r}\,\tilde J_i(\mathbf k),
$$
where
$$
\tilde J_i(\mathbf k)=\int e^{-i\mathbf k\cdot\mathbf s}J_i(\mathbf s)\,d^3s.
$$

Restore time dependence:
$$
A_i(\mathbf r,t)=\frac{\mu_0}{4\pi}\frac{e^{i(kr-\omega t)}}{r}\,\tilde J_i(\mathbf k).
$$

---

## 5) Radiation-zone fields and transverse projector

Define the transverse projector:
$$
T_{ij}=\delta_{ij}-n_in_j.
$$

Then
$$
E_i=\frac{\mu_0}{4\pi}\frac{e^{ikr}}{r}(i\omega)\,T_{ij}\tilde J_j,
$$
$$
B_i=\frac{\mu_0}{4\pi}\frac{e^{ikr}}{r}\Big(\frac{i\omega}{c}\Big)\epsilon_{ipq}n_p\tilde J_q.
$$

---

## 6) Time averaging and power per solid angle

Time-average rule for complex amplitudes:
$$
\langle f(t)g(t)\rangle=\frac12\,\Re(\tilde f^{\,\ast}\tilde g).
$$

Time-averaged Poynting vector:
$$
\langle \mathbf S\rangle=\frac{1}{2\mu_0}\,\mathbf E^\ast\times \mathbf B,
\qquad
\langle S_i\rangle=\frac{1}{2\mu_0}\epsilon_{ijk}E_j^\ast B_k.
$$

Result:
$$
S=\frac{\mu_0}{4\pi}\frac{1}{8\pi r^2}\frac{\omega^2}{c}\;\Big[\tilde J_i^\ast(\mathbf k)\,T_{ij}\,\tilde J_j(\mathbf k)\Big].
$$

Hence
$$
\frac{dP}{d\Omega}=r^2S
=\frac{1}{4\pi\epsilon_0}\frac{1}{8\pi}\frac{\omega^2}{c^3}\;\Big[\tilde J_i^\ast(\mathbf k)\,T_{ij}\,\tilde J_j(\mathbf k)\Big],
$$
using \(\mu_0=1/(\epsilon_0c^2)\).

---

## 7) Multipole expansion of \(\tilde{\mathbf J}(\mathbf k)\)

Assume \(ks\ll 1\) (small source). Expand:
$$
e^{-i\mathbf k\cdot\mathbf s}=1-ik_\ell s_\ell+\cdots,
$$
so
$$
\tilde J_i=\int (1-ik_\ell s_\ell+\cdots)\,J_i(\mathbf s)\,d^3s.
$$

Continuity equation:
$$
\partial_t\rho+\partial_jJ_j=0
\quad\Rightarrow\quad
\partial_jJ_j=-\partial_t\rho.
$$

With \(\rho(\mathbf s,t)=\rho(\mathbf s)e^{-i\omega t}\):
$$
\partial_t\rho=-i\omega\rho
\quad\Rightarrow\quad
\partial_jJ_j=i\omega\rho.
$$

Key identity:
$$
\partial_j(s_iJ_j)=\delta_{ij}J_j+s_i(\partial_jJ_j)=J_i+i\omega s_i\rho,
$$
so
$$
J_i=\partial_j(s_iJ_j)-i\omega s_i\rho.
$$

Substitute into \(\tilde J_i\) and integrate by parts; surface terms vanish for localized sources:
$$
\tilde J_i
=\int (1-ik_\ell s_\ell)\Big[\partial_j(s_iJ_j)-i\omega s_i\rho\Big]\,d^3s
=ik_j\int s_iJ_j\,d^3s
-i\omega\int s_i\rho\,d^3s
-\omega k_j\int s_is_j\rho\,d^3s.
$$

Split \(s_iJ_j\):
$$
s_iJ_j=\frac{1}{2}(s_iJ_j+s_jJ_i)+\frac{1}{2}(s_iJ_j-s_jJ_i).
$$

Use
$$
\partial_k(s_is_jJ_k)=s_jJ_i+s_iJ_j+s_is_j\partial_kJ_k
=s_jJ_i+s_iJ_j+i\omega s_is_j\rho,
$$
so
$$
\int (s_jJ_i+s_iJ_j)\,d^3s=-i\omega\int s_is_j\rho\,d^3s.
$$

For the antisymmetric piece, use
$$
(s_iJ_j-s_jJ_i)=\epsilon_{ijm}(\mathbf s\times\mathbf J)_m.
$$

Define multipole moments:
$$
p_i\equiv \int s_i\rho\,d^3s,
$$
$$
\mu_m\equiv \frac12\int (\mathbf s\times \mathbf J)_m\,d^3s,
$$
$$
q_{ij}\equiv \int (3s_is_j-s^2\delta_{ij})\,\rho\,d^3s.
$$

After combining terms and subtracting the trace (longitudinal piece \(\propto k_i\) is irrelevant for radiation), the compact result is
$$
\tilde J_i(\mathbf k)= -i\omega p_i \;+\; i\,\epsilon_{ijm}k_j\,\mu_m \;-\;\frac{1}{6}\omega k_j q_{ij}.
$$

---

## 8) E1 angular factor: where \(\sin^2\theta\) comes from

Use
$$
T_{ij}=\delta_{ij}-n_in_j.
$$

Then
$$
p_i^\ast T_{ij}p_j
=p_i^\ast p_i-(p_i^\ast n_i)(n_jp_j)
=|p|^2-|\hat{\mathbf n}\cdot\mathbf p|^2.
$$

If \(\theta\) is the angle between \(\mathbf p\) and \(\hat{\mathbf n}\),
$$
\hat{\mathbf n}\cdot\mathbf p=|p|\cos\theta
\quad\Rightarrow\quad
p_i^\ast T_{ij}p_j=|p|^2(1-\cos^2\theta)=|p|^2\sin^2\theta.
$$

---

## Appendix A — Levi–Civita contractions in \(\langle \mathbf S\rangle\)

Start:
$$
\langle S_i\rangle=\frac{1}{2\mu_0}\epsilon_{ijk}E_j^\ast B_k.
$$

Substitute radiation-zone \(E,B\) and collect prefactors:
$$
\langle S_i\rangle
=\frac{1}{2\mu_0}\Big(\frac{\mu_0}{4\pi}\Big)^2\frac{1}{r^2}\frac{\omega^2}{c}\;
\epsilon_{ijk}\Big[(\delta_{jm}-n_jn_m)\tilde J_m^\ast\Big]
\Big[\epsilon_{kpq}n_p\tilde J_q\Big].
$$

Use the identity:
$$
\epsilon_{ijk}\epsilon_{kpq}=\delta_{ip}\delta_{jq}-\delta_{iq}\delta_{jp}.
$$

Contract:
$$
\epsilon_{ijk}\epsilon_{kpq}(\delta_{jm}-n_jn_m)n_p
=(\delta_{ip}\delta_{jq}-\delta_{iq}\delta_{jp})(\delta_{jm}-n_jn_m)n_p.
$$

First term:
$$
\delta_{ip}\delta_{jq}(\delta_{jm}-n_jn_m)n_p
=\delta_{ip}(\delta_{qm}-n_qn_m)n_p
=n_i(\delta_{qm}-n_qn_m)=n_iT_{qm}.
$$

Second term:
$$
-\delta_{iq}\delta_{jp}(\delta_{jm}-n_jn_m)n_p
=-\delta_{iq}(\delta_{pm}-n_pn_m)n_p
=-\delta_{iq}\,(n_m-(n_pn_p)n_m)=0.
$$

Therefore:
$$
\epsilon_{ijk}\epsilon_{kpq}(\delta_{jm}-n_jn_m)n_p=n_iT_{mq}.
$$

So:
$$
\langle S_i\rangle
=\frac{1}{2\mu_0}\Big(\frac{\mu_0}{4\pi}\Big)^2\frac{1}{r^2}\frac{\omega^2}{c}\;
n_i\Big[\tilde J_m^\ast T_{mq}\tilde J_q\Big],
$$
and the magnitude is
$$
S
=\frac{1}{2\mu_0}\Big(\frac{\mu_0}{4\pi}\Big)^2\frac{1}{r^2}\frac{\omega^2}{c}\;
\Big[\tilde J_m^\ast T_{mq}\tilde J_q\Big].
$$
