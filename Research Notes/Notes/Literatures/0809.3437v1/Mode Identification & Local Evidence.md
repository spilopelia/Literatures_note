
These are advanced features of the [[The MultiNest Algorithm]] that provide a much deeper physical insight into the results, especially for complex problems. They address what to do when the posterior distribution is **multi-modal** (i.e., has multiple distinct peaks or solutions).

> **Analogy:** If your posterior is a mountain range, these features don't just give you the total volume of the range; they give you a list of every individual mountain, its exact location, and its individual volume.

---

## Mode Identification

**Goal:** To automatically find and separate all the distinct peaks (modes) in the posterior distribution.

#### The MultiNest Method (Dynamic Identification)

MultiNest performs mode identification **during the sampling run**, not as a post-processing step. This makes it more robust and efficient.

1.  **The Test:** At each iteration, the algorithm has a set of ellipsoids that bound the `N_live` active points. The core test is to check if this set of ellipsoids is **geometrically connected**.
2.  **Connectivity Check:** The algorithm starts with one ellipsoid and uses an exact intersection algorithm to find all other ellipsoids it touches. It then repeats this for the newly found ellipsoids, forming a "chain reaction".
3.  **The Split:** If this chain reaction stops before all ellipsoids have been included, it means the active points have separated into at least two physically disconnected regions. A "split" is declared.
4.  **Creating a Family Tree:** When a group of points `G_parent` splits, it becomes **inactive**. The disconnected sets of ellipsoids form new, separate **active groups** (`G_child1`, `G_child2`, ...). This process can happen recursively, creating a family tree of groups (see Fig. 4 of the paper).
5.  **Final Modes:** At the end of the run, every group that is still "active" (i.e., it never split) is promoted to a **mode**.

---

## Local Evidence (`Z_mode`)

**Goal:** To calculate the [[Bayesian Evidence (Z)]] for each individual mode that was identified. This allows for a quantitative comparison of the different solutions found by the model.

#### The Problem with a Simple Sum

A naive approach would be to sum the `L*w` contributions only for the points that end up in a given mode. This is flawed because it ignores the evidence contributed by "ancestor" points from before the mode split off from its parent, leading to a severe underestimation.

#### The MultiNest Solution: Share the Inheritance

MultiNest solves this by retrospectively partitioning the evidence from the inactive "ancestor" groups among their final "descendant" modes.

1.  **The New Formula:**
    `Z_l = (Evidence from mode l's own points) + (A fraction `α` of the evidence from its ancestor points)`

2.  **Calculating the Inheritance Fraction (`α`):**
    The fraction is determined by the "size" of the child groups at the exact moment of the split. "Size" is measured by the number of active points `n(A)`.
    -   When a parent group `G_parent` splits into child groups `G_child1`, `G_child2`, etc., the fraction of the parent's evidence inherited by `G_child1` is:
        `fraction = n(A)_child1 / n(A)_parent`
    -   This is applied recursively up the family tree to calculate the total inheritance from all ancestors.

### The Final Output

For each mode, MultiNest provides:
-   **Local log-evidence `ln(Z_mode)`:** Allows you to calculate the Bayes Factor *between solutions*.
-   **Mean parameter values:** The location of that specific peak.
-   **Parameter covariances:** The size and shape of that specific peak (the uncertainties for that solution).
-   **Posterior Mass:** The fraction of the total posterior probability contained within that mode.