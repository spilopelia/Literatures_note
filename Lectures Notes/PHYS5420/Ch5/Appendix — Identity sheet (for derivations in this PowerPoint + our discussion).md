
Conventions: repeated indices summed; \(\delta_{ij}\) Kronecker; \(\epsilon_{ijk}\) Levi–Civita; \(\partial_i \equiv \partial/\partial r_i\).  
Assume *localized steady currents* unless stated: \(\nabla\cdot\mathbf J=0\) and surface terms vanish.

---

## A. Index ↔ vector identities

### A.1 Cross product
$$
(\mathbf a\times \mathbf b)_i=\epsilon_{ijk}a_j b_k
$$

### A.2 Curl
$$
(\nabla\times\mathbf A)_m=\epsilon_{mni}\partial_n A_i
$$

### A.3 Divergence
$$
\nabla\cdot\mathbf A=\partial_i A_i
$$

### A.4 Triple product
$$
\mathbf a\times(\mathbf b\times\mathbf c)=\mathbf b(\mathbf a\cdot\mathbf c)-\mathbf c(\mathbf a\cdot\mathbf b)
$$

### A.5 Epsilon–epsilon contractions
Most used forms:
$$
\epsilon_{ijk}\epsilon_{imn}=\delta_{jm}\delta_{kn}-\delta_{jn}\delta_{km}
$$
$$
\epsilon_{ijk}\epsilon_{lmk}=\delta_{il}\delta_{jm}-\delta_{im}\delta_{jl}
$$
In the force derivation (contracting over \(j\)):
$$
\epsilon_{ijk}\epsilon_{lmj}=\delta_{im}\delta_{kl}-\delta_{il}\delta_{km}
$$
In the \(B\) from \(A\) derivation (contracting over \(i\)):
$$
\epsilon_{mni}\epsilon_{kji}=\delta_{mk}\delta_{nj}-\delta_{mj}\delta_{nk}
$$

---

## B. Product rules and “steady-current” differential identities

### B.1 Product rule (symbolic)
$$
\partial(sJ)=(\partial s)J+s(\partial J)
$$

### B.2 Key identity used in the slides
$$
\partial_i(s_jJ_i)=(\partial_i s_j)J_i+s_j(\partial_iJ_i)
$$
With \(\partial_i s_j=\delta_{ij}\) and steady current \(\partial_iJ_i=0\):
$$
\partial_i(s_jJ_i)=\delta_{ij}J_i=J_j
$$

---

## C. Divergence theorem / integration-by-parts identities

### C.1 Net current vanishes (localized steady current)
From \(\partial_i(s_jJ_i)=J_j\):
$$
\int J_j\,d^3s=\int \partial_i(s_jJ_i)\,d^3s=\oint s_j\,\mathbf J\cdot d\mathbf a=0
$$
So:
$$
\int \mathbf J\,d^3s=\mathbf 0
$$

### C.2 “Radial flow” integral
Let \(f=\tfrac12 s^2\), so \(\nabla f=\mathbf s\). Then
$$
\nabla\cdot(f\mathbf J)=(\nabla f)\cdot\mathbf J+f(\nabla\cdot\mathbf J)=\mathbf s\cdot\mathbf J
$$
Integrate:
$$
\int (\mathbf s\cdot\mathbf J)\,d^3s=\int \nabla\cdot(f\mathbf J)\,d^3s=\oint f\,\mathbf J\cdot d\mathbf a=0
$$
So:
$$
\int (\mathbf s\cdot\mathbf J)\,d^3s=0
$$

### C.3 Symmetric part of \(\int s_jJ_i\) vanishes
Use \(\partial_k(s_is_jJ_k)\):
$$
\partial_k(s_is_jJ_k)=s_jJ_i+s_iJ_j+s_is_j(\partial_kJ_k)
$$
With \(\partial_kJ_k=0\), integrate and drop surface term:
$$
\int (s_jJ_i+s_iJ_j)\,d^3s=0
$$
Hence \(\int s_jJ_i\) is antisymmetric:
$$
\int s_jJ_i\,d^3s=-\int s_iJ_j\,d^3s
$$

