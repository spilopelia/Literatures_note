## 1. The Cosmic Ray Transport Equation

Cosmic rays are not static; they propagate through the galaxy, interact, and decay. Their evolution is described by a transport equation.

### Key Processes in Propagation

The "full" propagation equation for a cosmic ray species `ψ` includes several terms:
$$
\frac{\partial\psi(\vec{r}, p, t)}{\partial t} = q(\vec{r}, p, t) + \vec{\nabla} \cdot (D_{xx}\vec{\nabla}\psi - \vec{V}\psi) + \frac{\partial}{\partial p} \left[ p^2 D_{pp} \frac{\partial}{\partial p} \frac{\psi}{p^2} \right] - \frac{\partial}{\partial p} \left[ \dot{p}\psi - \frac{p}{3}(\vec{\nabla}\cdot\vec{V})\psi \right] - \frac{1}{\tau_f}\psi - \frac{1}{\tau_r}\psi
$$

Our conversation focused on two key **loss terms**:

#### a) Fragmentation Loss
This describes the loss of a cosmic ray species `i` when it collides with the Interstellar Medium (ISM) and breaks apart into a lighter species `j`.

- **Loss Equation:**
  $$
  \frac{\partial n_i}{\partial t} = - n_i \left( \frac{\rho}{m} \right)_{\text{ISM}} \sigma_{i \to j} v
  $$
- **Term Breakdown:**
    - `n_i`: Number density of the cosmic ray species `i`. The more you have, the more can be lost.
    - `(ρ/m)_ISM`: Number density of target particles in the ISM (e.g., hydrogen atoms).
    - `σ_{i→j}`: The **fragmentation cross-section**. This is the effective "area" for an interaction that turns species `i` into `j`. It represents the probability of the interaction occurring.
    - `v`: The velocity of the cosmic ray. Faster particles sweep through more of the ISM per unit time, increasing the interaction rate.
    - **The negative sign** signifies that this is a **loss** term; the population of species `i` is decreasing.

#### b) Radioactive Decay Loss
For unstable isotopes, this term describes their decay.
- **Loss Equation:**
  $$
  \frac{\partial n_i}{\partial t} = - \frac{n_i}{\tau_i}
  $$
  - `τ_i`: The lifetime of the particle. For relativistic particles, this lifetime is Lorentz-boosted: `τ(E) = γτ₀`.

### The Leaky-Box Approximation
To simplify the complex transport equation, we use the **leaky-box model**. This model assumes cosmic rays are confined within a "box" (the galaxy) and have a certain probability of escaping.

- **Simplification**: The spatial diffusion term (`D∇²n_i`) is replaced by a simple escape term: `-n_i / T_e`, where `T_e` is the average escape time.
- **Resulting Equation**: For a purely secondary species (source term `Q=0`) in a steady state (`∂n_i/∂t = 0`), the equation becomes:
  $$
  \frac{n_i}{T_e} = - \frac{n_i}{T_f} - \frac{n_i}{T_{\text{dec}}} + C_i
  $$
  - `T_f`: Characteristic fragmentation (destruction) time.
  - `T_dec`: Characteristic decay time.
  - `C_i`: A source term representing the *creation* of species `i` from the fragmentation or decay of heavier species `j`.

---
## 2. Probing Propagation with Secondary Ratios (In-Depth)

The ratios of secondary to primary cosmic rays are our most powerful tools for understanding how cosmic rays travel through the galaxy. By measuring these ratios, we can deduce key propagation parameters.

### a) Radioactive Clocks: The ¹⁰Be/⁹Be Ratio and Derivation

The ratio of a radioactive isotope (`¹⁰Be`) to a stable one (`⁹Be`) allows us to measure the cosmic ray **residence time**.

**Derivation:**
We start with the simplified leaky-box equation for the number density `n` of each species:

1.  **For stable ⁹Be:** The only loss terms are escape (`T_e`) and fragmentation (`T_f`). In steady state, production equals loss.
    $$
    C_{^{9}\text{Be}} = n_{^{9}\text{Be}} \left( \frac{1}{T_e} + \frac{1}{T_f} \right) = \frac{n_{^{9}\text{Be}}}{T_{e+f}}
    $$

