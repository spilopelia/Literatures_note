## 0. Roadmap (what the chapter is doing)

Goal: given sources \( \rho(\mathbf r,t)\) and \(\mathbf J(\mathbf r,t)\), solve for \(\mathbf E,\mathbf B\).

Strategy (the standard pipeline):
1. Use the **homogeneous** Maxwell equations to introduce **potentials**.
2. Put potentials into the **inhomogeneous** Maxwell equations \(\Rightarrow\) PDEs for the potentials.
3. Use a **gauge choice** to simplify/decouple the PDEs.
4. In vacuum, solve the resulting wave equations; study plane waves and polarization.
5. Compare EM waves with elastic waves (analogy via Lagrangians).
6. Supplement: finite-width beams \(\Rightarrow\) small longitudinal component + beam spreading.

---

## 1. The potentials

### 1.1 Vector potential

Because \(\nabla\cdot \mathbf B = 0\) is always true (even time-dependent), define \(\mathbf A\) by
$$
\mathbf B(\mathbf r,t) = \nabla\times \mathbf A(\mathbf r,t).
$$

**Physical insight:** “No magnetic monopoles” means magnetic field lines don’t start/end; mathematically that means \(\mathbf B\) can be written as a curl.

---

### 1.2 Scalar potential

Electrostatics had \(\nabla\times\mathbf E=0\Rightarrow \mathbf E=-\nabla\Phi\).  
But time-dependence gives **Faraday’s law**
$$
\nabla\times\mathbf E = -\frac{\partial \mathbf B}{\partial t}.
$$
Substitute \(\mathbf B=\nabla\times\mathbf A\):
$$
\nabla\times\left(\mathbf E+\frac{\partial \mathbf A}{\partial t}\right)=0.
$$
So the bracket has zero curl \(\Rightarrow\) it is a gradient:
$$
\mathbf E+\frac{\partial \mathbf A}{\partial t}=-\nabla\Phi,
$$
hence
$$
\mathbf E(\mathbf r,t) = -\nabla\Phi(\mathbf r,t)-\frac{\partial \mathbf A(\mathbf r,t)}{\partial t}.
$$

**Physical insight (why “EMF with no electric field” can happen):**
- The **EMF** is (work per unit charge around a loop), i.e.
  $$
  \mathcal E=\oint \mathbf E\cdot d\boldsymbol\ell
  $$
  **only** when charges are pushed by an electric field.
- In *motional* cases (moving conductor), charges can be pushed by magnetic Lorentz force \(q\,\mathbf v\times \mathbf B\) even if \(\mathbf E=0\) in the lab region; you still get an effective EMF from non-electrostatic forces.
- In *transformer* cases (changing \(\mathbf B\)), \(\mathbf E\) exists but is **non-conservative**: \(\nabla\times\mathbf E\neq 0\), so a single scalar potential \(\Phi\) cannot describe it globally.

---

### 1.3 Voltage in circuits (path dependence, inductors, Kirchhoff)

#### Key definitions

Inductor flux linkage:
$$
\phi_B = L I.
$$

When flux is changing, typically
$$
\oint \mathbf E\cdot d\boldsymbol\ell \neq 0,
$$
so the usual path-independent “voltage”
$$
V_P=-\int_O^P \mathbf E\cdot d\boldsymbol\ell
$$
becomes **path dependent**.

#### The “which path?” problem for an inductor

An inductor has terminals \(B\) and \(C\). Going from \(B\to C\) through the inductor is not a closed loop; to define a flux you must **close the loop** by adding some return path \(\gamma\). Different \(\gamma\) can enclose different flux, especially if the inductor has very few turns.

---

### Circuit example (battery \( \mathcal E_0\), resistor \(R\), solenoid \(L\))

Define potential differences (pd):
- \(V_{BA}\): across the battery
- \(V_{AC}\): across the resistor
- \(V_{CB}\): “across the inductor”

By definition (but path dependent):
$$
V_{CB} = -\int_B^C \mathbf E\cdot d\boldsymbol\ell.
$$

Three paths \(\gamma_1,\gamma_2,\gamma_3\):
- \(\gamma_1\): returns on a path that **does not enclose flux**
- \(\gamma_2\): along the inductor’s wires
- \(\gamma_3\): on the other side, enclosing some flux

#### Statement 1 (Kirchhoff loop must avoid flux)
Kirchhoff’s loop law corresponds to applying
$$
\oint_{\Gamma_1}\mathbf E\cdot d\boldsymbol\ell = 0
$$
on a loop \(\Gamma_1\) that **encloses no changing flux**. That forces you to use the pd based on \(\gamma_1\), i.e. \(V_{CB}(\gamma_1)\).

