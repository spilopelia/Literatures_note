# Chapter 5 — Magnetostatics II (PowerPoint + our discussion)
Source slides: :contentReference[oaicite:0]{index=0}

Conventions: Einstein summation; \(\delta_{ij}\) Kronecker; \(\epsilon_{ijk}\) Levi–Civita; \(\partial_i\equiv \partial/\partial r_i\); \(r=|\mathbf r|\).

---

## Contents
1. Multipole expansion  
2. Magnetic moment  
3. Force & torque on a magnetic dipole  
4. Material medium  
5. Further topics (vector potential, AB effect, monopoles)

---

# 1. Multipole expansion

## 1.1 Potential (electrostatics recall)
Start from the Coulomb potential:
$$
\Phi(\mathbf r)=\frac{1}{4\pi\epsilon_0}\int \frac{\rho(\mathbf s)}{|\mathbf r-\mathbf s|}\,d^3s .
$$

For \(r\gg s\), expand:
$$
\frac{1}{|\mathbf r-\mathbf s|}
= \frac{1}{r} + s_j\,\partial_j\!\left(\frac{1}{r}\right) + \frac{1}{2}s_js_k\,\partial_j\partial_k\!\left(\frac{1}{r}\right)+\cdots .
$$

Define multipole moments:
$$
Q=\int \rho(\mathbf s)\,d^3s,\qquad
p_j=\int s_j\,\rho(\mathbf s)\,d^3s,\qquad
Q_{jk}=\int s_js_k\,\rho(\mathbf s)\,d^3s,\ \dots
$$

So:
$$
\Phi(\mathbf r)=\frac{1}{4\pi\epsilon_0}\left[
\frac{Q}{r}+p_j\,\partial_j\!\left(\frac{1}{r}\right)+\frac{1}{2}Q_{jk}\,\partial_j\partial_k\!\left(\frac{1}{r}\right)+\cdots
\right].
$$

Useful derivatives:
$$
\partial_i\left(\frac{1}{r}\right)=-\frac{r_i}{r^3},
$$
$$
\partial_i\partial_j\left(\frac{1}{r}\right)=\frac{3r_ir_j-r^2\delta_{ij}}{r^5}\qquad (r\neq 0).
$$

Distribution identity:
$$
\nabla^2\left(\frac{1}{r}\right)=-4\pi\delta^3(\mathbf r).
$$

---

## 1.2 Field (magnetostatics: vector potential)
Vector potential:
$$
A_i(\mathbf r)=\frac{\mu_0}{4\pi}\int \frac{J_i(\mathbf s)}{|\mathbf r-\mathbf s|}\,d^3s .
$$

Use the same expansion:
$$
A_i(\mathbf r)=\frac{\mu_0}{4\pi}\left[
\frac{1}{r}\int J_i\,d^3s
+\partial_j\!\left(\frac{1}{r}\right)\int s_jJ_i\,d^3s
+\cdots
\right].
$$

### “No monopole” for steady localized currents
Steady current:
$$
\nabla\cdot\mathbf J=0.
$$
Then:
$$
\int \mathbf J(\mathbf s)\,d^3s=\mathbf 0.
$$
(So the \(1/r\) term vanishes.)

A standard identity used in the slides:
$$
\partial_i(s_jJ_i)=(\partial_i s_j)J_i+s_j(\partial_iJ_i)=\delta_{ij}J_i=J_j,
$$
and integrating + divergence theorem kills the surface term.

---

# 2. Magnetic moment

## 2.1 Current loop (definition)
Magnetic dipole moment:
$$
\boldsymbol\mu=\frac12\int \mathbf s\times\mathbf J(\mathbf s)\,d^3s.
$$

Component form:
$$
\mu_k=\frac12\,\epsilon_{kji}\int s_jJ_i\,d^3s.
$$

For steady localized currents, the symmetric part vanishes:
$$
\int (s_iJ_j+s_jJ_i)\,d^3s=0
\quad\Rightarrow\quad
\int s_jJ_i\,d^3s=\epsilon_{kji}\mu_k.
$$

## 2.2 Dipole form of \(\mathbf A\)
From the multipole term:
$$
A_i(\mathbf r)=\frac{\mu_0}{4\pi}\frac{r_j}{r^3}\int s_jJ_i\,d^3s
=\frac{\mu_0}{4\pi}\,\epsilon_{kji}\mu_k\,\frac{r_j}{r^3}.
$$
Vector form:
$$
\mathbf A(\mathbf r)=\frac{\mu_0}{4\pi}\frac{\boldsymbol\mu\times\mathbf r}{r^3}.
$$