2.  **For radioactive ¹⁰Be:** We have an additional loss term for radioactive decay (`T_dec`).
    $$
    C_{^{10}\text{Be}} = n_{^{10}\text{Be}} \left( \frac{1}{T_e} + \frac{1}{T_f} + \frac{1}{T_{dec}} \right) = n_{^{10}\text{Be}} \left( \frac{1}{T_{e+f}} + \frac{1}{T_{dec}} \right)
    $$

3.  **Solving for the ratio `n(¹⁰Be) / n(⁹Be)`:** We can rearrange the equations and divide them:
    $$
    \frac{n_{^{10}\text{Be}}}{n_{^{9}\text{Be}}} = \left( \frac{C_{^{10}\text{Be}}}{C_{^{9}\text{Be}}} \right) \frac{1/T_{e+f}}{1/T_{e+f} + 1/T_{dec}}
    $$
    - The term `C(¹⁰Be)/C(⁹Be)` is, to a good approximation, the ratio of their production cross-sections from heavier nuclei.

**Physical Interpretation (The "Clock"):**

-   **High-Energy Limit**: At high energies, the particle's velocity is near `c`, so the Lorentz factor `γ` is large. The decay lifetime in the lab frame (`T_dec = γτ₀`) becomes very long. Thus, `1/T_dec → 0`. The isotope doesn't have time to decay before escaping. The ratio simplifies to the production ratio:
    $$
    \frac{n_{^{10}\text{Be}}}{n_{^{9}\text{Be}}} \approx \frac{C_{^{10}\text{Be}}}{C_{^{9}\text{Be}}}
    $$
-   **Low-Energy Limit**: At lower energies, `T_dec` is comparable to the propagation time `T_{e+f}`. The `1/T_dec` term is significant and suppresses the ratio. By measuring this suppression (as seen in the plot on slide 11), we can solve for `T_{e+f}`, which gives us the cosmic ray residence time of **~10⁷ years**.

### b) Secondary-to-Primary Ratios: The B/C Ratio and Derivation

This ratio is the "gold standard" for measuring the energy dependence of cosmic ray diffusion.

**Derivation:**
We start with the leaky-box equation for Boron (B), which is stable (`T_dec → ∞`) and mainly produced from Carbon (C).

1.  **Steady-state equation for Boron:**
    $$
    \frac{n_B}{T_e} = -\frac{n_B}{T_f} + C_B
    $$
2.  **The source term `C_B`** is dominated by Carbon fragmentation:
    $$
    C_B \approx n_C \cdot n_{ISM} \cdot \sigma_{C \to B} \cdot v
    $$
3.  **Substituting and solving for the B/C ratio:**
    $$
    n_B \left(\frac{1}{T_e} + \frac{1}{T_f}\right) = n_C \cdot n_{ISM} \cdot \sigma_{C \to B} \cdot v \quad \implies \quad \frac{n_B}{n_C} = \frac{n_{ISM} \cdot \sigma_{C \to B} \cdot v}{1/T_e + 1/T_f}
    $$

**Physical Interpretation (Energy Dependence):**

-   **Fragmentation Dominated (Low Energy)**: Here, `1/T_f >> 1/T_e`. The denominator is approximately `1/T_f`. Since `1/T_f = n_{ISM} \cdot \sigma_{B \to X} \cdot v`, the `n_ISM` and `v` terms cancel, leaving the B/C ratio as a simple ratio of nuclear cross-sections, which is nearly energy-independent.
-   **Escape Dominated (High Energy)**: Here, `1/T_e >> 1/T_f`. The denominator is approximately `1/T_e`. The ratio becomes:
    $$
    \frac{n_B}{n_C} \approx n_{ISM} \cdot \sigma_{C \to B} \cdot v \cdot T_e(E)
    $$
    Since propagation models predict `T_e(E) ∝ E^-δ`, the B/C ratio directly traces this falling energy dependence.

### c) Grammage and its Relation to B/C

Grammage `X(E)` simplifies propagation by combining density and time into a single, observable-linked quantity.

**Derivation:**