**Physical insight:** Kirchhoff’s “sum of drops = 0” is really “\(\oint \mathbf E\cdot d\ell = 0\)”, which fails if the loop threads changing magnetic flux.

#### Statement 2 (difference between \(\gamma_1\) and \(\gamma_3\): one-turn enclosed flux)
$$
V_{CB}(\gamma_1)-V_{CB}(\gamma_3) = -\frac{d\phi'_B}{dt},
$$
where \(\phi'_B\) is the flux through the closed loop formed by \(\gamma_1\) and \(-\gamma_3\). For \(N\) turns, the solenoid linkage scales like
$$
\phi_B \sim N\,\phi'_B.
$$

**Why “only one turn” here?**  
That loop \(\gamma_1-\gamma_3\) goes around the solenoid **once as a geometric loop**, so it counts the flux through that *single* spanning surface once. It is not “flux through one coil turn”; it’s “flux through the loop you just drew”.

#### Statement 3 (difference between \(\gamma_1\) and \(\gamma_2\): flux linkage defining \(L\))
$$
V_{CB}(\gamma_1)-V_{CB}(\gamma_2) = -\frac{d\phi_B}{dt},
$$
where \(\phi_B\) is the flux linkage through the loop \(\gamma_1-\gamma_2\). This is *the* loop whose flux is used to define \(L\).

#### Statement 4 (along a perfect conductor)
$$
V_{CB}(\gamma_2)=0
$$
because inside an ideal wire (negligible resistance) the internal electric field adjusts to (approximately) zero in steady conduction.

**What is “internal \(\mathbf E\)”?**  
It means the microscopic electric field *inside the conductor material*. In ideal-circuit approximations, it is taken as \(0\) along perfect wires; nonzero \(\mathbf E\) is concentrated in resistive elements or in space where induction creates a non-conservative \(\mathbf E\).

#### Combine statements 3 and 4
From (3) and (4):
$$
V_{CB}(\gamma_1)=-\frac{d\phi_B}{dt}=-L\frac{dI}{dt}.
$$

Battery and resistor:
$$
V_{BA}=\mathcal E_0,\qquad V_{AC}=-IR.
$$

Kirchhoff using the correct loop then gives:
$$
\mathcal E_0 - L\frac{dI}{dt}-IR=0.
$$

**Voltmeter insight:** A voltmeter reading depends on its lead placement (i.e. which path it effectively uses), so different hookups can differ by small flux terms.

---

## 2. Gauge transformations

Potentials are not unique. For any \(\Lambda(\mathbf r,t)\),
$$
\Phi \mapsto \Phi-\frac{\partial \Lambda}{\partial t},\qquad
\mathbf A \mapsto \mathbf A+\nabla \Lambda,
$$
leaves \(\mathbf E,\mathbf B\) unchanged.

**Physical insight (trade-off, “like I’m five”):**  
Potentials are like “descriptions” of the same field. You can redraw the “map” (change \(\Phi,\mathbf A\)) without changing the real terrain (\(\mathbf E,\mathbf B\)). Different redrawings make different calculations easier.

---

## 3. Equations for the potential

### 3.1 Arbitrary gauge (still coupled)

Start from
$$
\mathbf E=-\nabla\Phi-\frac{\partial \mathbf A}{\partial t},\qquad
\mathbf B=\nabla\times\mathbf A.
$$

**Gauss’ law** \(\nabla\cdot \mathbf E=\rho/\epsilon_0\) gives
$$
-\nabla^2\Phi-\frac{\partial}{\partial t}(\nabla\cdot \mathbf A)=\frac{\rho}{\epsilon_0}.
$$

**Ampère–Maxwell law**
$$
\nabla\times\mathbf B-\mu_0\epsilon_0\frac{\partial \mathbf E}{\partial t}=\mu_0\mathbf J
$$
leads to
$$
-\nabla^2\mathbf A+\mu_0\epsilon_0\frac{\partial^2\mathbf A}{\partial t^2}+\nabla G=\mu_0\mathbf J,
$$
where
$$
G=\nabla\cdot\mathbf A+\mu_0\epsilon_0\frac{\partial\Phi}{\partial t}.
$$

So you have 4 coupled equations: one for \(\Phi\) and three for \(\mathbf A\).

---

### 3.2 Decoupling (Lorenz gauge)

Choose a gauge so that
$$
G=0,\qquad\text{i.e.}\qquad
\nabla\cdot\mathbf A+\mu_0\epsilon_0\frac{\partial\Phi}{\partial t}=0.
$$
This is the **Lorenz gauge**.

Then \(\mathbf A\) satisfies decoupled wave equations:
$$
\left(-\nabla^2+\mu_0\epsilon_0\frac{\partial^2}{\partial t^2}\right)\mathbf A=\mu_0\mathbf J,
$$
and \(\Phi\) satisfies
$$
\left(-\nabla^2+\mu_0\epsilon_0\frac{\partial^2}{\partial t^2}\right)\Phi=\frac{\rho}{\epsilon_0}.
$$

Combine into a 4-component object \((\Phi,\mathbf A)\):
$$
D\begin{pmatrix}\Phi\\ \mathbf A\end{pmatrix}
=
\begin{pmatrix}\rho/\epsilon_0\\ \mu_0\mathbf J\end{pmatrix},
$$
with the wave operator (d’Alembertian)
$$
D=-\nabla^2+\mu_0\epsilon_0\frac{\partial^2}{\partial t^2}.
$$

**Gauge-freedom check:** Under a gauge transform, \(G\) changes as
$$
G\mapsto G-D\Lambda,
$$
so you can enforce \(G=0\) if you can solve
$$
D\Lambda=f
$$
for a suitable \(f\).

**Physical insight (what “decoupling” means):**  
Before gauge-fixing, the equations for \(\Phi\) and \(\mathbf A\) talk to each other (coupled). The Lorenz gauge is a smart “coordinate choice” that makes each component satisfy its own clean wave equation.

**Relativity connection (four-vector):**  
\((\Phi,\mathbf A)\) is the electromagnetic **4-potential**. The operator \(D\) is the spacetime wave operator; in units with \(c\), it’s the invariant combination matching the spacetime interval.

---

## 4. Solution in free space (vacuum)

In vacuum, the source terms vanish:
$$
D\begin{pmatrix}\Phi\\ \mathbf A\end{pmatrix}=0.
$$

### 4.1 Scalar analog

Try plane wave
$$
\phi(\mathbf r,t)=\phi_0 e^{i(\mathbf k\cdot\mathbf r-\omega t)}.
$$
Then \(\nabla\to i\mathbf k\), \(\partial_t\to -i\omega\), so
$$
D \to k^2-\mu_0\epsilon_0\omega^2.
$$
Setting \(D=0\):
$$
c^2=\frac{\omega^2}{k^2}=\frac{1}{\mu_0\epsilon_0}.
$$

### 4.2 EM waves

Same dispersion for each component \(\Rightarrow\) EM waves propagate at
$$
c=\frac{1}{\sqrt{\mu_0\epsilon_0}}.
$$
Write
$$
D=-\nabla^2+\frac{1}{c^2}\frac{\partial^2}{\partial t^2}.
$$

**Physical insight:** Two “static” constants \(\epsilon_0,\mu_0\) set a wave speed. Historically surprising; conceptually, it reveals that light is an EM wave.

---

### 4.3 Polarization (plane-wave potentials)

Plane-wave potential:
$$
\begin{pmatrix}\Phi\\ \mathbf A\end{pmatrix}
=
\begin{pmatrix}e_0\\ \mathbf e\end{pmatrix}
e^{i(\mathbf k\cdot\mathbf r-\omega t)}.
$$
Here \(e_0\) and \(\mathbf e\) are the **amplitudes** (the “polarization data” for the 4-potential).

Lorenz gauge condition becomes
$$
\mathbf k\cdot\mathbf e-\frac{\omega}{c^2}e_0=0
\quad\Rightarrow\quad
e_0=\frac{\mathbf k\cdot\mathbf e}{k\,c}.
$$

Compute fields:
$$
\mathbf E= -\nabla\Phi-\frac{\partial \mathbf A}{\partial t}
= i\omega\left(\mathbf e-\mathbf k\,\frac{\mathbf k\cdot\mathbf e}{k^2}\right)e^{i(\mathbf k\cdot\mathbf r-\omega t)}.
$$

Define the **transverse projection**:
$$
\mathbf e^{\,T}\equiv \mathbf e-\mathbf k\,\frac{\mathbf k\cdot\mathbf e}{k^2},
$$
or in index form
$$
e_i^{T}=T_{ij}e_j,
\qquad
T_{ij}=\delta_{ij}-\frac{k_i k_j}{k^2}=\delta_{ij}-n_i n_j,
$$
where \(\mathbf n=\mathbf k/k\).

Then
$$
\mathbf E=i\omega (T\mathbf e)\,e^{i(\mathbf k\cdot\mathbf r-\omega t)}.
$$

And
$$
\mathbf B=\nabla\times\mathbf A=i(\mathbf k\times \mathbf e)\,e^{i(\mathbf k\cdot\mathbf r-\omega t)}.
$$

#### Meaning of each term in \(T_{ij}\)
- \(\delta_{ij}\): identity operator (keeps the vector unchanged).
- \(\dfrac{k_i k_j}{k^2}\): projector **onto** the direction of \(\mathbf k\) (longitudinal part).
- \(T_{ij}=\delta_{ij}-\dfrac{k_i k_j}{k^2}\): identity minus “longitudinal projector” \(\Rightarrow\) removes the component along \(\mathbf k\).

**Physical insight:** Only the **transverse** part of \(\mathbf e\) affects \(\mathbf E\) and \(\mathbf B\). The longitudinal part is “gauge-like” for radiation.

If we set the longitudinal part to zero, then \(\mathbf k\cdot\mathbf e=0\Rightarrow e_0=0\), and
$$
\Phi=0,\qquad
\mathbf E=-\frac{\partial \mathbf A}{\partial t},\qquad
\mathbf B=\nabla\times \mathbf A.
$$

**Answers to common confusions (from discussion):**
- **Is wave direction perpendicular to \(\mathbf A\)?** You can choose a gauge where \(\mathbf A\perp \mathbf k\) for radiation, so yes in that common choice. Then \(\mathbf E\parallel \mathbf A\) (for harmonic waves) and both are \(\perp \mathbf k\).
- **Why “longitudinal part not physical”?** Because for freely propagating radiation in vacuum, Maxwell enforces \(\nabla\cdot\mathbf E=0\Rightarrow \mathbf k\cdot\mathbf E=0\). Any longitudinal \(\mathbf e\) can be removed without changing \(\mathbf E,\mathbf B\) (it lives in the gauge redundancy).
- **If \(\Phi\) can be gauged to zero, why keep it?** With sources present, different gauges trade off simplicity: sometimes \(\Phi\) makes boundary conditions, causality (retarded potentials), or solving with \(\rho\) easier. You can’t always make \(\Phi=0\) everywhere while keeping other convenient conditions.

#### Transverse vs radial (radiation context)
- “Radial” = along the line from the source to the observation point (the \(\hat{\mathbf r}\) direction).
- “Transverse” = perpendicular to that direction.
Far-field radiation has dominant transverse fields that scale like \(1/r\); energy flux scales like \(1/r^2\) because it’s quadratic in fields.

---

## 5. Analogy with elastic waves (via Lagrangians)

### 5.1 1D elastic waves

Displacement \(\xi(x,t)\). Strain:
$$
e(x,t)=\frac{\partial \xi}{\partial x}.
$$
Strain energy density:
$$
U=\frac{M}{2}\left(\frac{\partial \xi}{\partial x}\right)^2.
$$
Kinetic energy density:
$$
K=\frac{\rho}{2}\left(\frac{\partial \xi}{\partial t}\right)^2.
$$
Lagrangian density:
$$
\mathcal L=\frac{\rho}{2}\left(\frac{\partial \xi}{\partial t}\right)^2-\frac{M}{2}\left(\frac{\partial \xi}{\partial x}\right)^2.
$$
Wave speed:
$$
c^2=\frac{M}{\rho}.
$$

**Why does \(c\) increase with stiffness \(M\)?**  
Bigger \(M\) means the medium produces a larger restoring force for the same distortion, so disturbances “pull their neighbors along” more strongly \(\Rightarrow\) faster propagation.

---

### 5.2 EM waves in vacuum

Magnetic energy density:
$$
U=\frac{1}{2\mu_0}B^2=\frac{1}{2\mu_0}(\nabla\times \mathbf A)^2.
$$
Electric energy density (in the gauge with \(\Phi=0\) for radiation):
$$
K=\frac{\epsilon_0}{2}E^2=\frac{\epsilon_0}{2}\left(\frac{\partial \mathbf A}{\partial t}\right)^2.
$$
Lagrangian density:
$$
\mathcal L=\frac{\epsilon_0}{2}\left(\frac{\partial \mathbf A}{\partial t}\right)^2-\frac{1}{2\mu_0}(\nabla\times \mathbf A)^2.
$$

Analogy:
$$
\rho \leftrightarrow \epsilon_0,\qquad
M \leftrightarrow \mu_0^{-1},
\qquad
\frac{M}{\rho}\leftrightarrow \frac{1}{\mu_0\epsilon_0}.
$$
So
$$
c^2=\frac{1}{\mu_0\epsilon_0}.
$$

**Physical insight about the analogy \(M/\rho \leftrightarrow 1/(\epsilon_0\mu_0)\):**
- \(\epsilon_0\) behaves like an “inertia parameter” for the electric field term (it multiplies the time-derivative energy).
- \(1/\mu_0\) behaves like a “stiffness parameter” for the magnetic spatial-variation term.
- Bigger “stiffness” \((1/\mu_0)\) or smaller “inertia” \((\epsilon_0)\) \(\Rightarrow\) faster waves.

**Modern caveat (in the note):** In vacuum, the logic is often inverted: \(c\) is fundamental, and \(\epsilon_0,\mu_0\) are not independent.

---

## Supplement — Beams of finite lateral extent

### Tilted plane wave

Wavevector slightly off \(z\)-axis:
$$
\mathbf k = q\,\hat{\mathbf x}+k_0\,\hat{\mathbf z},\qquad
k_0=\sqrt{k^2-q^2}\approx k-\frac{q^2}{2k},\quad (|q|\ll k).
$$

### Polarization constraint (transversality)

Let
$$
\mathbf e = u\,\hat{\mathbf x}+v\,\hat{\mathbf z}.
$$
Transverse condition \( \mathbf k\cdot \mathbf e=0\) gives
$$
qu+k_0 v=0
\quad\Rightarrow\quad
v=-\frac{q}{k_0}u\approx -\frac{q}{k}u.
$$

So an approximately \(x\)-polarized wave gains a small \(z\)-component:
$$
\mathbf E \propto \left(\hat{\mathbf x}-\frac{q}{k}\hat{\mathbf z}\right)
e^{iqx}\,e^{-iq^2 z/(2k)}\,e^{i(kz-\omega t)}.
$$

### Superposition to make a finite beam

Define
$$
E_x = \int \frac{dq}{2\pi}\, f(q)\, e^{iqx}\, e^{-iq^2 z/(2k)}.
$$
And
$$
E_z=\frac{i}{k}\frac{\partial E_x}{\partial x}.
$$

Take a Gaussian spectrum:
$$
f(q)=\exp\!\left(-\frac{a^2 q^2}{2}\right).
$$

At the waist \(z=0\):
$$
E_x \propto \exp\!\left(-\frac{x^2}{2a^2}\right),
\qquad
|E_x|^2\propto \exp\!\left(-(x/a)^2\right).
$$

For \(z\neq 0\), the beam width evolves as
$$
a(z)^2=a^2+\frac{z^2}{a^2 k^2},
$$
and far away
$$
a(z)\approx \frac{z}{ak}.
$$

**Uncertainty-principle-style insight (in the note):**
- Confining the beam to width \(\sim a\) means transverse wavenumbers spread \(\Delta q\sim 1/a\).
- Small angle \(\theta\sim q/k\sim 1/(ka)\).
- After distance \(z\), transverse spread \(x\sim z\theta\sim z/(ka)\), matching the result above.

**Summary lessons (from the supplement):**
- Finite beams must have a small longitudinal polarization component of order \(\sim 1/(ka)\).
- Finite beams must spread with characteristic divergence angle \(\sim 1/(ka)\).

Reference cited in the note:
- PT Leung (2015), on Maxwell’s discovery and gauge condition.

---

## Extra “law map” (connects to your earlier questions)

Maxwell equations (differential form) and common “law names”:
$$
\nabla\cdot\mathbf E=\frac{\rho}{\epsilon_0}\quad\text{(Gauss’ law for electricity)}
$$
$$
\nabla\cdot\mathbf B=0\quad\text{(Gauss’ law for magnetism)}
$$
$$
\nabla\times\mathbf E=-\frac{\partial \mathbf B}{\partial t}\quad\text{(Faraday’s law)}
$$
$$
\nabla\times\mathbf B=\mu_0\mathbf J+\mu_0\epsilon_0\frac{\partial \mathbf E}{\partial t}\quad\text{(Ampère–Maxwell law)}
$$

Force law (on charge \(q\)):
$$
\mathbf F=q(\mathbf E+\mathbf v\times\mathbf B)\quad\text{(Lorentz force law)}
$$

Coulomb and Biot–Savart (static limits):
$$
\mathbf E(\mathbf r)=\frac{1}{4\pi\epsilon_0}\frac{q}{r^2}\hat{\mathbf r}\quad\text{(Coulomb field of a point charge)}
$$
$$
\mathbf B(\mathbf r)=\frac{\mu_0}{4\pi}\int \frac{I\,d\boldsymbol\ell\times \hat{\mathbf r}}{r^2}
\quad\text{(Biot–Savart law)}
$$
