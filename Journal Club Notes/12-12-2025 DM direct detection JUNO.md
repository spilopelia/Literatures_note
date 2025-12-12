---
title: "Sub-GeV Dark Matter Direct Detection with Neutrino Observatories — Leane & Beacom"
tags: [dark-matter, direct-detection, neutrino-detectors, JUNO, scintillator, annual-modulation]
---

## 0. One-sentence idea (connects back to “using neutrino detectors for DM”)
Use a **neutrino observatory’s hardware** (huge scintillator target + lots of PMTs) to look for **dark matter (DM)** by counting **tiny, uncorrelated single-photon hits** in the PMTs and extracting the DM signal via the **known annual modulation**.

Key point: you are **not detecting neutrinos** here. You are reusing the **same detector** but changing the **analysis strategy**:
- Neutrino analyses: identify a *single event* using **many correlated PMT hits**.
- This paper’s DM analysis: individual DM scatters give **≲ 1 PMT hit**, so you **can’t** see events one-by-one; instead you measure a **rate** (hits/day) and search for its **yearly sinusoidal modulation**.

---

## 1. Glossary of jargon (mapped to where it appears later)

### Dark matter (DM), “sub-GeV”
- **DM**: hypothetical particle making up most matter in the Universe (not the atoms we know).
- **sub-GeV**: DM mass below 1 GeV (a GeV is a particle-physics energy/mass unit).

### Scintillator (LAB), PMT, dark rate
- **LAB**: linear alkylbenzene, the liquid in JUNO that produces light when excited.
- **PMT**: photomultiplier tube; counts photons by producing an electrical pulse (“hit”).
- **Dark rate**: PMT hits not caused by physics signals (thermal noise, radioactivity, etc.). This is the dominant background.

### “DM–electron scattering”, “cross section”, “amplitude”
- **Scattering**: DM bumps an electron and transfers energy.
- **Cross section** (σ): an effective area that quantifies how likely the interaction is.
- **Amplitude** (𝓜): the quantum-mechanical “strength” whose square gives probabilities.

### Form factors: \(F_{\rm DM}(q)\) and \(f_{ij}(\vec q)\)
- **Momentum transfer** \(q \equiv |\vec q|\): how much momentum DM gives the electron/molecule.
- \(F_{\rm DM}(q)\): particle-physics model dependence (how interaction strength changes with \(q\)).
- \(f_{ij}(\vec q)\): *molecular* structure factor (how the bound electrons respond to being kicked from level \(i\to j\)).

### Reduced mass \( \mu_{\chi e} \)
- A standard two-body combination:
$$
\mu_{\chi e} \equiv \frac{m_\chi m_e}{m_\chi+m_e}.
$$
It appears whenever two masses interact in a way that depends on their relative motion.

### Annual modulation \(f_{\rm mod}\)
- Earth’s speed through the DM “wind” changes over the year → the DM scattering rate changes slightly in a **known sinusoidal** way.

---

## 2. Physical chain: how a DM scatter becomes a PMT hit
1. DM scatters on a **bound electron** in a LAB molecule.
2. The molecule ends up **excited** (or ionized).
3. De-excitation produces photons (scintillation/fluorescence).
4. Only a fraction of produced photons yield a PMT hit → captured by an **efficiency** factor \( \xi \).

---

## 3. Kinematics: derive the energy transfer relation (paper Eq. 1)

### Setup
- Incoming DM mass \(m_\chi\), velocity \(\vec v\).
- DM loses momentum \(\vec q\), so its momentum changes:
$$
\vec p_i = m_\chi \vec v, \qquad \vec p_f = \vec p_i - \vec q.
$$

### DM kinetic energy change
Nonrelativistic kinetic energy \(E = p^2/(2m)\). So
$$
\Delta E_\chi
= \frac{|\vec p_f|^2}{2m_\chi}-\frac{|\vec p_i|^2}{2m_\chi}
= \frac{|\vec p_i-\vec q|^2-|\vec p_i|^2}{2m_\chi}.
$$

Expand the square:
$$
|\vec p_i-\vec q|^2 = |\vec p_i|^2 -2\vec p_i\cdot \vec q + q^2.
$$

Plug in:
$$
\Delta E_\chi
= \frac{-2\vec p_i\cdot\vec q + q^2}{2m_\chi}
= -\vec v\cdot\vec q + \frac{q^2}{2m_\chi}.
$$

Energy given to the electron/molecule is the negative of DM’s change:
$$
\Delta E_e = -\Delta E_\chi
= \vec q\cdot\vec v - \frac{q^2}{2m_\chi}.
$$

This is the paper’s Eq. (1).

---