---

## D. Magnetic dipole moment identities

### D.1 Definition
$$
\boldsymbol\mu=\frac12\int \mathbf s\times\mathbf J(\mathbf s)\,d^3s
$$

### D.2 Component form
$$
\mu_k=\frac12\,\epsilon_{kji}\int s_jJ_i\,d^3s
$$

### D.3 Inversion (express \(\int s_jJ_i\) in terms of \(\mu\))
Using antisymmetry:
$$
\int s_jJ_i\,d^3s=\epsilon_{kji}\,\mu_k
$$

---

## E. Thin wire / line-current reductions

### E.1 Volume element of a thin wire
$$
d^3s=da\,dl
$$

### E.2 Converting \(\mathbf J d^3s\) to \(I\,d\boldsymbol\ell\)
For \(\mathbf J=J\hat{\mathbf e}_\ell\):
$$
\mathbf J\,d^3s=(J\hat{\mathbf e}_\ell)\,da\,dl=(J\,da)(\hat{\mathbf e}_\ell\,dl)=I\,d\boldsymbol\ell
$$

### E.3 Moment becomes a line integral
$$
\boldsymbol\mu=\frac12\oint \mathbf s\times I\,d\boldsymbol\ell
$$

### E.4 Area vector identity and \(\mu=IA\)
Define:
$$
\mathbf A\equiv \frac12\oint \mathbf s\times d\boldsymbol\ell
$$
Then:
$$
\boldsymbol\mu=I\mathbf A
$$

### E.5 Triangle area element behind \(\mathbf A\)
$$
d\mathbf A=\frac12\,\mathbf s\times d\boldsymbol\ell,
\qquad
dA=\frac12|\mathbf s\times d\boldsymbol\ell|
$$

---

## F. Areal velocity (Kepler 2nd law connection)

For motion \(d\mathbf r=\mathbf v\,dt\):
$$
d\mathbf A=\frac12\,\mathbf r\times d\mathbf r
$$
$$
\frac{d\mathbf A}{dt}=\frac12\,\mathbf r\times\mathbf v
$$

Point charge current density:
$$
\mathbf J(\mathbf s)=q\,\mathbf v\,\delta^3(\mathbf s-\mathbf r)
$$
Magnetic moment:
$$
\boldsymbol\mu=\frac12\int \mathbf s\times\mathbf J\,d^3s=\frac{q}{2}\,\mathbf r\times\mathbf v
$$
So:
$$
\boldsymbol\mu=q\,\frac{d\mathbf A}{dt}
$$

---

## G. Multipole expansion identities

### G.1 Expansion kernel
$$
\frac{1}{|\mathbf r-\mathbf s|}
=\frac{1}{r}+s_j\partial_j\left(\frac{1}{r}\right)+\frac12 s_js_k\partial_j\partial_k\left(\frac{1}{r}\right)+\cdots
$$

### G.2 Derivatives of \(1/r\)
$$
\partial_i\left(\frac{1}{r}\right)=-\frac{r_i}{r^3}
$$
For \(r\neq 0\):
$$
\partial_i\partial_j\left(\frac{1}{r}\right)=\frac{3r_ir_j-r^2\delta_{ij}}{r^5}
$$

### G.3 Distribution identities
$$
\nabla^2\left(\frac{1}{r}\right)=-4\pi\delta^3(\mathbf r)
$$
Full distribution completion:
$$
\partial_i\partial_j\left(\frac{1}{r}\right)
=\frac{3r_ir_j-r^2\delta_{ij}}{r^5}-\frac{4\pi}{3}\delta_{ij}\delta^3(\mathbf r)
$$

### G.4 Delta sampling
$$
\int f(\mathbf s)\,\delta^3(\mathbf s-\mathbf r)\,d^3s=f(\mathbf r)
$$

---

## H. Dipole vector potential and field