## 2.3 Thin wire loop: \(\mu=IA\)
For a thin wire with cross-section \(da\) and line element \(dl\):
$$
d^3s = da\,dl,\qquad \mathbf J=J\,\hat{\mathbf e}_\ell,
$$
$$
\mathbf J\,d^3s=(J\hat{\mathbf e}_\ell)\,da\,dl=(J\,da)(\hat{\mathbf e}_\ell\,dl)=I\,d\boldsymbol\ell.
$$
So:
$$
\boldsymbol\mu=\frac12\oint \mathbf s\times I\,d\boldsymbol\ell.
$$
Define the area vector:
$$
\mathbf A\equiv \frac12\oint \mathbf s\times d\boldsymbol\ell,
$$
hence:
$$
\boldsymbol\mu=I\mathbf A.
$$

### Triangle/area element in the slides
A small wedge swept by \(\mathbf s\) and \(d\boldsymbol\ell\):
$$
d\mathbf A=\frac12\,\mathbf s\times d\boldsymbol\ell,
\qquad
dA=\frac12|\mathbf s\times d\boldsymbol\ell|.
$$

## 2.4 Connection to Kepler’s 2nd law (“areal velocity”)
For orbital motion \(d\mathbf r=\mathbf v\,dt\):
$$
d\mathbf A=\frac12\,\mathbf r\times d\mathbf r,
\qquad
\frac{d\mathbf A}{dt}=\frac12\,\mathbf r\times\mathbf v.
$$

For a point charge current density:
$$
\mathbf J(\mathbf s)=q\,\mathbf v\,\delta^3(\mathbf s-\mathbf r),
$$
$$
\boldsymbol\mu=\frac12\int \mathbf s\times\mathbf J\,d^3s
=\frac{q}{2}\,\mathbf r\times\mathbf v
=q\,\frac{d\mathbf A}{dt}.
$$
This is why the magnetic moment has the same “shape” as \(dA/dt\): it measures how fast charge sweeps out area (Kepler-2-law form).

---

## 2.5 Relation to angular momentum (fluid picture)
If charge density \(\rho\) moves with velocity \(\mathbf v\):
$$
\mathbf J=\rho\,\mathbf v.
$$
Then:
$$
\boldsymbol\mu=\frac12\int \mathbf s\times(\rho\mathbf v)\,d^3s.
$$

Mechanical angular momentum for mass density \(\rho_m\):
$$
\mathbf L=\int \mathbf s\times(\rho_m\mathbf v)\,d^3s.
$$

If \(\rho(\mathbf r)=\kappa\rho_m(\mathbf r)\) and \(q=\kappa m\), then:
$$
\boldsymbol\mu=\frac{\kappa}{2}\mathbf L=\frac{q}{2m}\mathbf L.
$$

General \(g\)-factor form:
$$
\boldsymbol\mu=g\,\frac{q}{2m}\mathbf L.
$$

Electron (schematic expansion shown):
$$
g = 2 + \frac{\alpha}{\pi} + \cdots + \left(\frac{\alpha}{\pi}\right)^2 + \cdots
$$

---

## 2.6 Electric dipole vs magnetic dipole (distribution “mathematical statement”)
Electric dipole charge distribution:
$$
\rho(\mathbf r)=-\mathbf p\cdot\nabla\delta^3(\mathbf r).
$$
Maxwell constraints:
$$
\nabla\cdot\mathbf E=\frac{\rho}{\epsilon_0},\qquad \nabla\cdot\mathbf B=0.
$$