## 4. Maximum transferable energy (paper Eq. 2)
From
$$
\Delta E_e = q v \cos\theta - \frac{q^2}{2m_\chi},
$$
the maximum occurs for \(\cos\theta=1\) and optimizing over \(q\):
$$
\frac{d}{dq}\left(qv-\frac{q^2}{2m_\chi}\right)=v-\frac{q}{m_\chi}=0
\;\Rightarrow\; q = m_\chi v.
$$
Then
$$
(\Delta E_e)_{\max} = m_\chi v^2 - \frac{m_\chi^2 v^2}{2m_\chi}
= \frac{1}{2}m_\chi v^2.
$$
This matches the paper’s Eq. (2) scaling.

---

## 5. Microscopic excitation rate: define \((\sigma v)_{ij}\) (paper Eq. 3)

The “reaction rate factor” for exciting a molecule from level \(i\to j\) is written as an integral over momentum transfer:
$$
(\sigma v)_{ij}
=
\int \frac{d^3\vec q}{(2\pi)^3}\,(2\pi)\,\delta(\Delta E_{ij}-\omega)\,
\frac{|\mathcal{M}_{\rm free}|^2\,|f_{ij}(\vec q)|^2}{16\,m_\chi^2\,m_e^2}.
$$

Meaning of each piece:
- \(\Delta E_{ij}\): fixed excitation energy of the molecule.
- \(\omega\): energy transfer, identified with \(\Delta E_e\) from kinematics.
- \(\delta(\Delta E_{ij}-\omega)\): enforces “the energy deposited matches the level spacing”.
- \(|f_{ij}(\vec q)|^2\): molecular response (bound-electron physics).
- \(\mathcal{M}_{\rm free}\): DM–free-electron scattering amplitude.

---

## 6. Connect amplitude to a reference cross section and DM model (paper Eq. 4)
They parameterize the amplitude-squared as
$$
\frac{|\mathcal{M}_{\rm free}|^2}{16\,m_\chi^2\,m_e^2}
\equiv
\frac{\pi\,\bar\sigma_e}{\mu_{\chi e}^2}\,F_{\rm DM}^2(q).
$$

Interpretation:
- \(\bar\sigma_e\): a conventional “reference” DM–electron cross section (defined at a fixed \(q\)).
- \(F_{\rm DM}(q)\): tells you whether interaction is “heavy mediator” or “light mediator”-like:
  - Heavy mediator: \(F_{\rm DM}(q)=1\)
  - Light mediator: \(F_{\rm DM}(q) = (\alpha m_e)^2/q^2\)

---

## 7. Total scattering rate in the detector (paper Eq. 5)
DM number density is \(n_\chi = \rho_\chi/m_\chi\). Multiply by targets and average over velocities:

$$
R_{\rm scatter}
=
\sum_{i,j}
N_{\rm LAB}^e\,
\frac{\rho_\chi}{m_\chi}
\int d^3\vec v\; g_\chi(\vec v)\; (\sigma v)_{ij}.
$$

- \(N_{\rm LAB}^e\): number of target electrons (here: number of LAB molecules × relevant electrons per molecule).
- \(g_\chi(\vec v)\): DM velocity distribution in the lab frame.

---

## 8. Velocity distribution model (paper Eq. 6)
They take a truncated Maxwell–Boltzmann form:
$$
g_\chi(v)
=
\frac{1}{K}
\exp\!\left(-\frac{|\vec v+\vec v_E|^2}{v_0^2}\right)\,
\Theta\!\left(v_{\rm esc}-|\vec v+\vec v_E|\right).
$$

- \(v_0\): characteristic halo speed,
- \(v_E\): Earth’s speed through the halo,
- \(v_{\rm esc}\): galactic escape speed,
- \(K\): normalization constant,
- \(\Theta\): step function (0 or 1), implementing a cutoff.

---

## 9. Derive the “minimum speed” \(v_{\min}(q)\) (paper Eq. 8)
Start from the kinematic requirement that *some* scattering angle \(\theta\) exists with \(|\cos\theta|\le 1\):
$$
\Delta E_{ij} = q v\cos\theta - \frac{q^2}{2m_\chi}
\le qv - \frac{q^2}{2m_\chi}.
$$

Solve for \(v\):
$$
qv \ge \Delta E_{ij} + \frac{q^2}{2m_\chi}
\;\Rightarrow\;
v \ge \frac{\Delta E_{ij}}{q} + \frac{q}{2m_\chi}.
$$

So
$$
v_{\min}^{ij}(q)=\frac{\Delta E_{ij}}{q}+\frac{q}{2m_\chi}.
$$

---

## 10. Define the “velocity integral” \(\eta(v_{\min})\) (paper Eq. 7)
They package the integral over DM speeds above threshold into
$$
\eta\!\left(v_{\min}^{ij}\right)
=
\int \frac{4\pi v^2\,dv}{v}\; g_\chi(v)\;
\Theta\!\left(v - v_{\min}^{ij}(q)\right).
$$

