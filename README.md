# Blackbody Radiation: Classical vs. Quantum

A short notebook comparing two theoretical predictions for the spectral energy
density of blackbody radiation — the **Rayleigh–Jeans law** (classical) and
**Planck's law** (quantum) — and visualizing the divergence between them
known as the **ultraviolet catastrophe**.

## Background

At the end of the 19th century, classical physics predicted that a hot
object should radiate energy that increases without bound as frequency
increases — the Rayleigh–Jeans law. Experimentally, this isn't what
happens: radiated energy rises, peaks, then falls back to zero. This
mismatch was one of the key puzzles that classical physics couldn't
explain.

In 1900, Max Planck resolved it by proposing that electromagnetic energy is
emitted in discrete packets (`E = hν`) rather than continuously. This one
assumption reproduces the observed spectrum and is widely regarded as the
starting point of quantum mechanics.

## What this notebook does

- Defines the **classical** spectral energy density:

  ρ_classical(ν) = 8π kB T ν² / c³

- Defines the **quantum (Planck)** spectral energy density:

  ρ_quantum(ν) = 8π h ν³ / (c³ (e^(hν / kB T) − 1))

- Plots both as a function of frequency at a fixed temperature (T = 300 K)
  to show where the two models agree (low frequency) and where they
  dramatically diverge (high frequency).

## Requirements

- Python 3
- `numpy`
- `matplotlib`

```bash
pip install numpy matplotlib
```

## Usage

Open `Black_body_radiation_analysis.ipynb` in Jupyter and run the single
cell. It will produce a plot of both energy density curves over the chosen
frequency range.
<img width="1500" height="900" alt="blackbody_extended" src="https://github.com/user-attachments/assets/c59a18a1-079b-4773-8478-9f58410f6b8c" />
## Notes / possible extensions

- The frequency range currently plotted (0–10¹⁴ Hz) sits mostly in the
  infrared. Extending it further into the UV (10¹⁵–10¹⁶ Hz) makes the
  classical curve's divergence from the Planck curve much more dramatic.
- Try varying `T` to see how the peak of the quantum curve shifts with
  temperature (Wien's displacement law).
  


# Quantum Harmonic Oscillator Wavefunctions

A notebook computing and visualizing the energy eigenstates of the quantum
harmonic oscillator (QHO) the quantum-mechanical analogue of a mass on a
spring using two independent methods.

## Background

The QHO is one of the few quantum systems solvable in closed form, and its
solutions (a Gaussian modulated by a polynomial) appear throughout physics,
from molecular vibrations to quantum field theory. Its energy levels are
evenly spaced, `Eₙ = (n + 1/2)ℏω`, and its wavefunctions `ψₙ` alternate
between even and odd symmetry as n increases.

## What this notebook does

**1. Power-series (Frobenius) solution**
Solves the QHO Schrödinger equation by assuming
`ψₙ(y) = e^(−y²/2) × (polynomial in y)`
and deriving the polynomial coefficients from a recursion relation. Plots
`ψ₀`–`ψ₃`, each shifted vertically by its energy level, alongside the
parabolic potential `V(y) = y²` reproducing the standard "wavefunctions
in a potential well" textbook figure.

**2. Hermite polynomial solution**
Recomputes the same wavefunctions using the closed-form expression
`ψₙ(x) ∝ Hₙ(x) · e^(−x²/2)`, generating the Hermite polynomials `Hₙ` with
`numpy.polynomial.hermite`. Plots `ψ₀`–`ψ₆`, left unnormalized, so
amplitude grows with `n`.

Both methods produce the same underlying physics and serve as a check on
one another.

## Requirements

- Python 3
- `numpy`
- `matplotlib`

```bash
pip install numpy matplotlib
```

## Usage

Open the notebook in Jupyter and run the single cell. It produces two
plots in sequence:

1. `ψ₀`–`ψ₃` nested in the potential well (power-series method)
2. `ψ₀`–`ψ₆`, unnormalized (Hermite polynomial method)
3. <img width="1200" height="900" alt="8ffb2952-6415-43b1-a5cb-d37b744f80a5" src="https://github.com/user-attachments/assets/6c9bab5e-dd21-4b30-b99f-3f945d2bc8af" />
<img width="1500" height="900" alt="659421fe-5f28-4aed-b006-f94fb1de307a" src="https://github.com/user-attachments/assets/5c677e33-b287-4e9a-9046-a340e6830f21" />


## Notes / possible extensions

- The second set of wavefunctions is intentionally left unnormalized;
  normalizing each by `1/√(2ⁿ n! √π)` would make peak heights comparable
  across n.
- Try extending the power-series method past n=3 and comparing directly
  against the Hermite-polynomial curves for the same n.



# Quantum Tunnelling Through a Rectangular Barrier

A notebook visualizing quantum tunnelling: an electron with energy below a
potential barrier's height, which classically could not cross it, but
which quantum mechanically has a nonzero probability of appearing on the
far side.

## Background

For a particle with energy `E` hitting a potential barrier of height `V₀`
and width `b`, classical mechanics says: if `E < V₀`, the particle bounces
back, full stop. Quantum mechanics instead treats the particle as a wave
governed by the Schrödinger equation. Inside the barrier the wave doesn't
propagate — it decays exponentially — but if the barrier is thin enough,
the wave doesn't fully die out before reaching the other side, so a
reduced-amplitude wave continues beyond it. That leaked-through amplitude
is quantum tunnelling.

## What this notebook does

- Sets up an electron (`E = 0.9 eV`) incident on a barrier
  (`V₀ = 1 eV`, width `b = 1.4 nm`) — a sub-barrier ("classically
  forbidden") case
- Computes:
  - `k = √(2mE)/ħ` — the oscillatory wavenumber in the free regions
    (left of the barrier and right of it)
  - `α = √(2m(V₀−E))/ħ` — the exponential decay constant inside the
    barrier
- Defines the wavefunction piecewise across three regions (left of the
  barrier, inside it, right of it), matching amplitudes at each boundary
- Plots `Re[ψ(x)]` across all three regions, showing the wave amplitude
  drop off exponentially through the barrier and continue, reduced, on
  the other side

## Requirements

- Python 3
- `numpy`
- `matplotlib`

```bash
pip install numpy matplotlib
```

## Usage

Open the notebook in Jupyter and run the single cell. It produces a plot
of the real part of the wavefunction across all three regions.
<img width="1284" height="724" alt="13459b2a-e72e-4f24-b4fc-833bb2bb3358" src="https://github.com/user-attachments/assets/c310cf49-0629-4e89-97e0-308c7ee7f72d" />


## Notes / limitations

- This uses a **simplified continuity treatment**: inside the barrier
  the wavefunction is modeled with a single decaying exponential term
  only (no growing-exponential component), and amplitudes are matched at
  each boundary without separately enforcing derivative (slope)
  continuity. This is enough to illustrate the qualitative tunnelling
  picture, but it is *not* the full rigorous boundary-matching solution.
- A complete treatment would include a reflected wave in the left region
  and both exponential terms in the barrier, solved via the standard 4
  (or transfer-matrix) boundary conditions — giving an exact transmission
  coefficient `T` and reflection coefficient `R` with `T + R = 1`.
- For reference, the rough estimate `T ≈ e^(−2αb)` for these parameters
  gives T ≈ 1%, consistent with the small amplitude visible in the
  right-hand region of the plot.
- Try varying `E` relative to `V₀`, or the barrier width `b`, to see how
  sharply the transmitted amplitude depends on both.
