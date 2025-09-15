
**Other Names:** Annealing, Path Sampling

**Primary Goal:** To calculate the [[Bayesian Evidence (Z)]], a quantity that standard [[Markov Chain Monte Carlo (MCMC)]] methods are not designed to find.

**Core Concept:** Thermodynamic Integration (TI) is a robust but computationally intensive MCMC-based method for calculating the evidence. It works by creating a continuous "path" between two distributions: a simple one where the evidence is known, and the complex target distribution where it is not. By integrating the change along this path, it finds the final evidence value.

> **Analogy: The Geologist's Method for Measuring a Mountain's Volume**
> Imagine you have a special altimeter that cannot measure absolute altitude, but can perfectly measure any *change* in altitude. To find the height of a mountain, you start at a known point (sea level, altitude = 0), walk a path to the peak, and sum up (integrate) all the small changes your altimeter recorded along the way.
> - **Sea Level (Known Start):** The Prior Distribution.
> - **Mountain Peak (Unknown End):** The Posterior Distribution.
> - **The Path:** The "annealing schedule" controlled by `λ`.
> - **The Special Altimeter:** The MCMC sampler measuring `<ln(L)>` at each step.

### The Mathematical Framework

TI constructs a "powered-up" posterior distribution, `P_λ`, controlled by an "inverse temperature" parameter `λ`:

`P_λ ∝ L(θ)^λ * π(θ)`

-   **When `λ = 0` (Infinite Temperature):** The distribution is `P₀ ∝ L⁰ * π = π`. This is just the **prior distribution**. Its evidence `Z₀` is 1 by definition, so `ln(Z₀) = 0`. This is our known starting point, our "sea level".
-   **When `λ = 1` (Unit Temperature):** The distribution is `P₁ ∝ L¹ * π`. This is the true **posterior distribution**. Its evidence `Z₁` is the `Z` we want to find.

The core formula of TI connects the final `ln(Z)` to an integral over `λ`:

**`ln(Z) = ∫₀¹ <ln(L)>_λ dλ`**

Where `<ln(L)>_λ` is the **average of the log-likelihood**, with the average taken over many samples drawn from the distribution `P_λ`.

### The Algorithm in Practice

1.  **Define an Annealing Schedule:** Choose a series of `λ` values between 0 and 1 (e.g., `λ = 0.1, 0.2, 0.3, ...`).
2.  **Run MCMC at each Temperature:** For each `λ` in the schedule:
    a. Run a long [[Markov Chain Monte Carlo (MCMC)]] simulation targeting the distribution `P_λ`.
    b. Collect thousands of samples `θ` from this chain.
    c. For each sample, calculate its log-likelihood `ln(L(θ))`.
    d. Compute the average of all these `ln(L)` values to get `<ln(L)>_λ`. This gives one point on the curve to be integrated.
3.  **Integrate:** Use a numerical method (like the trapezium rule) to calculate the area under the curve of `<ln(L)>_λ` versus `λ`. This final area is the estimate for `ln(Z)`.

### Costs and Benefits

-   **Benefit:** It is extremely robust and considered a "gold standard" for evidence calculation when implemented carefully.
-   **Cost:** It is **extremely** computationally expensive. It requires running many long MCMC chains, making it at least an order of magnitude more costly than a single [[Parameter Estimation]] run. Each chain produces samples that are only used to calculate a single average value and are then discarded.