## Contents
1. Introduction  
2. Laws of magnetostatics  
3. Vector potential  
4. Biot–Savart law  

---

# 1. Introduction

## 1.1 Magnetostatics as a stand-alone subject
- Treat magnetism from **currents / moving charges** without (yet) invoking relativity/covariance.

## 1.2 Current and moving charge
- A moving point charge acts like a localized current:
$$
\rho(\mathbf r)=q\,\delta^{(3)}(\mathbf r-\mathbf s), 
\qquad 
\mathbf J(\mathbf r)=\rho(\mathbf r)\,\mathbf v
= q\,\mathbf v\,\delta^{(3)}(\mathbf r-\mathbf s).
$$

## 1.3 Force between parallel currents
For two long, straight, parallel wires separated by distance $$r$$:
$$
\frac{F}{\ell}=\kappa\,\frac{I_1 I_2}{r}.
$$

Using Ampère’s law field of a long straight wire:
$$
B(r)=\frac{\mu_0 I_1}{2\pi r},
$$
force per unit length on the second wire (magnitude):
$$
\frac{F}{\ell}=I_2 B
=\frac{\mu_0}{2\pi}\frac{I_1 I_2}{r}.
$$
So
$$
\kappa=\frac{\mu_0}{2\pi}.
$$

## 1.4 Definition of ampere (historical link)
Historically, choosing $$I_1=I_2=1\,\mathrm{A}$$ and $$r=1\,\mathrm{m}$$ gives a reference force per unit length, fixing the numerical value of the constant (and hence linking to $$\mu_0$$ via $$\kappa=\mu_0/(2\pi)$$).

---

# 2. Laws of magnetostatics

## 2.1 Ampère’s law (magnetostatics)

### Integral form
$$
\oint_{\Gamma}\mathbf B\cdot d\boldsymbol{\ell}
=\mu_0 I_{\mathrm{enc}}
=\mu_0\int_S \mathbf J\cdot d\mathbf S.
$$
- $$\Gamma$$: closed loop  
- $$S$$: any surface with boundary $$\partial S=\Gamma$$  
- $$I_{\mathrm{enc}}=\int_S \mathbf J\cdot d\mathbf S$$  

### Differential form (via Stokes’ theorem)
Stokes:
$$
\oint_{\Gamma}\mathbf B\cdot d\boldsymbol{\ell}
=\int_S (\nabla\times\mathbf B)\cdot d\mathbf S
$$
Therefore (magnetostatics):
$$
\nabla\times\mathbf B=\mu_0\mathbf J.
$$

### “OK in magnetostatics, but…” (need for generalization)
Problem: the LHS depends only on the loop $$\Gamma$$, so the RHS must be independent of which spanning surface $$S$$ we pick.  
Charging capacitor example:
- Surface through the wire: $$\int_S \mathbf J\cdot d\mathbf S = I$$  
- Surface through the plate gap: $$\int_S \mathbf J\cdot d\mathbf S = 0$$  
So bare Ampère’s law cannot hold in time-dependent situations.

Charge conservation (continuity equation):
$$
\nabla\cdot\mathbf J=-\frac{\partial\rho}{\partial t}.
$$
If we (incorrectly) used $$\nabla\times\mathbf B=\mu_0\mathbf J$$ always, then taking divergence gives
$$
0=\nabla\cdot(\nabla\times\mathbf B)=\mu_0\nabla\cdot\mathbf J
\;\Rightarrow\;
\nabla\cdot\mathbf J=0,
$$
which contradicts the continuity equation when $$\partial\rho/\partial t\neq 0$$.

Use Gauss’s law:
$$
\nabla\cdot\mathbf E=\frac{\rho}{\varepsilon_0}
\;\Rightarrow\;
\nabla\cdot\frac{\partial\mathbf E}{\partial t}
=\frac{1}{\varepsilon_0}\frac{\partial\rho}{\partial t}.
$$
Combine with continuity:
$$
\nabla\cdot\left(\mathbf J+\varepsilon_0\frac{\partial\mathbf E}{\partial t}\right)=0.
$$
Thus the corrected (Maxwell–Ampère) law is
$$
\nabla\times\mathbf B
=\mu_0\mathbf J+\mu_0\varepsilon_0\frac{\partial\mathbf E}{\partial t}.
$$
Integral form:
$$
\oint_{\Gamma}\mathbf B\cdot d\boldsymbol{\ell}
=\mu_0\int_S\left(\mathbf J+\varepsilon_0\frac{\partial\mathbf E}{\partial t}\right)\cdot d\mathbf S.
$$
Define displacement current:
$$
I_D\equiv \varepsilon_0\frac{d\Phi_E}{dt},
\qquad
\Phi_E\equiv \int_S \mathbf E\cdot d\mathbf S,
$$
so
$$
\oint_{\Gamma}\mathbf B\cdot d\boldsymbol{\ell}=\mu_0\left(I_{\text{cond}}+I_D\right).
$$

## 2.2 No magnetic monopole (Gauss’s law for magnetism)

### Integral form
$$
\oint_S \mathbf B\cdot d\mathbf S = 0.
$$

### Differential form
$$
\nabla\cdot\mathbf B=0.
$$

Physical meaning: magnetic field lines do not begin/end (no magnetic “charge” observed).  
For a straight wire, this is consistent with $$\mathbf B$$ being **tangential** (circles around the wire), not radial.

---

# 3. Vector potential

## 3.1 Definition
Define the vector potential $$\mathbf A$$ by
$$
\mathbf B=\nabla\times\mathbf A.
$$