1.  **Definition of Grammage**: The total matter traversed is $$X(E) = ρ_ISM \cdot c \cdot T_e(E)$$`. Note that `$$ρ_{ISM} = m \cdot n_{ISM}$$`, where `m` is the average mass of an ISM particle.
2.  **Connecting to B/C Ratio**: We take the high-energy (escape-dominated) B/C ratio:
    $$
    \frac{n_B}{n_C} \approx (n_{ISM} \cdot \sigma_{C \to B} \cdot c) \cdot T_e(E)
    $$
3.  **Substitute `n_ISM = ρ_ISM / m`**:
    $$
    \frac{n_B}{n_C} \approx \left(\frac{\rho_{ISM}}{m} \cdot \sigma_{C \to B} \cdot c\right) \cdot T_e(E) = \frac{\sigma_{C \to B}}{m} \left( \rho_{ISM} \cdot c \cdot T_e(E) \right) = \frac{\sigma_{C \to B}}{m} X(E)
    $$
This shows that the B/C ratio is directly proportional to the grammage `X(E)`. By measuring B/C, we directly measure the amount of "stuff" cosmic rays have passed through.

---

## 3. Antimatter Secondaries (In-Depth)

Antimatter particles are clean secondary messengers, as they are not expected to be produced by primary astrophysical sources.

### a) Antiproton Production and Threshold Energy Derivation

Antiprotons are produced in high-energy collisions. The minimum energy required is called the threshold energy.

**Derivation of the Threshold:**
We analyze the reaction `p + p → p + p + p + p̄` in a relativistically invariant way.

1.  **Define the Mandelstam variable `s`**: `s` is the square of the total four-momentum, which is the same in all reference frames. `s = (p₁ + p₂)²`.
2.  **Calculate `s` in the Lab Frame**: A cosmic ray proton (`p₁`) hits a stationary ISM proton (`p₂`).
    - `p₁ = (E_lab, \vec{p})`
    - `p₂ = (m_p, 0)`
    - `s = p₁² + p₂² + 2p₁·p₂ = m_p² + m_p² + 2(E_lab \cdot m_p - \vec{p} \cdot 0) = \mathbf{2m_p² + 2m_p E_{lab}}`
3.  **Calculate `s` at Threshold in the Center-of-Mass (CM) Frame**: At the minimum energy (threshold), all four final particles are created at rest in the CM frame.
    - Total final rest mass = `m_p + m_p + m_p + m_p̄ = 4m_p`.
    - The total energy in the CM frame is `√s_thr = 4m_p`, so `s_thr = \mathbf{16m_p²}`.
4.  **Equate the two expressions for `s`**:
    $$
    16m_p² = 2m_p² + 2m_p E_{lab} \quad \implies \quad 14m_p² = 2m_p E_{lab} \quad \implies \quad E_{lab} = 7m_p
    $$
5.  **Find the Kinetic Energy Threshold**: The total energy `E_lab` includes rest mass energy. The kinetic energy `T` is `T = E - m`.
    $$
    T_{thr} = E_{lab} - m_p = 7m_p - m_p = \mathbf{6m_p} \approx 5.6 \, \text{GeV}
    $$

## Problem 2 — Threshold Energy for \( \bar{p} \) Production

Consider the reaction:

$$
p + p \rightarrow p + p + p + \bar{p}.
$$

Baryon number conservation requires producing a \( p\bar{p} \) pair in addition to the two initial protons, so the **lightest final state** has four nucleons.

We work in the **lab frame**, where one proton (mass \( m_p \)) is at rest and the other is the beam proton.

The Mandelstam variable \( s \) is:

$$
s = (p_1 + p_2)^2 = m_p^2 + m_p^2 + 2 m_p E_{\text{lab}}
= 2m_p^2 + 2m_pE_{\text{lab}}.
$$

At **threshold**, all final particles are produced at rest in the center-of-mass frame, so:

$$
\sqrt{s_{\text{thr}}} = 4 m_p
\quad \Rightarrow \quad
s_{\text{thr}} = 16 m_p^2.
$$

Equating the two gives:

$$
16m_p^2 = 2m_p^2 + 2m_p E_{\text{lab}}
\quad \Rightarrow \quad
E_{\text{lab}} = 7 m_p.
$$

Hence, the **threshold kinetic energy** of the beam proton is:

$$
T_{\text{thr}} = E_{\text{lab}} - m_p = 6 m_p
\approx 6 \times 938~\text{MeV} \approx 5.6~\text{GeV}.
$$

✅ **Result:**

$$
\boxed{T_{\text{thr}} = 5.6~\text{GeV}}
$$

---

## Problem 3 — Maximum Energy of the Antiproton at Fixed \( \sqrt{s} \)

At a given center-of-mass energy \( \sqrt{s} \), the **maximum energy of the antiproton** occurs when the other three protons move together with minimal internal excitation.  
Their total invariant mass is then:

$$
M_{\text{cl}} = 3 m_p.
$$

We can treat the final state effectively as a **two-body system**:

$$
\sqrt{s} \to \bar{p} \ (m_1 = m_p) + \text{cluster} \ (m_2 = 3m_p).
$$

For a general two-body final state in the CM frame:

$$
E_1 = \frac{s + m_1^2 - m_2^2}{2\sqrt{s}}.
$$

Substituting \( m_1 = m_p \) and \( m_2 = 3m_p \):

$$
E_{\bar{p}}^{\max} = \frac{s + m_p^2 - (3m_p)^2}{2\sqrt{s}}
= \frac{s - 8m_p^2}{2\sqrt{s}}.
$$

The corresponding momentum is:

$$
p_{\bar{p}}^{\max} = \sqrt{(E_{\bar{p}}^{\max})^2 - m_p^2}.
$$

✅ **Result:**

$$
\boxed{
E_{\bar{p}}^{\max} = \frac{s - 8m_p^2}{2\sqrt{s}}
}
$$

### b) The Role of the Differential Cross Section

The simple leaky-box model tells us the *total* number of antiprotons produced, but not their energies. To predict the antiproton *spectrum*, we need the **differential cross section**.

- **Concept**: The differential cross section, `dσ/dT_p̄`, gives the probability of producing an antiproton with a specific kinetic energy `T_p̄` from an incoming proton of energy `E_p`.
- **The Source Term Integral (from Slide 38)**: To find the number of antiprotons at a given energy `T_p̄`, we must sum the contributions from *all* primary protons with enough energy to create them. This is done with an integral:
  $$
  n_{\bar{p}}(T_{\bar{p}}) = \left( \int_{E_{th}}^\infty n_p(E_p) \frac{d\sigma_{pp \to \bar{p}X}}{dT_{\bar{p}}}(E_p, T_{\bar{p}}) dE_p - \text{loss term} \right) \frac{X}{m}
  $$
- **Explanation**: This formula calculates the source of antiprotons at energy `T_p̄` by integrating the primary proton flux `n_p(E_p)` weighted by the probability `dσ/dT_p̄` that a proton of energy `E_p` will produce an antiproton of energy `T_p̄`.

### c) Coalescence Momentum and Antinuclei Production

Antinuclei (like antideuterons, `d̄`) are formed when antiprotons and antineutrons, created in the same interaction, are close enough in phase space to bind.

- **The Coalescence Picture**: This is a phenomenological model used to estimate the production rate of antinuclei.
- **Coalescence Momentum `p₀`**: This is the key parameter. The model assumes that a `p̄` and an `n̄` will coalesce into a `d̄` if and only if their relative momentum is less than `p₀`.
  $$
  |\vec{p}_{\bar{p}} - \vec{p}_{\bar{n}}| < p_0
  $$
- **The Coalescence Formula (from Slide 42)**: The production rate of antideuterons is proportional to the product of the production rates of antiprotons and antineutrons, scaled by a factor related to `p₀`.
  $$
  \gamma_{\bar{d}}\frac{d^3N_{\bar{d}}}{dp_{\bar{d}}^3} \propto \frac{4\pi}{3}p_0^3 \left(\gamma_{\bar{p}}\frac{d^3N_{\bar{p}}}{dp_{\bar{p}}^3}\right) \left(\gamma_{\bar{n}}\frac{d^3N_{\bar{n}}}{dp_{\bar{n}}^3}\right)
  $$
- **Interpretation**: The term `(4π/3)p₀³` represents the **volume of a sphere in momentum space**. It quantifies the "target volume" for coalescence. A larger `p₀` means a larger volume, making coalescence more probable. Since `p₀` is small (`~100 MeV/c`), this probability is very low, which is why antinuclei are extremely rare. `p₀` is not calculated from theory but is a **fitting parameter**, tuned to match data from particle accelerator experiments.