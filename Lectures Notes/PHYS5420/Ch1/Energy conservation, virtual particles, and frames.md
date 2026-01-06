
## Does the slide imply energy is not strictly conserved because of time–energy uncertainty?
No. In quantum field theory (QFT), **energy–momentum is conserved exactly** at every interaction vertex and for the full process.  
The slide’s “borrow energy for a short time” is a **heuristic** used to build intuition about **short-lived intermediate states** and the **range** of forces, not a literal breaking of conservation.

---

## On-shell vs off-shell (what “off-shell” means)

### On-shell (real particle)
A **real (free, detectable)** particle must satisfy the mass–energy relation:

$$
E^2 = p^2c^2 + m^2c^4 .
$$

Equivalently, in 4-vector form:

$$
p^\mu p_\mu = m^2 c^2 .
$$

“On-shell” means the particle’s energy and momentum lie on this “mass shell.”

### Off-shell (virtual particle)
An **off-shell** momentum does **not** satisfy the free-particle relation:

$$
p^\mu p_\mu \neq m^2 c^2
\quad\Longleftrightarrow\quad
E^2 - p^2c^2 \neq m^2c^4 .
$$

---

## Why virtual particles don’t have to satisfy the relation

- **Virtual particles are not real, free particles.** They are **internal lines** in Feynman diagrams—pieces of the calculation representing intermediate field propagation.
- **Only external (incoming/outgoing) particles are on-shell**, because those are prepared/detected as real states.
- **Internal momenta are integrated over** in the amplitude, so they are not constrained to lie on the mass shell.

A typical propagator factor (schematic) is:

$$
\frac{i}{q^2 - m^2 + i\varepsilon},
$$

where the internal 4-momentum $$q^\mu$$ is generally **off-shell**.

**Important:** off-shell does *not* mean energy conservation fails.  
Energy–momentum is still conserved at vertices:

$$
\sum p^\mu_{\text{in}} = \sum p^\mu_{\text{out}} .
$$

---

## “Why introduce virtual particles if they violate laws?”
They don’t violate conservation laws.

- The relation $$E^2 = p^2c^2 + m^2c^4$$ is **not** a conservation law.
- It is the **dispersion relation for a free real particle**.
- Virtual particles are not free real particles, so they do not need to obey the on-shell condition.

Virtual particles are mainly:
- **bookkeeping** for perturbation theory,
- and a useful intuition for **force mediation** and **propagators**.

---

## Explain-like-I’m-five summary

- A **real particle** is like a ball you can throw and catch; it must follow the “ball rule”:

$$
E^2 = p^2c^2 + m^2c^4 .
$$

- A **virtual particle** is like a quick “push” during a high-five—useful to describe what happened, but you can’t catch it by itself.  
  Because you can’t measure it as a standalone free particle, it doesn’t have to follow the “ball rule.”
- **The real law** (“what goes in equals what comes out”) is still true:

$$
\sum p^\mu_{\text{in}} = \sum p^\mu_{\text{out}} .
$$

---

## Does energy always conserve in a non-inertial frame?
Not always in the simple “this number stays constant” sense.

### What is always true (local conservation)
Physics enforces **local** conservation of energy–momentum (special relativity form):

$$
\partial_\mu T^{\mu\nu} = 0 .
$$

In general relativity, the corresponding statement is:

$$
\nabla_\mu T^{\mu\nu} = 0 .
$$

### Global “total energy conserved” depends on the frame/symmetry
- In an **inertial frame** with time-translation symmetry (time-independent laws), an isolated system typically has a conserved total energy.
- In a **non-inertial frame** (accelerating/rotating), you introduce **fictitious forces**; the “energy” of just the particles can appear to change unless you include the work/energy exchange associated with the accelerating frame (or the agent driving the acceleration).

**Rule of thumb:**  
Energy conservation as a constant-of-motion is tied to **time-translation symmetry**; non-inertial frames generally obscure that symmetry, so naive mechanical energy need not be conserved.

---
