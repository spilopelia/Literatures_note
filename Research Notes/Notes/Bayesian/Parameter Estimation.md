
Parameter estimation is the process of inferring the values of a model's parameters (`θ`) after observing some data (`D`). In a Bayesian context, the goal is not to find a single "best-fit" value, but to determine the entire **posterior probability distribution**, `P(θ|D, H)`.

> **Analogy:** The posterior is a topographic map of a mountain range. Parameter estimation is the process of creating this map.

The posterior distribution tells you everything you want to know:
-   **Best-Fit Values:** The location of the highest peak(s) of the distribution.
-   **Uncertainties:** The width and shape of the peak(s), often quoted as confidence intervals or "error bars".
-   **Correlations:** The orientation of the peaks, revealing how changing one parameter affects the plausible values of others.

The traditional method for performing parameter estimation is [[Markov Chain Monte Carlo (MCMC)]].