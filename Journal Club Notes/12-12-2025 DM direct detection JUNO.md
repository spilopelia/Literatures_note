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

## 13. DM sensitivity from annual modulation (expanded)

### 13.1 What quantity is being fit in the data?
You bin the detector’s **total PMT hit rate** into time bins (the paper takes daily bins). Let the observed number of hits in bin \(i\) be

$$
n_i
$$

and the **expected mean** number of hits in that bin be

$$
\lambda_i
$$

A standard assumption for counting data is Poisson statistics:

$$
n_i \sim \mathrm{Poisson}(\lambda_i)
$$

with variance approximately

$$
\mathrm{Var}(n_i) \simeq \lambda_i
$$

Because the PMT dark rate is enormous, \(\lambda_i\) is dominated by background.

---

### 13.2 Signal + background decomposition
Write the expected counts as “background + DM signal”:

$$
\lambda_i = \left[B(t_i) + S(t_i)\right]\Delta t
$$

where
- \(B(t)\) is the background hit rate (dominated by PMT dark rate),
- \(S(t)\) is the DM-induced hit rate,
- \(\Delta t\) is the bin width (e.g., 1 day),
- \(t_i\) is the time at the center of bin \(i\).

---

### 13.3 What is “annual modulation” physically?
The DM scattering rate depends on the Earth’s speed through the DM halo. Over a year, Earth’s speed changes slightly due to its orbit, which changes the DM scattering rate slightly. The paper estimates the modulation by evaluating the scattering rate (from the signal-rate formula earlier) at four representative dates:
- baseline around March 2 and September 2,
- increased Earth speed by about \(+15\ \mathrm{km/s}\) around June 2,
- decreased Earth speed by about \(-15\ \mathrm{km/s}\) around December 2.

From these, define a modulation fraction by comparing the maximum and minimum rates:

$$
f_{\mathrm{mod}} \equiv \frac{R_{\max}-R_{\min}}{R_{\max}+R_{\min}}
$$

with

$$
R_{\max} = R(v_E + \Delta v),\qquad R_{\min} = R(v_E - \Delta v),\qquad \Delta v \simeq 15\ \mathrm{km/s}
$$

Important qualitative point: near threshold (lighter DM), only the fast tail of the DM velocity distribution contributes, so a small change in Earth speed changes the rate more strongly, making \(f_{\mathrm{mod}}\) larger.

---

### 13.4 The DM signal model used for fitting (paper Eq. 11)
Let the **total number of DM signal counts** accumulated over the full observation time \(T\) be

$$
S_{\mathrm{tot}}
$$

Then the average signal rate is

$$
\frac{S_{\mathrm{tot}}}{T}
$$

The paper models the time dependence as a sinusoid with known period and phase:

$$
S(t) = \frac{S_{\mathrm{tot}}}{T}\left[1 + f_{\mathrm{mod}}\cos\left(\frac{2\pi t}{1\ \mathrm{yr}}-\frac{\pi}{2}\right)\right]
$$

They choose the phase so that (by their convention) the signal is higher during the first half-year after March 2 and lower in the second half-year.

Equivalent “same shape” rewriting (using \(\cos(x-\pi/2)=\sin(x)\)):

$$
S(t) = \frac{S_{\mathrm{tot}}}{T}\left[1 + f_{\mathrm{mod}}\sin\left(\frac{2\pi t}{1\ \mathrm{yr}}\right)\right]
$$

This form is often easier to interpret: the signal rate oscillates once per year with fractional amplitude \(f_{\mathrm{mod}}\).

---

### 13.5 How this connects to the “only total hit rate is observable”
Neutrino analyses usually build events from correlated multi-PMT activity. Here, DM scatters are too small to form events, so the analysis uses only the scalar time series:

$$
N(t) = B(t) + S(t)
$$

and searches for the known sinusoidal component in \(N(t)\).

---

## 14. Why modulation gives sensitivity (expanded)

### 14.1 Simplest background model: constant dark rate
Start with the idealized case:

$$
B(t) = \frac{B_{\mathrm{tot}}}{T}
$$

where \(B_{\mathrm{tot}}\) is the total number of background counts over the time \(T\).

Then

$$
N(t) = \frac{B_{\mathrm{tot}}}{T} + \frac{S_{\mathrm{tot}}}{T}\left[1 + f_{\mathrm{mod}}\cos\left(\frac{2\pi t}{1\ \mathrm{yr}}-\frac{\pi}{2}\right)\right]
$$

The constant parts are hard to use because the absolute background level is not known precisely. The trick is to use only the **modulated** piece, which has a known template (period and phase fixed).

