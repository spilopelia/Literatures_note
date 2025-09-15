
MultiNest is a specific, highly efficient implementation of the [[Nested Sampling]] framework. Its main innovation is how it solves the most difficult step of Nested Sampling: finding a new point with `L > L_worst`.

### The Core Innovation: Ellipsoidal Bounding

Instead of searching the entire parameter space for a valid new point (which is hugely inefficient), MultiNest uses a "divide and conquer" strategy.

1.  **Clustering / Partitioning:** At each step, it takes the current set of `N_live` points and runs a clustering algorithm to see if they form one or more distinct groups ("modes").
2.  **Ellipsoidal Bounding:** It draws a tight-fitting, N-dimensional ellipsoid around each identified cluster. This creates one or more tiny, targeted search regions.
3.  **Sampling:** It then draws a new random point from within one of these small ellipsoids. This point has a very high probability of satisfying the `L > L_worst` constraint.

This method makes MultiNest extremely fast and robust, especially for multi-modal posteriors, as it can track and sample from all peaks simultaneously.

### Key User Parameters

-   `N_live`: Number of live points. A trade-off between accuracy (high `N_live`) and speed (low `N_live`).
-   `tol`: The desired accuracy on the final `ln(Z)` value. Controls when the algorithm stops.
-   `efr`: The sampling efficiency. Controls the balance between evidence accuracy and posterior sample quality.