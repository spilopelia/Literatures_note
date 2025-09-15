
The Bayesian Evidence, also called the *marginalized likelihood*, is the central quantity in [[Model Selection]]. It is the denominator in Bayes' Theorem, `P(D|H)`.

`Z = ∫ L(θ) * π(θ) dθ`

> **Analogy:** If the posterior distribution (`L * π`) is a mountain range, the Evidence (`Z`) is the total **volume** of the entire range.

### Interpretation

The Evidence represents the average likelihood of a model over its entire prior parameter space. It answers the question: **"How well does this model, as a whole, predict the data we actually observed?"**

A high evidence value means the model provides a good, natural explanation for the data without requiring fine-tuning. This is why it acts as a mathematical formulation of **Ockham's Razor**, penalizing overly complex models.

### The Challenge: Calculation

Calculating this multi-dimensional integral is the single hardest numerical task in Bayesian inference. Two main approaches are:
1.  **[[Thermodynamic Integration]]**: The traditional, brute-force method.
2.  **[[Nested Sampling]]**: The elegant, efficient method used by MultiNest.

### Working with `ln(Z)`

In practice, we almost always work with the natural logarithm of the evidence, `ln(Z)`. This is for three key reasons:
1.  **Numerical Stability:** The likelihood `L` can be an astronomically small number, causing computer "underflow." Working with logs turns products into sums, keeping the numbers manageable.
2.  **Algorithmic Convenience:** Both TI and Nested Sampling are naturally constructed to calculate `ln(Z)`.
3.  **Interpretive Scale:** Comparing models by subtracting log-evidences (`ln(Z₁) - ln(Z₂)`) is more intuitive and aligns with scales like the Jeffreys scale.