## 1. Motivation
- Diffusion models (score-based priors) are widely used for **inverse problems**, recovering clean data \(x_0\) from measurements \(y = A(x_0) + \text{noise}\).
- Standard reverse SDE/ODE posterior sampling tightly couples each step to the previous.  
  → **Early errors propagate** and cannot be corrected.  
- This is especially harmful in **nonlinear inverse problems** (e.g. phase retrieval).

---

## 2. Core Idea of DAPS
**DAPS = Decoupled Annealing Posterior Sampling**

- **Decoupling:** The update from \(t' \to t\) does not constrain \(x_t\) to be a small perturbation of \(x_{t'}\).  
- **Annealing:** The marginals \(p(x_t \mid y)\) still converge gradually to the true posterior \(p(x_0 \mid y)\) as \(t \to 0\).  
- Effect: Larger corrections are possible → better exploration and error recovery.

---

## 3. Framework

### 3.1 Key recursion (Proposition 1)
If

$$
x_{t'} \sim p(x_{t'} \mid y),
$$

then sample

$$
x_0 \sim p(x_0 \mid x_{t'}, y),
\quad
x_t \sim p(x_t \mid x_0),
$$

to obtain

$$
x_t \sim p(x_t \mid y).
$$

---

### 3.2 Sampling \(x_0 \mid x_{t'}, y\)

General Langevin dynamics (Eq. 6):

$$
x_0^{(j+1)} = x_0^{(j)} 
+ \eta \, \nabla_{x_0} \log p(x_0 \mid x_{t'}, y)
+ \sqrt{2\eta} \, \epsilon_j,
$$

where

$$
\nabla_{x_0} \log p(x_0 \mid x_{t'}, y)
= \nabla_{x_0} \log p(y \mid x_0) + \nabla_{x_0} \log p(x_0 \mid x_{t'}).
$$

---

### 3.3 Bayes’ rule decomposition
From Bayes:

$$
p(x_0 \mid y, x_{t'}) \propto p(y \mid x_0, x_{t'}) \, p(x_0 \mid x_{t'}).
$$

Using conditional independence \(y \perp x_{t'} \mid x_0\):

$$
p(x_0 \mid y, x_{t'}) \propto p(y \mid x_0) \, p(x_0 \mid x_{t'}).
$$

Thus the gradient separates into:

1. **Likelihood gradient:** \( \nabla_{x_0} \log p(y \mid x_0) \)  
2. **Bridge prior gradient:** \( \nabla_{x_0} \log p(x_0 \mid x_{t'}) \)

---

## 4. Gaussian Measurement Noise (Eq. 7)

Assume

$$
y = A(x_0) + \varepsilon, \quad \varepsilon \sim \mathcal{N}(0, \sigma_y^2 I).
$$

- Likelihood gradient:

$$
\nabla_{x_0} \log p(y \mid x_0) 
= -\tfrac{1}{\sigma_y^2} A^\top (A(x_0) - y).
$$

- Prior gradient (Gaussian approximation  
\(p(x_0 \mid x_{t'}) \approx \mathcal{N}(\hat{x}_0(x_{t'}), \sigma_{t'}^2 I)\)):

$$
\nabla_{x_0} \log p(x_0 \mid x_{t'}) 
= -\tfrac{1}{\sigma_{t'}^2}(x_0 - \hat{x}_0(x_{t'})).
$$

### Simplified Langevin update (Eq. 7)

$$
x_0^{(j+1)} = x_0^{(j)} 
+ \eta \Big[
-\tfrac{1}{\sigma_y^2} A^\top(A(x_0^{(j)}) - y)
-\tfrac{1}{\sigma_{t'}^2}(x_0^{(j)} - \hat{x}_0(x_{t'}))
\Big]
+ \sqrt{2\eta}\, \epsilon_j.
$$

---

## 5. Role of the ODE Solver

### 5.1 Probability Flow ODE
The diffusion model admits a **probability flow ODE**:

$$
dx = \Big[f(x,t) - \tfrac{1}{2} g(t)^2 \nabla_x \log p_t(x)\Big] dt.
$$

- Solving this ODE deterministically maps a noisy latent \(x_{t'}\) to a clean prediction \(\hat{x}_0\).  
- This gives the **mean** of the Gaussian bridge:

$$
p(x_0 \mid x_{t'}) \approx \mathcal{N}(\hat{x}_0(x_{t'}), \sigma_{t'}^2 I).
$$

### 5.2 Why multiple steps?
- The ODE defines a continuous trajectory from \(t'\) to \(0\).  
- Computing \(\hat{x}_0\) requires solving

$$
\hat{x}_0 = x_{t'} + \int_{t'}^0 \Big[f(x,t) - \tfrac{1}{2} g(t)^2 \nabla_x \log p_t(x)\Big] dt.
$$

- This integral has no closed form → must use **numerical ODE solvers** (Euler, Heun, Runge–Kutta, DDIM).  
- The solver discretizes the interval \([t',0]\) into multiple sub-steps, each requiring a score model call.

### 5.3 Trade-off
- **Few ODE steps:** fast, but less accurate estimate of \(\hat{x}_0\).  
- **More ODE steps:** slower, but \(\hat{x}_0\) is more faithful to the diffusion prior.  
- DAPS needs far fewer steps than full reverse diffusion (hundreds), but still >1 step for stable integration.

### 5.4 Contrast with standard reverse diffusion
- **Standard reverse SDE/ODE:** many small backward steps from \(x_T \to x_0\), each with score calls.  
- **DAPS:** at each noise level \(t'\), use an ODE solver (with a modest number of steps) to jump directly to \(\hat{x}_0\), then refine via MCMC.

---

## 6. Role of MCMC Samplers

- **Langevin Dynamics:**  
  Gradient-based sampler with Gaussian noise injection. Efficient under Gaussian assumptions.  

- **Hamiltonian Monte Carlo (HMC):**  
  Introduces auxiliary momentum \(p\) and defines a Hamiltonian:

  $$
  H(x_0, p) = U(x_0) + K(p),
  $$

  where  
  - Potential energy: \( U(x_0) = -\log p(x_0 \mid x_{t'}, y) \)  
  - Kinetic energy: \( K(p) = \tfrac{1}{2} p^\top M^{-1} p \)

  Simulate Hamiltonian dynamics:

  $$
  \frac{dx_0}{dt} = \frac{\partial H}{\partial p} = M^{-1} p,
  \quad
  \frac{dp}{dt} = -\frac{\partial H}{\partial x_0} = \nabla_{x_0} \log p(x_0 \mid x_{t'}, y).
  $$

  → Propose new states \((x_0', p')\) that travel further in parameter space, reducing random-walk behavior.  

- **Metropolis–Hastings (MH):**  
  Accept–reject correction step:  

  $$
  \alpha = \min\!\Bigg(1, \frac{p(y \mid x_0') p(x_0' \mid x_{t'}) \, q(x_0 \mid x_0')}
  {p(y \mid x_0) p(x_0 \mid x_{t'}) \, q(x_0' \mid x_0)} \Bigg).
  $$

  Guarantees correct stationary distribution.  

### Why MH works without gradients
- MH only requires **evaluating the posterior density**, not its gradient.  
- For nonlinear or non-differentiable forward models \(A(x_0)\), computing  
  \(\nabla_{x_0} \log p(y \mid x_0)\) may be infeasible.  
- But MH still works as long as you can compute likelihood values \(p(y \mid x_0)\).  
- Therefore, MH is functional in **gradient-intractable settings** where Langevin/HMC cannot be used.

---

## 7. Algorithmic Steps

Pseudocode outline for DAPS:

```python
# Input: measurement y, forward model A, pretrained diffusion score model
# Noise schedule: {t_N ... t_0}

x_t = sample_initial_prior(t_N)   # start from prior (Gaussian noise)

for t' in reversed(noise_schedule):  # iterate down noise levels
    # 1. ODE solver: map x_t' → hat{x}_0
    x0_hat = solve_probability_flow_ode(x_t, t', 0)

    # 2. MCMC step: sample x0 ~ p(x0 | x_t', y)
    x0 = run_mcmc(x0_hat, y, t', sampler="Langevin/HMC/MH")

    # 3. Re-noise: sample x_t ~ p(x_t | x0)
    x_t = add_noise(x0, sigma_t)

# Final estimate at t=0
return x0