### H.1 Dipole vector potential
From multipole + \(\int s_jJ_i=\epsilon_{kji}\mu_k\):
$$
A_i(\mathbf r)=\frac{\mu_0}{4\pi}\,\epsilon_{kji}\mu_k\,\frac{r_j}{r^3}
$$
Vector form:
$$
\mathbf A(\mathbf r)=\frac{\mu_0}{4\pi}\frac{\boldsymbol\mu\times\mathbf r}{r^3}
$$

### H.2 Curl definition for \(\mathbf B\)
$$
B_m=\epsilon_{mni}\partial_n A_i
$$

---

## I. Dipole “mathematical statement” (contact terms)

Electric dipole:
$$
E_m=\frac{1}{4\pi\epsilon_0}\,p_j\left[\partial_m\partial_j\frac{1}{r}+C\,\delta_{mj}\delta^3(\mathbf r)\right]
$$
Magnetic dipole:
$$
B_m=\frac{\mu_0}{4\pi}\,\mu_j\left[\partial_m\partial_j\frac{1}{r}+C'\,\delta_{mj}\delta^3(\mathbf r)\right]
$$
Constraints:
$$
\nabla\cdot\mathbf E=\frac{\rho}{\epsilon_0},\qquad
\rho=-\mathbf p\cdot\nabla\delta^3(\mathbf r),
$$
$$
\nabla\cdot\mathbf B=0
$$
Result:
$$
C=0,\qquad C'=4\pi
$$

---

## J. Force and torque identities

### J.1 Force on a current distribution
$$
d\mathbf F=(\mathbf J\,d^3s)\times \mathbf B,\qquad
\mathbf F=\int \mathbf J(\mathbf s)\times \mathbf B(\mathbf s)\,d^3s
$$
Component form:
$$
F_i=\epsilon_{ijk}\int J_j(\mathbf s)B_k(\mathbf s)\,d^3s
$$

### J.2 Dipole force result (from epsilon–epsilon contraction)
Intermediate:
$$
F_i=\epsilon_{ijk}\epsilon_{lmj}\,\mu_l\,\partial_m B_k
$$
After contraction:
$$
F_i=\mu_k\partial_i B_k-\mu_i\partial_k B_k
$$
Using \(\nabla\cdot\mathbf B=0\):
$$
F_i=\mu_k\partial_i B_k
$$

### J.3 Identity relating \(\nabla(\mu\cdot B)\) and \((\mu\cdot\nabla)B\)
For constant \(\boldsymbol\mu\):
$$
\nabla(\boldsymbol\mu\cdot\mathbf B)=(\boldsymbol\mu\cdot\nabla)\mathbf B+\boldsymbol\mu\times(\nabla\times\mathbf B)
$$

### J.4 Torque on a current distribution
$$
\boldsymbol\tau=\int \mathbf s\times[\mathbf J(\mathbf s)\times \mathbf B(\mathbf s)]\,d^3s
$$
If \(\mathbf B\) uniform:
$$
\mathbf s\times(\mathbf J\times\mathbf B)=\mathbf J(\mathbf s\cdot\mathbf B)-\mathbf B(\mathbf s\cdot\mathbf J)
$$
and with
$$
\int (\mathbf s\cdot\mathbf J)\,d^3s=0
$$
one obtains:
$$
\boldsymbol\tau=\boldsymbol\mu\times\mathbf B
$$

---

## K. Gauge / AB-effect identities (5.2)

Gauge transformations:
$$
\mathbf A\to \mathbf A+\nabla\Lambda,\qquad
\phi\to \phi-\partial_t\Lambda
$$
Wavefunction phase:
$$
\psi\to \psi\,e^{iq\Lambda/\hbar}
$$
AB phase shift:
$$
\Delta\varphi=\frac{q}{\hbar}\oint \mathbf A\cdot d\mathbf l
=\frac{q}{\hbar}\int \mathbf B\cdot d\mathbf a
=\frac{q}{\hbar}\Phi_B
$$
