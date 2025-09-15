
Bayesian inference is a statistical method based on **Bayes' Theorem**. Its core idea is the formalization of learning: we start with an initial belief (a **prior**), gather new data (the **likelihood**), and update our belief based on that data to arrive at a final, more informed conclusion (a **posterior**).

### Bayes' Theorem

The central equation is:

`P(θ|D, H) = [ P(D|θ, H) * P(θ|H) ] / P(D|H)`

-   **`P(θ|D, H)` (The Posterior):** Our final belief. The probability of the parameters `θ` *given* the data `D` and the model `H`.
-   **`P(D|θ, H)` (The Likelihood):** The information from the data. The probability of observing the data `D` if the parameters were `θ`.
-   **`P(θ|H)` (The Prior):** Our initial belief. The probability of the parameters `θ` *before* seeing the data.
-   **`P(D|H)` (The Evidence):** The normalization constant. Also known as the [[Bayesian Evidence (Z)]].

### The Two Goals of Bayesian Inference

1.  **[[Parameter Estimation]]**: Working within a single model (`H`), what are the most plausible values and uncertainties for its parameters (`θ`)? This involves mapping out the **Posterior**.
2.  **[[Model Selection]]**: Given the data, which of several competing models (`H1` vs `H2`) is the best explanation? This involves calculating and comparing the **Evidence** for each model.