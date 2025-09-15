
Nested Sampling is an elegant and efficient algorithm for calculating the [[Bayesian Evidence (Z)]]. It is the theoretical framework behind [[The MultiNest Algorithm]].

> **Analogy:** The "CAT Scanner Method". You leave the mountain as it is and take a series of horizontal slices at different altitudes (`L`). By summing up the volume of each slice (`Area * Thickness`), you can reconstruct the total volume of the mountain.

### The Mathematical Transformation

Nested Sampling's key innovation is to transform the complex, multi-dimensional integral for `Z` over parameters `θ` into a simple, one-dimensional integral over the **Prior Mass `X`**.

-   **Prior Mass `X(λ)`:** The fraction of the total prior volume where the likelihood is greater than a threshold `λ`. This is the "area of the dry islands" when flooding the landscape to a water level `λ`.
-   **The Master Equation:** `Z = ∫₀¹ L(X) dX`
    -   `L(X)` is the likelihood contour that encloses a prior mass `X`.

### The Algorithm

1.  **Initialization:** Scatter `N` "live points" randomly from the prior.
2.  **Iteration:**
    a. Find the live point with the lowest likelihood, `L_worst`.
    b. Add its contribution `L_worst * w` to the total Evidence `Z`.
    c. Remove the "worst" point (it is now "dead").
    d. Find a new replacement point by sampling from the prior, but with the critical constraint that its likelihood must be `L_new > L_worst`.
3.  **Termination:** Stop when the remaining contribution to `Z` is negligible.

### The "Two-for-One" Benefit

Nested Sampling is incredibly powerful because the collection of "dead" points generated during the run is not waste. They form a perfectly weighted set of samples from the posterior distribution. This means it solves for both the **Evidence** and the **Posterior** simultaneously.