---

### 14.2 What is the “modulated signal size” in counts?
From the signal model, the oscillating (time-varying) part has amplitude in *rate*:

$$
\frac{S_{\mathrm{tot}}}{T} f_{\mathrm{mod}}
$$

Over the full time series, the paper treats the effective amplitude in *counts* as

$$
S_{\mathrm{tot}} f_{\mathrm{mod}}
$$

This is the piece you are trying to pull out of the total counts.

---

### 14.3 What is the statistical uncertainty from the background?
If the background dominates, the counting noise is controlled by the total background counts. For Poisson counting, the typical size of fluctuations is

$$
\sigma_B \simeq \sqrt{B_{\mathrm{tot}}}
$$

This sets the scale of how well you can measure any small modulation on top of the background, before worrying about systematics.

---

### 14.4 The paper’s 95% C.L. sensitivity estimate (their “back-of-the-envelope”)
They require the modulated DM counts to be about \(2\sigma\) above background fluctuations:

$$
S_{\mathrm{tot}} f_{\mathrm{mod}} \gtrsim 2\sqrt{B_{\mathrm{tot}}}
$$

Solve for the minimum detectable total signal counts:

$$
S_{\mathrm{tot}} \gtrsim \frac{2\sqrt{B_{\mathrm{tot}}}}{f_{\mathrm{mod}}}
$$

Because they find \(f_{\mathrm{mod}}\sim 0.1\) (with mass dependence), this becomes roughly

$$
S_{\mathrm{tot}} \sim 20\sqrt{B_{\mathrm{tot}}}
$$

Interpretation: you cannot beat the huge background in absolute level, but you can still detect a small DM contribution if it carries a known yearly “fingerprint”.

---

### 14.5 Convert that into a required signal *rate*
Define total rates:

$$
R_{\mathrm{sig}} \equiv \frac{S_{\mathrm{tot}}}{T},\qquad R_{\mathrm{bkg}} \equiv \frac{B_{\mathrm{tot}}}{T}
$$

Then the condition becomes

$$
R_{\mathrm{sig}} \gtrsim \frac{2}{f_{\mathrm{mod}}}\sqrt{\frac{R_{\mathrm{bkg}}}{T}}
$$

So the minimum detectable signal rate improves slowly with observation time:

$$
R_{\mathrm{sig}} \propto \frac{1}{\sqrt{T}}
$$

---

### 14.6 How this becomes a limit on the DM–electron cross section
Earlier in the note, the predicted DM signal rate scales linearly with the reference cross section:

$$
R_{\mathrm{sig}} \propto \bar{\sigma}_e
$$

So the sensitivity estimate implies a cross-section reach that scales like

$$
\bar{\sigma}_e^{\mathrm{lim}} \propto \frac{1}{f_{\mathrm{mod}}}\sqrt{\frac{B_{\mathrm{tot}}}{T}}
$$

This is why a large modulation fraction helps: larger \(f_{\mathrm{mod}}\) means you need fewer total DM counts to reach the same significance.

---

### 14.7 What changes in real data (why the Supplemental Material exists)
In reality, \(B(t)\) is not perfectly constant: there are secular drifts and possibly backgrounds that also modulate annually (temperature-driven PMT noise, radon, muons, solar neutrino seasonal variation, reactor cycles, etc.).

A generic “fit model” for the expected counts per bin (from the paper’s Supplemental Material) can be written schematically as:

$$
\lambda_i = N\left(1+\delta_{\mathrm{PMT}}+\alpha\cos(\omega t_i)+\sum_k \beta_k\left(1+\delta_k\right)\cos(\omega t_i+\phi_k)\right)
$$

where:
- \(N\) is the dominant mean counts per bin,
- \(\delta_{\mathrm{PMT}}\) is a (systematic) fractional uncertainty on the flat background level,
- \(\alpha\) encodes the DM modulation strength relative to the dominant rate,
- the sum allows additional modulating backgrounds \(k\) with amplitudes \(\beta_k\), phases \(\phi_k\), and systematic uncertainties \(\delta_k\).

Even if backgrounds modulate, many have phases shifted by weeks–months relative to the DM phase, which helps disentangle them when fitting multiple sinusoidal components.

---

## 15. What to remember (minimal mental model)
- The hard part for sub-GeV DM is depositing enough energy.
- Bound electrons + molecular structure (the form factor \(f_{ij}\)) can strongly enhance excitation probability.
- Neutrino observatories have *enormous mass*, but also *enormous noise*.
- Annual modulation gives a clean “template” to pull out a tiny DM signal from a huge background.
