
Model selection is the process of using data to compare two or more competing hypotheses or models (`H1`, `H2`, ...). In the Bayesian framework, this is achieved by comparing the [[Bayesian Evidence (Z)]] for each model.

The key tool for comparison is the **Bayes Factor**, `B₁₂`:

`B₁₂ = Z₁ / Z₂ = P(D|H₁) / P(D|H₂)`

The Bayes Factor is the ratio of the evidences for two models. It quantifies how much more probable one model is than another, given the data.

### Interpreting the Bayes Factor

The **Jeffreys Scale** provides a common rule of thumb for interpretation:

| `ln(B₁₂)`      | Strength of Evidence for H1 |
|----------------|-----------------------------|
| `< 1.0`        | Inconclusive                |
| `1.0 to 2.5`   | Weak                        |
| `2.5 to 5.0`   | Moderate                    |
| `> 5.0`        | Strong                      |

A key feature of Bayesian model selection is that it naturally incorporates **Ockham's Razor**. The [[Bayesian Evidence (Z)]] automatically penalizes overly complex models that require fine-tuning to fit the data.