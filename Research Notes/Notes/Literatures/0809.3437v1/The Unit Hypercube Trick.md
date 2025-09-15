
This is a crucial technical detail that makes [[The MultiNest Algorithm]] robust and general. MultiNest **never works in the physical parameter space**. It transforms the entire problem into a simple, standardized space called the **unit hypercube**.

A unit hypercube is an N-dimensional cube where each axis runs from 0 to 1.

### Why is this useful?

The physical parameter space can be very messy:
-   Parameters can have vastly different scales (e.g., 0-1 vs 50-100).
-   Priors can be complex (Uniform, Gaussian, Log-uniform, etc.).

The unit hypercube is a clean, simple, standardized "workbench":
-   Every parameter is on the same 0-1 scale.
-   The prior is, by definition, uniform in this space.
-   The geometry is simple, making the ellipsoidal bounding much easier and more stable.

### The Transformation

The mapping from the hypercube (`u`) to the physical space (`θ`) is done using the **inverse Cumulative Distribution Function (CDF)** of the prior for each parameter.

-   **MultiNest's Job:** Lives entirely in the hypercube, generating new points `u_new`.
-   **User's Job:** Provides a function that takes `u_new`, transforms it into physical parameters `θ_new` using the inverse CDFs, calculates the likelihood `L(θ_new)`, and returns `L` to MultiNest.

This method can even handle complex, **non-separable priors** (where parameters are correlated) by using a sequence of conditional transformations.```

