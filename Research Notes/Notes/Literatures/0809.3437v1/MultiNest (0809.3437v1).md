# Detailed Notes on MultiNest Paper (Feroz et al. 2008)

**Full Title:** MULTINEST: an efficient and robust Bayesian inference tool for cosmology and particle physics
**Authors:** F. Feroz, M.P. Hobson, M. Bridges
**arXiv:** [0809.3437](https://arxiv.org/abs/0809.3437)

---

## Section 1: Introduction

This section sets the stage by outlining the state of [[Bayesian Inference]] in physics and cosmology.

-   **Two Categories of Bayesian Inference:**
    1.  **[[Parameter Estimation]]**: Typically done with [[Markov Chain Monte Carlo (MCMC)]].
    2.  **[[Model Selection]]**: Requires calculating the [[Bayesian Evidence (Z)]].

-   **Problems with Existing Methods:**
    -   **MCMC for Parameter Estimation:**
        -   Computationally intensive.
        -   Struggles with multi-modal posteriors (multiple peaks).
        -   Struggles with curving degeneracies (long, thin "banana" shapes).
        -   Requires careful tuning of proposal distribution.
        -   Convergence can be difficult to diagnose.
    -   **MCMC for Model Selection ([[Thermodynamic Integration]]):**
        -   **Even more** computationally expensive than parameter estimation (often >10x).
        -   This high cost has hindered the widespread adoption of Bayesian model selection.

-   **Introduction to [[Nested Sampling]] (Skilling 2004):**
    -   Presents Nested Sampling as a Monte Carlo method specifically targeted at the efficient calculation of the Evidence.
    -   Crucially, it also produces posterior inferences as a **by-product**.
    -   Previous work showed it requires far fewer likelihood evaluations (~100x less) than [[Thermodynamic Integration]].

-   **Contribution of this Paper:**
    -   Presents further development and the first public release of the **MultiNest** algorithm.
    -   Builds upon previous work (Feroz & Hobson 2008, FH08) to improve efficiency and robustness.
    -   Introduces fundamental changes to the ellipsoidal sampling method.
    -   Naturally identifies individual modes and allows for the calculation of [[remote-repo/Research Notes/Notes/Literatures/0809.3437v1/Mode Identification & Local Evidence|'local' evidence]] for each mode.

---

## Section 2: Bayesian Inference

This section provides the mathematical foundation.

-   **Bayes' Theorem (Eq. 1):**
    -   `Posterior = (Likelihood * Prior) / Evidence`
    -   Defines the key terms: Posterior `P(θ)`, Likelihood `L(θ)`, Prior `π(θ)`, and Evidence `Z`.

-   **Parameter Estimation:**
    -   Focuses on the **Posterior**.
    -   The Evidence `Z` is just a normalization constant and is usually ignored.
    -   Inferences are made by sampling from the unnormalized posterior `L(θ) * π(θ)`.

-   **Model Selection:**
    -   Focuses on the **Evidence `Z`**.
    -   `Z = ∫ L(θ) * π(θ) dθ` (Eq. 2).
    -   The evidence is the average of the likelihood over the prior.
    -   **Occam's Razor:** The evidence automatically penalizes more complicated models unless they are significantly better at explaining the data.
    -   Models are compared using the **Bayes Factor**: `B₁₀ = Z₁ / Z₀` (Eq. 3).

---

## Section 3: Nested Sampling

This section explains the core theoretical framework that MultiNest implements.

-   **The Core Idea:** Transform the multi-dimensional evidence integral (Eq. 2) into a one-dimensional integral.
-   **Prior Volume `X` (Eq. 4):**
    -   `X(λ)` is defined as the integral of the prior `π(θ)` over the region where the likelihood `L(θ)` is greater than some threshold `λ`.
    -   This is the "area of the islands" from our analogy.
-   **The Master Equation (Eq. 5):**
    -   The evidence integral is rewritten as `Z = ∫₀¹ L(X) dX`.
    -   This is a 1D integral that is much easier to solve numerically. `L(X)` is the inverse of `X(λ)`.
-   **The Numerical Algorithm:**
    -   The integral is approximated as a weighted sum `Z = Σ Lᵢ * wᵢ` (Eq. 7).
    -   **Live Points:** Start with `N` "active" or "live" points drawn from the prior.
    -   **Iteration:**
        1.  Find the point with the lowest likelihood `Lᵢ` in the active set.
        2.  Remove this point (it becomes "inactive").
        3.  Replace it with a new point drawn from the prior, subject to the hard constraint that its likelihood must be `L > Lᵢ`.
    -   **Prior Volume Shrinkage:** The prior volume `X` is estimated to shrink at each step `i` as `Xᵢ ≈ exp(-i/N)`.
    -   **Termination:** Stop when the maximum possible remaining evidence contribution is below a specified tolerance.
    -   **Posterior Samples (Eq. 9):** The full set of inactive ("dead") points can be used to reconstruct the posterior. Each point `j` is assigned a weight `pⱼ = (Lⱼ * wⱼ) / Z`.

---

## Section 4: Ellipsoidal Nested Sampling

This section discusses the critical implementation challenge: how to efficiently draw new samples that satisfy the `L > Lᵢ` constraint.

-   **The Challenge:** Naively drawing from the full prior is incredibly inefficient as the high-likelihood region becomes very small.
-   **The Solution:** Approximate the iso-likelihood contour `L = Lᵢ` with a bounding shape.
    -   **Uni-modal Case:** Use a single N-dimensional ellipsoid determined from the covariance of the active points.
    -   **Multi-modal Case (The Innovation):**
        -   Identify distinct clusters of active points.
        -   Construct a separate, individual ellipsoid bound around **each cluster**.
        -   This significantly increases sampling efficiency for multi-modal problems (as illustrated in Fig. 2).

---

## Section 5: The MultiNest Algorithm (The Details)

This is the core of the paper, detailing the specific improvements and methods that define MultiNest.

### 5.1 Unit Hypercube Sampling Space

-   **[[The Unit Hypercube Trick]]**: A crucial transformation. MultiNest does not work in the "physical" parameter space.
-   It maps the problem to an N-dimensional **unit hypercube** where each parameter runs from 0 to 1.
-   The transformation uses the inverse CDF of the prior for each parameter (Eq. 13 for separable priors, Eq. 14-15 for the general non-separable case).
-   **Benefit:** The algorithm's internal workings (partitioning, ellipsoid construction) are performed in a simple, standardized, uniform space, making them much more robust and efficient. The "physics" is cleanly separated from the sampling.

### 5.2 Partitioning and Construction of Ellipsoidal Bounds

-   This is the "engine room," explaining *how* the clusters and ellipsoids are made.
-   It uses an **Expectation-Maximization (EM)** approach to find the optimal ellipsoidal decomposition of the active points.
-   The algorithm recursively partitions point sets, optimizing a function `F(S)` (Eq. 18) that balances the number of ellipsoids and their total volume.
-   The metric used for assigning points to clusters is a **weighted Mahalanobis distance** (Eq. 22), which accounts for the volume of each ellipsoid.
-   This process is more robust and flexible than the previous methods in FH08, capable of handling complex shapes like a torus (Fig. 3).

### 5.3 Sampling from Overlapping Ellipsoids

-   Once the ellipsoids are constructed, a new point is drawn by:
    1.  Choosing an ellipsoid with probability proportional to its volume (Eq. 23).
    2.  Drawing a point uniformly from within that ellipsoid.
    3.  **Overlap Correction:** Checking how many ellipsoids (`nₑ`) the new point falls into. The point is then accepted with a probability of `1/nₑ`. This ensures the final sample is drawn uniformly from the *union* of all ellipsoids.

### 5.6 Identification of Modes

-   This section describes the dynamic, in-run method for identifying separate modes.
-   **The Test:** At each iteration, the algorithm checks if the set of ellipsoids bounding the active points is **fully connected**. It does this by checking for physical intersections between ellipsoids.
-   **A Split:** If the ellipsoids form two or more disconnected sets, a "split" is declared. The original "parent" group becomes inactive, and two or more new "child" active groups are created.
-   **Family Tree:** This process creates a hierarchy of groups (illustrated in Fig. 4). At the end of the run, each final, unsplit active group is promoted to a "mode".

### 5.7 Evaluating 'Local' Evidences

-   Describes the robust method for calculating the evidence of each individual mode found in 5.6.
-   **The Problem:** The simple approach of just summing the `L*w` of points in a final mode underestimates the evidence. It ignores the contribution of "ancestor" points from before the mode split off.
-   **The Solution: Share the Inheritance.**
    -   The evidence from inactive "parent" groups is retrospectively partitioned among its "descendant" modes.
    -   The fraction of evidence a child inherits from a parent is proportional to the number of active points it received at the moment of the split (Eq. 27-28).
    -   This ensures that the sum of all local evidences equals the global evidence (`Σ Zₗ = Z`, Eq. 30).

---

## Section 6 & 7: Applications

This section demonstrates the algorithm's performance on toy problems and a real-world cosmological problem.

-   **Toy Model 1: Egg-box Likelihood (Fig. 5):**
    -   A highly multi-modal problem.
    -   Demonstrates that MultiNest correctly identifies all the modes and calculates their local evidences accurately (Table 1).
-   **Toy Model 2: Gaussian Shells (Fig. 6):**
    -   A problem with pronounced curving degeneracies ("rings").
    -   Shows that MultiNest is orders of magnitude more efficient than the previous FH08 algorithm, especially in high dimensions (Table 3).
-   **Cosmological Application (Sec. 7):**
    -   Analyzes extensions to the standard ΛCDM model.
    -   Finds that MultiNest produces reliable parameter constraints (Fig. 9) and evidence values (Table 5) on similar timescales to standard MCMC methods, but with the added benefit of providing the evidence for "free".

---

## Section 8: Discussion and Conclusions

-   **Summary of Achievements:** MultiNest is an efficient, robust, and publicly available tool that produces reliable evidence estimates and posterior inferences, even for challenging distributions.
-   **Guide for Users:**
    -   **`N_live`:** Should be large enough to find all modes. `N > D` (dimensionality) is a hard requirement. For cosmology, `N=400` for evidence and `N=50` for parameter estimation worked well.
    -   **`e` (efficiency):** For evidence evaluation, `e ~ 0.3` is recommended. For quick parameter estimation, `e = 1.0` is faster.