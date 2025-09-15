
The **Synthetic Galaxy Distance (SGD)** is a metric designed to evaluate the realism of generated galaxy images by comparing **distributions of physical features** between real and generated datasets.  
Unlike pixel-level losses, SGD focuses on **observable galaxy properties**.

---

## Features Used

- **Aperture flux**  
  - Total light measured within a fixed circular aperture.  
  - Proxy for *brightness* as in observational photometry.  

- **Half-light radius (\(R_e\))**  
  - Radius that encloses half of the total light of the galaxy.  
  - Proxy for *size*.  

- *(If multi-band data is available, features like colours \(g-r\), \(r-z\) are also used.)*

---

## Wasserstein Distance (Earth Mover’s Distance)

For two 1D distributions \(P\) and \(Q\), the **Wasserstein-1 distance** is:

\[
W(P, Q) \;=\; \int_{-\infty}^{\infty} \big| F_P(x) - F_Q(x) \big| \, dx
\]

where \(F_P(x)\) and \(F_Q(x)\) are the cumulative distribution functions (CDFs).  

- **Intuition**: Imagine \(P\) as a pile of dirt and \(Q\) as a hole.  
  The Wasserstein distance is the minimum "work" needed to move dirt into the hole,  
  where work = (mass moved) × (distance).  
- Larger \(W(P,Q)\) = more mismatch between distributions.

---

## Empirical CDFs in Galaxy Context

For a feature \(f\) (e.g., flux, \(R_e\)) measured from each galaxy:

- **Real dataset CDF**:
\[
F_\text{real}(x) \;=\; \frac{1}{N} \sum_{i=1}^N \mathbf{1}\!\left(f^{(r)}_i \leq x\right)
\]

- **Generated dataset CDF**:
\[
F_\text{gen}(x) \;=\; \frac{1}{M} \sum_{j=1}^M \mathbf{1}\!\left(f^{(g)}_j \leq x\right)
\]

where \(\mathbf{1}(\cdot)\) is the indicator function.

The Wasserstein distance \(W(f)\) is then the **area between these two CDFs**.

---

## Synthetic Galaxy Distance (SGD)

The total SGD is the sum of Wasserstein distances across all chosen features:

\[
\text{SGD} \;=\; \sum_{f \in \{\text{flux}, R_e, \ldots\}} W\!\big(P_\text{real}(f), P_\text{gen}(f)\big)
\]

---

## Interpretation

- **Low SGD**  
  Generated galaxies closely follow the distributions of real galaxies in brightness and size.  

- **High SGD**  
  Generated galaxies deviate, e.g. systematically too faint, too bright, too small, or too large.  

- **Baseline (truth vs. truth)**  
  Expected minimum SGD due to sampling variance; useful for calibration.  

---

## Key Insight

SGD is powerful because it **compares physically meaningful quantities** (brightness, size) rather than raw pixels.  
It captures whether the **population statistics** of generated galaxies resemble those of the real universe.

