
These are powerful post-processing (or in-run) features of MultiNest that provide deeper insights into multi-modal posteriors (posteriors with multiple peaks).

### Mode Identification

This is the process of automatically finding and separating the distinct solutions (peaks) in the posterior distribution.

> **Analogy:** If your posterior is a mountain range, this process gives you the coordinates of each individual peak.

MultiNest performs this dynamically during the run. At each step, it checks if the ellipsoids bounding the live points are physically connected. If they separate into two or more disconnected sets, a **"split"** is declared, and the algorithm begins tracking them as separate modes. This creates a "family tree" of modes.

### Local Evidence (`Z_mode`)

This is the [[Bayesian Evidence (Z)]] calculated for a single, specific mode.

> **Analogy:** If the global evidence `Z` is the volume of the entire mountain range, the local evidence `Z_mode` is the volume of a **single, individual mountain**.

This allows you to calculate a Bayes Factor between different solutions *within the same model*, quantifying which solution is more probable given the data.

#### Calculation

The local evidence is calculated by redistributing the evidence from "ancestor" groups to their final "descendant" modes. When a group splits, the evidence is divided among the children in proportion to the number of live points each child group received at the moment of the split. This ensures that the sum of all local evidences equals the global evidence.```