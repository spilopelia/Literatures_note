
## 0. Setup and notation
- \(z\): complex variable.
- \(\zeta\): fixed point (often inside a closed contour).
- \(\gamma\): a closed contour (positively oriented) in the complex plane.
- “Inside \(\gamma\)” means the region enclosed by \(\gamma\).

---

## 1. Analytic functions (the “nice” functions)
**Analytic on and inside \(\gamma\)** means \(f(z)\) is complex differentiable everywhere in that region (no blow-ups, no singular points).

### Cauchy’s Theorem (closed integral is zero)
If \(f\) is analytic on and inside \(\gamma\), then
$$
\oint_\gamma f(z)\,dz = 0.
$$
**Interpretation:** A closed contour integral can only be nonzero if the integrand has singularities inside the loop.

---

## 2. Poles and “order of a pole”
A function has a **pole of order \(n\)** at \(z=\zeta\) if near \(\zeta\)
$$
f(z)=\frac{g(z)}{(z-\zeta)^n},
$$
where \(g\) is analytic near \(\zeta\) and \(g(\zeta)\neq 0\).

- Order 1: **simple pole** \(\sim 1/(z-\zeta)\)
- Order 2: **double pole** \(\sim 1/(z-\zeta)^2\)
- etc.

---

## 3. Key contour integrals around \(\zeta\)
Let \(\gamma\) wind once around \(\zeta\).

### (A) The special one
$$
\oint_\gamma \frac{dz}{z-\zeta} = 2\pi i.
$$

### (B) Higher powers vanish
For \(n\ge 2\),
$$
\oint_\gamma \frac{dz}{(z-\zeta)^n} = 0.
$$

**Intuition:** Parameterize a circle \(z-\zeta=re^{i\theta}\). The integrand gains a factor \(e^{i(1-n)\theta}\) which oscillates and cancels over \([0,2\pi]\). Only the \(n=1\) case does not oscillate.

---

## 4. Laurent expansion and why only the \((z-\zeta)^{-1}\) term matters
Near an isolated singularity \(\zeta\), a function can be written as a Laurent series:
$$
f(z)=\frac{b_N}{(z-\zeta)^N}+\cdots+\frac{b_2}{(z-\zeta)^2}+\frac{b_1}{z-\zeta}+P(z),
$$
where \(P(z)\) is analytic near \(\zeta\).

### Residue
The coefficient of \((z-\zeta)^{-1}\) is the **residue**:
$$
\operatorname{Res}(f,\zeta)=b_1.
$$

### Why the contour integral “picks out” \(b_1\)
Integrating term-by-term:
- \(\oint P(z)\,dz=0\) (Cauchy’s theorem; analytic part)
- \(\oint (z-\zeta)^{-n} dz = 0\) for \(n\ge 2\)
- \(\oint (z-\zeta)^{-1} dz = 2\pi i\)

So
$$
\oint_\gamma f(z)\,dz = 2\pi i\, b_1 = 2\pi i\,\operatorname{Res}(f,\zeta).
$$

---

## 5. Residue Theorem
If \(f\) is analytic on and inside \(\gamma\) except for isolated singularities \(\{\zeta_k\}\) inside \(\gamma\), then
$$
\oint_\gamma f(z)\,dz = 2\pi i \sum_k \operatorname{Res}(f,\zeta_k).
$$

**Connection to “closed integral is zero”:**
- If there are **no** singularities inside, the sum is empty \(\Rightarrow 0\).
- Nonzero integrals come **only** from singularities (via residues).

---

## 6. Cauchy Integral Formula (CIF)
Assume \(f\) is analytic on and inside \(\gamma\), and \(\zeta\) is inside \(\gamma\). Then
$$
f(\zeta)=\frac{1}{2\pi i}\oint_\gamma \frac{f(z)}{z-\zeta}\,dz.
$$

### Where the singularity is
- In CIF, **\(f\) has no singularity at \(\zeta\)**.
- The integrand \(\frac{f(z)}{z-\zeta}\) has a **simple pole at \(z=\zeta\)** due to the denominator.

### CIF as a special case of the residue theorem
Let
$$
g(z)=\frac{f(z)}{z-\zeta}.
$$
Then \(g\) has a simple pole at \(\zeta\) with residue:
$$
\operatorname{Res}(g,\zeta)=\lim_{z\to\zeta}(z-\zeta)\frac{f(z)}{z-\zeta}=f(\zeta).
$$
Residue theorem gives
$$
\oint_\gamma \frac{f(z)}{z-\zeta}\,dz = 2\pi i\,f(\zeta),
$$
which rearranges to CIF.

---

## 7. CIF connected directly to “closed integral is zero”
Define
$$
h(z)=\frac{f(z)-f(\zeta)}{z-\zeta}.
$$
Even though it looks singular, \(h(z)\) is actually analytic at \(z=\zeta\) (removable singularity), so \(h\) is analytic on and inside \(\gamma\). Then
$$
\oint_\gamma h(z)\,dz=0.
$$
Expand:
$$
0=\oint_\gamma \frac{f(z)}{z-\zeta}\,dz - f(\zeta)\oint_\gamma \frac{1}{z-\zeta}\,dz.
$$
Using \(\oint_\gamma \frac{dz}{z-\zeta}=2\pi i\), you get
$$
\oint_\gamma \frac{f(z)}{z-\zeta}\,dz = 2\pi i\,f(\zeta),
$$
i.e. CIF.

---

## 8. Derivative version (useful extension)
For \(n\ge 0\),
$$
f^{(n)}(\zeta)=\frac{n!}{2\pi i}\oint_\gamma \frac{f(z)}{(z-\zeta)^{n+1}}\,dz.
$$

---

## 9. One-line big picture
- **Cauchy’s theorem:** analytic inside \(\Rightarrow\) closed integral \(=0\).
- **Residue theorem:** if not analytic (poles inside), integral \(=2\pi i\) times sum of residues.
- **Cauchy integral formula:** residue theorem applied to \(\frac{f(z)}{z-\zeta}\), where the residue is \(f(\zeta)\).