Slide’s compact tensor statements:
$$
E_m=\frac{1}{4\pi\epsilon_0}\,p_j\left[\partial_m\partial_j\frac1r + C\,\delta_{mj}\delta^3(\mathbf r)\right],
$$
$$
B_m=\frac{\mu_0}{4\pi}\,\mu_j\left[\partial_m\partial_j\frac1r + C'\,\delta_{mj}\delta^3(\mathbf r)\right].
$$

Using
$$
\nabla^2\left(\frac1r\right)=-4\pi\delta^3(\mathbf r)
$$
gives:
$$
C=0,\qquad C'=4\pi.
$$

Equivalent explicit distribution identity:
$$
\partial_i\partial_j\left(\frac{1}{r}\right)
=\frac{3r_ir_j-r^2\delta_{ij}}{r^5}-\frac{4\pi}{3}\delta_{ij}\delta^3(\mathbf r).
$$

So the familiar far-field dipole forms (for \(r\neq 0\)) are:
$$
\mathbf E(\mathbf r)=\frac{1}{4\pi\epsilon_0}\left(\frac{3\mathbf r(\mathbf p\cdot\mathbf r)}{r^5}-\frac{\mathbf p}{r^3}\right),
$$
$$
\mathbf B(\mathbf r)=\frac{\mu_0}{4\pi}\left(\frac{3\mathbf r(\boldsymbol\mu\cdot\mathbf r)}{r^5}-\frac{\boldsymbol\mu}{r^3}\right),
$$
with the magnetic dipole having the contact term implied by \(C'=4\pi\).

---

# 3. Force & torque on a magnetic dipole

## 3.1 Force on a current distribution
Differential and total force:
$$
d\mathbf F = (\mathbf J(\mathbf s)\,d^3s)\times\mathbf B(\mathbf s),
\qquad
\mathbf F=\int \mathbf J(\mathbf s)\times\mathbf B(\mathbf s)\,d^3s.
$$
Component form:
$$
F_i=\epsilon_{ijk}\int J_j(\mathbf s)\,B_k(\mathbf s)\,d^3s.
$$

If \(\mathbf B\) is approximately uniform over the object, the uniform term vanishes because:
$$
\int \mathbf J\,d^3s=\mathbf 0.
$$

In the dipole (slowly varying field) limit the slide’s result is:
$$
F_i=\mu_k\,\partial_i B_k-\mu_i\,\partial_k B_k.
$$
Using \(\nabla\cdot\mathbf B=0\Rightarrow \partial_kB_k=0\):
$$
F_i=\mu_k\,\partial_i B_k.
$$

Vector identity relating common forms:
$$
\nabla(\boldsymbol\mu\cdot\mathbf B)=(\boldsymbol\mu\cdot\nabla)\mathbf B+\boldsymbol\mu\times(\nabla\times\mathbf B).
$$
So if \(\nabla\times\mathbf B=0\) at the dipole position (no current there),
$$
\mathbf F=\nabla(\boldsymbol\mu\cdot\mathbf B).
$$

## 3.2 Torque on a current distribution (uniform \(\mathbf B\))
Torque definition:
$$
\boldsymbol\tau=\int \mathbf s\times\big[\mathbf J(\mathbf s)\times\mathbf B\big]\,d^3s.
$$
Triple-product expansion:
$$
\mathbf s\times(\mathbf J\times\mathbf B)=\mathbf J(\mathbf s\cdot\mathbf B)-\mathbf B(\mathbf s\cdot\mathbf J).
$$
Key “problem” integral in the slide:
$$
\int (\mathbf s\cdot\mathbf J)\,d^3s=0,
$$
so for constant \(\mathbf B\):
$$
\boldsymbol\tau=\boldsymbol\mu\times\mathbf B.
$$

---

# 4. Material medium (macroscopic magnetostatics)

Define magnetization \(\mathbf M\) (dipole moment per unit volume).
Bound currents:
$$
\mathbf J_b=\nabla\times\mathbf M,
\qquad
\mathbf K_b=\mathbf M\times\hat{\mathbf n}.
$$

Split currents:
$$
\mathbf J=\mathbf J_f+\mathbf J_b,
$$
where \(\mathbf J_f\) are “free” currents from external circuits (the slide note: only these are tied to external circuits).

Define \(\mathbf H\):
$$
\mathbf B=\mu_0(\mathbf H+\mathbf M).
$$

Macroscopic Maxwell equations (magnetostatics):
$$
\nabla\cdot\mathbf B=0,
\qquad
\nabla\times\mathbf H=\mathbf J_f.
$$

Linear isotropic medium:
$$
\mathbf M=\chi_m\mathbf H,
\qquad
\mathbf B=\mu_0(1+\chi_m)\mathbf H=\mu\,\mathbf H.
$$

---

# 5. Further topics

## 5.1 Is vector potential necessary?
Definition:
$$
\mathbf B=\nabla\times\mathbf A.
$$
Time-dependent potentials:
$$
\mathbf E=-\nabla\phi-\frac{\partial\mathbf A}{\partial t}.
$$
Gauge freedom:
$$
\mathbf A\to\mathbf A+\nabla\Lambda,
\qquad
\phi\to\phi-\frac{\partial\Lambda}{\partial t}.
$$
Example for constant \(\mathbf B\) (one common choice):
$$
\mathbf A=\frac12\,\mathbf B\times\mathbf r.
$$

## 5.2 Is vector potential physical? (AB effect)
Wavefunction gauge phase:
$$
\psi\to \psi\,e^{iq\Lambda/\hbar}.
$$
Aharonov–Bohm phase shift:
$$
\Delta\varphi=\frac{q}{\hbar}\oint \mathbf A\cdot d\mathbf l
=\frac{q}{\hbar}\int \mathbf B\cdot d\mathbf a
=\frac{q}{\hbar}\Phi_B.
$$

## 5.3 Can there be monopoles? (conceptual)
If magnetic charge density \(\rho_m\) existed:
$$
\nabla\cdot\mathbf B=\rho_m,
$$
and the global representation \(\mathbf B=\nabla\times\mathbf A\) would fail without singularities/patches.

(Dirac quantization often appears in this discussion.)
$$
eg=\frac{n\hbar}{2},\qquad n\in\mathbb Z.
$$

---