## 3.2 Gauge degree of freedom
Gauge transformation:
$$
\mathbf A\to \mathbf A'=\mathbf A+\nabla\Lambda.
$$
Then
$$
\mathbf B'=\nabla\times\mathbf A'=\nabla\times\mathbf A+\nabla\times\nabla\Lambda=\mathbf B.
$$
So many different $$\mathbf A$$ produce the same physical $$\mathbf B$$.

### Coulomb gauge
Choose the gauge condition
$$
\nabla\cdot\mathbf A=0.
$$
If initially $$\nabla\cdot\mathbf A=f$$, then after gauge transform:
$$
\nabla\cdot\mathbf A'=\nabla\cdot\mathbf A+\nabla^2\Lambda = f+\nabla^2\Lambda.
$$
Pick $$\Lambda$$ solving
$$
\nabla^2\Lambda=-f
$$
(with boundary conditions such as $$\Lambda\to 0$$ at infinity, or a specified value on a boundary), to enforce $$\nabla\cdot\mathbf A'=0$$.

**Boundary conditions (meaning):** you must specify how $$\Lambda$$ behaves on the boundary/at infinity to ensure the Poisson equation has a well-defined, physically acceptable solution (and to fix uniqueness up to an additive constant).

## 3.3 Vector potential and current (decoupling)
Magnetostatics:
$$
\nabla\times\mathbf B=\mu_0\mathbf J,
\qquad
\mathbf B=\nabla\times\mathbf A.
$$
So
$$
\nabla\times(\nabla\times\mathbf A)=\mu_0\mathbf J
=
\nabla(\nabla\cdot\mathbf A)-\nabla^2\mathbf A.
$$
In Coulomb gauge $$\nabla\cdot\mathbf A=0$$:
$$
-\nabla^2\mathbf A=\mu_0\mathbf J
\quad\Rightarrow\quad
\nabla^2\mathbf A=-\mu_0\mathbf J.
$$
Solution (Green’s function, with decay at infinity):
$$
\mathbf A(\mathbf r)=\frac{\mu_0}{4\pi}\int \frac{\mathbf J(\mathbf r')}{|\mathbf r-\mathbf r'|}\,d^3r'.
$$

## 3.4 Point source (moving point charge; quasi-static)
For a charge at $$\mathbf s$$, define
$$
\boldsymbol{\xi}=\mathbf r-\mathbf s,\qquad \xi=|\boldsymbol{\xi}|.
$$
Scalar potential (electrostatics):
$$
\Phi(\mathbf r)=\frac{1}{4\pi\varepsilon_0}\frac{q}{\xi}.
$$
With $$\mathbf J(\mathbf r)=q\,\mathbf v\,\delta^{(3)}(\mathbf r-\mathbf s)$$, the vector potential becomes
$$
\mathbf A(\mathbf r)=\frac{\mu_0}{4\pi}\frac{q\,\mathbf v}{\xi},
\qquad
A_i(\mathbf r)=\frac{\mu_0}{4\pi}\frac{q\,v_i}{\xi}.
$$
(Quasi-static / leading low-velocity form; full time-dependent result is Liénard–Wiechert.)

### Note: $$\mathbf A$$ matters in QM (AB effect idea)
In quantum mechanics, phase can depend on
$$
\Delta\phi=\frac{q}{\hbar}\oint \mathbf A\cdot d\boldsymbol{\ell}
=\frac{q}{\hbar}\Phi_B,
$$
so regions with $$\mathbf B=0$$ along the path can still show an effect if the enclosed flux is nonzero.

---

# 4. Biot–Savart law (placed last to match PPT flow)

## 4.1 Main formula (as a practical field-computation tool)
For steady currents, the magnetic field can be written as the Biot–Savart integral:
$$
\mathbf B(\mathbf r)=\frac{\mu_0}{4\pi}\int \frac{\mathbf J(\mathbf r')\times(\mathbf r-\mathbf r')}{|\mathbf r-\mathbf r'|^3}\,d^3r'.
$$
(Equivalently, for a thin wire carrying current $$I$$ along curve $$\mathcal C$$:
$$
\mathbf B(\mathbf r)=\frac{\mu_0 I}{4\pi}\int_{\mathcal C}\frac{d\boldsymbol{\ell}'\times(\mathbf r-\mathbf r')}{|\mathbf r-\mathbf r'|^3}.
$$)

## 4.2 Long wire (result)
$$
B(r)=\frac{\mu_0 I}{2\pi r}.
$$

## 4.3 Small loop (magnetic dipole limit)
A small loop behaves like a magnetic dipole with moment
$$
\mathbf m = I\,\mathbf a
$$
(where $$\mathbf a$$ is area vector). (Far-field dipole formulas can be added if needed.)

## 4.4 Solenoid (ideal long solenoid)
Inside an ideal long solenoid:
$$
B \approx \mu_0 n I,
$$
with turn density $$n$$.

---

# Extra: relation between $$\mu$$ and $$\varepsilon$$ (from Maxwell generalization)
Electromagnetic wave speed in vacuum:
$$
c=\frac{1}{\sqrt{\mu_0\varepsilon_0}}
\quad\Rightarrow\quad
\mu_0\varepsilon_0=\frac{1}{c^2}.
$$
In a material:
$$
v=\frac{1}{\sqrt{\mu\varepsilon}},
\qquad
n=\frac{c}{v}=\sqrt{\mu_r\varepsilon_r}.
$$
