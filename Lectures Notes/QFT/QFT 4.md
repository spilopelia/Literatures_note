## 1) Discrete KG field = many coupled oscillators

Field on a 1D lattice: sites \(n\), spacing \(a\), field value \(\Phi_n(t)\).

**Lagrangian**
$$
L=\frac{a}{2}\sum_n (\partial_t\Phi_n)^2-\frac12\sum_{n,n'}K_{nn'}\,\Phi_n\Phi_{n'} .
$$

- First term: kinetic (time-variation).
- Second term: potential/couplings (springs + mass term encoded by \(K_{nn'}\)).

**Canonical momentum**
$$
\Pi_n \equiv \frac{\delta L}{\delta(\partial_t\Phi_n)}=a\,\partial_t\Phi_n .
$$

**Hamiltonian**
$$
H=\sum_n \Pi_n\,\partial_t\Phi_n - L
=\frac{1}{2a}\sum_n \Pi_n^2+\frac12\sum_{n,n'}K_{nn'}\,\Phi_n\Phi_{n'} .
$$

**Normal modes**
Diagonalize \(K\): the system becomes a sum of independent oscillators (normal modes). The slides then “study one oscillator” (one mode) and suppress its label.

---

## 2) One oscillator: classical setup

Pick one mode with coordinate \(\Phi(t)\), conjugate momentum \(\Pi(t)\), frequency \(\omega\).

**Lagrangian**
$$
L=\frac12(\partial_t\Phi)^2-\frac{\omega^2}{2}\Phi^2 .
$$

**Momentum**
$$
\Pi=\frac{\partial L}{\partial(\partial_t\Phi)}=\partial_t\Phi .
$$

**Hamiltonian**
$$
H=\Pi\,\partial_t\Phi-L=\frac12\Pi^2+\frac{\omega^2}{2}\Phi^2 .
$$

---

## 3) Writing the oscillation using \(a\) and \(a^\dagger\) (still can be classical)

Write the general sinusoidal motion in complex form:
$$
\Phi(t)=\frac{1}{\sqrt{2\omega}}
\Big(a\,e^{-i\omega t}+a^\dagger e^{i\omega t}\Big).
$$

Differentiate to get momentum (\(\Pi=\dot\Phi\)):
$$
\Pi(t)=\partial_t\Phi(t)
=\frac{-i\omega}{\sqrt{2\omega}}
\Big(a\,e^{-i\omega t}-a^\dagger e^{i\omega t}\Big).
$$

Define
$$
a(t)\equiv a\,e^{-i\omega t},\qquad a^\dagger(t)\equiv a^\dagger e^{i\omega t},
$$
so
$$
\Phi(t)=\frac{1}{\sqrt{2\omega}}\big(a(t)+a^\dagger(t)\big),\qquad
\Pi(t)=\frac{-i\omega}{\sqrt{2\omega}}\big(a(t)-a^\dagger(t)\big).
$$

**Interpretation (classical):** \(a\) is a complex amplitude encoding initial conditions (amplitude + phase). Nothing quantum is required yet.

---

## 4) Quantization: “promote to operators”

Quantization means:
- \(\Phi,\Pi\) become operators \(\hat\Phi,\hat\Pi\) acting on states \(|\psi\rangle\).
- Impose canonical commutation relation:
$$
[\hat\Phi,\hat\Pi]=i .
$$

This implies an uncertainty principle:
$$
\Delta\Phi\,\Delta\Pi\ge \frac12 .
$$

### Derivation sketch (how \([\Phi,\Pi]=i\) implies uncertainty)
For any operators \(A,B\),
$$
\Delta A\,\Delta B \ge \frac12\,\big|\langle [A,B]\rangle\big| .
$$
Setting \(A=\Phi, B=\Pi\) and using \([\Phi,\Pi]=i\) gives \(\Delta\Phi\,\Delta\Pi\ge 1/2\).

**Physical implication:** \(\Phi\) and \(\Pi\) cannot both be perfectly sharp; this leads to unavoidable ground-state (“zero-point”) fluctuations and energy.

---

## 5) Ladder operators and why \(\Phi\sim a+a^\dagger\), \(\Pi\sim a-a^\dagger\)

Define (with \(\hbar=1\)):
$$
a \equiv \sqrt{\frac{\omega}{2}}\;\Phi+\frac{i}{\sqrt{2\omega}}\;\Pi,
\qquad
a^\dagger \equiv \sqrt{\frac{\omega}{2}}\;\Phi-\frac{i}{\sqrt{2\omega}}\;\Pi.
$$

Invert:
$$
\Phi=\frac{1}{\sqrt{2\omega}}(a+a^\dagger),
\qquad
\Pi=-i\sqrt{\frac{\omega}{2}}(a-a^\dagger).
$$

**Insight**
- \(\Phi\) and \(\Pi\) are Hermitian observables, so they must be built from Hermitian combinations of \(a,a^\dagger\).
- \(a+a^\dagger\) is Hermitian → naturally gives \(\Phi\).
- \(a-a^\dagger\) is anti-Hermitian → multiplying by \(-i\) makes it Hermitian → naturally gives \(\Pi\).
- Also, \(\Pi=\dot\Phi\) introduces a phase shift (derivative of \(e^{\mp i\omega t}\) gives \(\mp i\omega\)), which produces the relative minus sign.

Commutator becomes:
$$
[a,a^\dagger]=1 .
$$

---

## 6) Hamiltonian in \(a,a^\dagger\) and energy spectrum

Hamiltonian:
$$
H=\omega\Big(a^\dagger a+\frac12\Big).
$$

Number operator:
$$
N\equiv a^\dagger a.
$$

Then:
$$
H=\omega\Big(N+\frac12\Big).
$$

Eigenstates \(|n\rangle\):
$$
N|n\rangle=n|n\rangle,\qquad n=0,1,2,\dots
$$

Energies:
$$
E_n=\omega\Big(n+\frac12\Big).
$$

Ground state:
$$
a|0\rangle=0.
$$

---

## 7) Meaning of \([H,a]=-\omega a\) and “creation/annihilation”

Commutators:
$$
[H,a]=-\omega a,\qquad [H,a^\dagger]=+\omega a^\dagger.
$$

**Time-evolution insight (Heisenberg)**
$$
\dot a(t)=i[H,a(t)]=-i\omega a(t)\quad\Rightarrow\quad a(t)=a(0)e^{-i\omega t}.
$$

**Energy-ladder insight**
If \(H|E\rangle=E|E\rangle\), then:
$$
H(a|E\rangle)=(E-\omega)\,a|E\rangle,
\qquad
H(a^\dagger|E\rangle)=(E+\omega)\,a^\dagger|E\rangle.
$$

Action on number states:
$$
a|n\rangle=\sqrt{n}\,|n-1\rangle,\qquad
a^\dagger|n\rangle=\sqrt{n+1}\,|n+1\rangle,\qquad
a|0\rangle=0.
$$

---

## 8) Why “quanta of energy” are “particles” (free field)

A free field decomposes into independent modes labeled by momentum \(\mathbf{k}\). Each mode is an oscillator:
$$
H=\sum_{\mathbf{k}}\omega_{\mathbf{k}}\Big(N_{\mathbf{k}}+\frac12\Big),\qquad
N_{\mathbf{k}}=a^\dagger_{\mathbf{k}}a_{\mathbf{k}}.
$$

A one-quantum state in mode \(\mathbf{k}\):
$$
|\mathbf{k}\rangle=a^\dagger_{\mathbf{k}}|0\rangle,
$$
carries energy \(\omega_{\mathbf{k}}\) (and momentum \(\mathbf{k}\)). Hence mode excitations are interpreted as particles.

**“Different \(k\)”**
- \(k\) labels a different normal mode (different wavelength/momentum).
- In the “one oscillator” slides, the label is suppressed: \(a \equiv a_k\) for some chosen \(k\).

---

## 9) Bosons vs fermions (why “these are bosons because \(n>1\)”)

Bosons:
$$
[a_{\mathbf{k}},a^\dagger_{\mathbf{k}'}]=\delta_{\mathbf{k}\mathbf{k}'}
\quad\Rightarrow\quad
n_{\mathbf{k}}=0,1,2,\dots
$$
So \(n>1\) is allowed in the same mode.

Fermions:
$$
\{b_{\mathbf{k}},b^\dagger_{\mathbf{k}'}\}=\delta_{\mathbf{k}\mathbf{k}'}
\quad\Rightarrow\quad
(b^\dagger_{\mathbf{k}})^2=0
\quad\Rightarrow\quad
n_{\mathbf{k}}=0\ \text{or}\ 1.
$$

So \(b^\dagger\) creates a fermion (raises energy), but you cannot create a second fermion in the same mode.

---

## 10) Schrödinger-picture harmonic oscillator and operator method

Identify:
$$
\Phi \to x,\qquad \Pi \to p=-i\frac{d}{dx}.
$$

Hamiltonian:
$$
H=\frac12\big(p^2+\omega^2 x^2\big).
$$

Stationary Schrödinger equation:
$$
\left(-\frac12\frac{d^2}{dx^2}+\frac{\omega^2}{2}x^2\right)\psi_n(x)=E_n\psi_n(x).
$$

This is a second-order ODE with unknown eigenvalue \(E_n\).

### Ladder operator method

Dimensionless coordinate:
$$
\xi=\sqrt{\omega}\,x,\qquad \frac{d}{dx}=\sqrt{\omega}\frac{d}{d\xi}.
$$

Then (up to overall constants):
$$
a \propto \xi+\frac{d}{d\xi},\qquad
a^\dagger \propto -\frac{d}{d\xi}+\xi.
$$

Ground state condition:
$$
a\,\psi_0(\xi)=0
\quad\Rightarrow\quad
\left(\frac{d}{d\xi}+\xi\right)\psi_0(\xi)=0.
$$

Solution:
$$
\psi_0(\xi)\propto e^{-\xi^2/2}.
$$

Excited states:
$$
\psi_n \propto (a^\dagger)^n \psi_0.
$$

Energies:
$$
E_n=\omega\Big(n+\frac12\Big).
$$

---

## 11) Useful commutator facts

Definition:
$$
[A,B]=AB-BA.
$$

Leibniz rule:
$$
[A,BC]=[A,B]C+B[A,C].
$$

---

## 12) Why commutators look like differentiation (adjoint action)

A useful trick is to package the commutator into a one-parameter family of operators
$$
B(\lambda)\equiv e^{\lambda A}\,B\,e^{-\lambda A},\qquad d\equiv \frac{d}{d\lambda}.
$$
Expanding to first order in \(\lambda\):
$$
e^{\lambda A}=I+\lambda A+O(\lambda^2),\qquad e^{-\lambda A}=I-\lambda A+O(\lambda^2),
$$
so
$$
B(\lambda)=(I+\lambda A)B(I-\lambda A)+O(\lambda^2)=B+\lambda(AB-BA)+O(\lambda^2).
$$
Therefore
$$
\frac{dB(\lambda)}{d\lambda}\Big|_{\lambda=0}=[A,B].
$$
**Interpretation:** \([A,\cdot]\) is the “infinitesimal change” of an operator under the continuous transformation generated by \(A\). It is the tangent vector to the curve \(B(\lambda)\) at \(\lambda=0\).

### Product case (why it becomes a product derivative)

Conjugation preserves products. Insert identities \(I=e^{-\lambda A}e^{\lambda A}\) between factors:
$$
\begin{aligned}
 e^{\lambda A}(B_1B_2\cdots B_n)e^{-\lambda A}
 &= e^{\lambda A}B_1\,(e^{-\lambda A}e^{\lambda A})\,B_2\,(e^{-\lambda A}e^{\lambda A})\cdots B_n e^{-\lambda A}\\
 &= (e^{\lambda A}B_1e^{-\lambda A})(e^{\lambda A}B_2e^{-\lambda A})\cdots(e^{\lambda A}B_ne^{-\lambda A})\\
 &= B_1(\lambda)B_2(\lambda)\cdots B_n(\lambda).
\end{aligned}
$$
Differentiate and evaluate at \(\lambda=0\):
$$
[A,B_1\cdots B_n]
=\frac{d}{d\lambda}\Big(B_1(\lambda)\cdots B_n(\lambda)\Big)\Big|_{\lambda=0}
=\sum_{k=1}^n B_1\cdots B_{k-1}[A,B_k]B_{k+1}\cdots B_n.
$$
This is the commutator “Leibniz rule” for any number of factors.

### Special case: \([A,B]\) commutes with \(B\)

Assume
$$
[[A,B],B]=0\quad\Longleftrightarrow\quad [A,B]B=B[A,B].
$$
Apply the general product rule to \(B^n\):
$$
[A,B^n]=\sum_{k=1}^n B^{k-1}[A,B]B^{n-k}.
$$
Because \([A,B]\) commutes with \(B\), it commutes with any power \(B^m\), so each term reduces to
$$
B^{k-1}[A,B]B^{n-k}=[A,B]B^{n-1}.
$$
There are \(n\) identical terms, giving
$$
[A,B^n]=n\,[A,B]B^{n-1}.
$$

### Physical insight (generators \(\Rightarrow\) rates of change)

In quantum mechanics, continuous symmetries act by conjugation with a unitary \(U(\lambda)\):
$$
O(\lambda)=U(\lambda)^\dagger O\,U(\lambda),\qquad U(\lambda)=e^{-\frac{i}{\hbar}\lambda G},
$$
where \(G\) is the generator. Differentiating at \(\lambda=0\) gives
$$
\frac{dO}{d\lambda}\Big|_{0}=\frac{i}{\hbar}[G,O].
$$
So commutators encode “derivatives along symmetry flows.” Key examples:

- **Time translations:** \(G=H\) (Hamiltonian), \(\lambda=t\)
$$
\frac{dO}{dt}=\frac{i}{\hbar}[H,O].
$$
If \([H,O]=0\), then \(O\) is conserved.

- **Spatial translations:** \(G=P\) (momentum), \(\lambda=a\) (displacement)
$$
\frac{dO}{da}\Big|_{0}=\frac{i}{\hbar}[P,O].
$$

- **Rotations:** \(G=J\) (angular momentum), \(\lambda=\theta\) (angle)
$$
\frac{dO}{d\theta}\Big|_{0}=\frac{i}{\hbar}[J,O].
$$

Classically, the analogous statement is “change along a flow is a Poisson bracket.” Quantization replaces Poisson brackets by commutators (schematically)
$$
\{\cdot,\cdot\}\ \longrightarrow\ \frac{1}{i\hbar}[\cdot,\cdot].
$$