You can read \(\eta\) as: “how much DM flux is available *above* the speed needed to make excitation \(i\to j\) at momentum transfer \(q\)”.

---

## 11. Main result: derive the expected detectable signal rate \(R_{\rm sig}\) (paper Eq. 9)

### Step 1: Insert Eq. (3) into Eq. (5)
$$
R_{\rm scatter}
=
\sum_{i,j}
N_{\rm LAB}^e\frac{\rho_\chi}{m_\chi}
\int d^3\vec v\; g_\chi(\vec v)\;
\int \frac{d^3\vec q}{(2\pi)^3}\,(2\pi)\,\delta(\Delta E_{ij}-\omega)\,
\frac{|\mathcal{M}_{\rm free}|^2\,|f_{ij}(\vec q)|^2}{16\,m_\chi^2\,m_e^2}.
$$

### Step 2: Replace amplitude using Eq. (4)
$$
R_{\rm scatter}
=
\sum_{i,j}
N_{\rm LAB}^e\frac{\rho_\chi}{m_\chi}
\int d^3\vec v\; g_\chi(\vec v)\;
\int \frac{d^3\vec q}{(2\pi)^3}\,(2\pi)\,\delta(\Delta E_{ij}-\omega)\,
\left(\frac{\pi\bar\sigma_e}{\mu_{\chi e}^2}F_{\rm DM}^2(q)\right)\,
|f_{ij}(\vec q)|^2.
$$

### Step 3: Do the angular part of the \(\delta\)-function integral
Use
$$
\omega = qv\cos\theta - \frac{q^2}{2m_\chi}.
$$

The delta function fixes \(\cos\theta\) to the value that makes \(\Delta E_{ij}=\omega\).
Integrating over angles gives a factor proportional to \(1/(qv)\) and a threshold condition \(v\ge v_{\min}^{ij}(q)\). This produces the \(\eta(v_{\min})\) defined above and leaves a \(1/q\) factor inside the \(q\)-integral.

### Step 4: Collect constants → the paper’s compact form
After that integration, the paper writes the detectable *single-hit* signal rate as
$$
R_{\rm sig}
=
\xi\;
\frac{N_{\rm LAB}^e\,\rho_\chi\,\bar\sigma_e}{8\pi\,m_\chi\,\mu_{\chi e}^2}
\sum_{i,j}
\int \frac{d^3\vec q}{q}\;
\eta\!\left(v_{\min}^{ij}(q)\right)\;
F_{\rm DM}^2(q)\;
|f_{ij}(\vec q)|^2.
$$

This is the “DM signal rate” equation you asked about.

---

## 12. Detector-to-hit efficiency factor \(\xi\) (paper Eq. 10)
Not every excitation becomes a recorded PMT hit; they model it as
$$
\xi = Q \times X \times Y.
$$

- \(Q\): fluorescence quantum yield (fraction of excitations producing a photon that survives as light),
- \(X\): PMT coverage fraction of detector surface,
- \(Y\): PMT quantum efficiency integrated over the emitted spectrum (probability photon → PMT hit).

---

## 13. Annual modulation signal model (paper Eq. 11)
They model the time-dependent DM signal rate as a known sinusoid:
$$
S(t) = \frac{S_{\rm tot}}{T}\left[1 + f_{\rm mod}\cos\!\left(\frac{2\pi t}{1\,{\rm yr}}-\frac{\pi}{2}\right)\right].
$$

- \(S_{\rm tot}\): total DM counts in observation time \(T\),
- \(f_{\rm mod}\): fractional modulation amplitude (order ~0.1).

Total observed counts are modeled as
$$
N(t) = B(t) + S(t),
$$
where \(B(t)\) is the (large) background PMT dark-rate contribution.

---

## 14. Why modulation helps: “extract the small DM signal from huge background”
If the background is approximately constant over a year, then:
- the *modulated* DM component has amplitude \(\sim S_{\rm tot} f_{\rm mod}\),
- the counting noise from background is \(\sim \sqrt{B_{\rm tot}}\).

A simple 95% C.L. (≈2σ) requirement is:
$$
S_{\rm tot} f_{\rm mod} \gtrsim 2\sqrt{B_{\rm tot}}
\quad\Rightarrow\quad
S_{\rm tot} \gtrsim \frac{2\sqrt{B_{\rm tot}}}{f_{\rm mod}}.
$$

This captures the logic of the paper’s sensitivity estimate.

---

## 15. What to remember (minimal mental model)
- The hard part for sub-GeV DM is depositing enough energy.
- Bound electrons + molecular structure (the form factor \(f_{ij}\)) can strongly enhance excitation probability.
- Neutrino observatories have *enormous mass*, but also *enormous noise*.
- Annual modulation gives a clean “template” to pull out a tiny DM signal from a huge background.
