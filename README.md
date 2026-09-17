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
propagate, it decays exponentially, but if the barrier is thin enough,
the wave doesn't fully die out before reaching the other side, so a
reduced-amplitude wave continues beyond it. That leaked-through amplitude
is quantum tunnelling.

## What this notebook does

- Sets up an electron (`E = 0.9 eV`) incident on a barrier
  (`V₀ = 1 eV`, width `b = 1.4 nm`) a sub-barrier ("classically
  forbidden") case
- Computes:
  - `k = √(2mE)/ħ` the oscillatory wavenumber in the free regions
    (left of the barrier and right of it)
  - `α = √(2m(V₀−E))/ħ` the exponential decay constant inside the
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
  <img width="1284" height="724" alt="tunnelling_wavefunction" src="https://github.com/user-attachments/assets/93c8da6a-cc0e-4e06-888a-a95bcd6d7e1b" />

- For reference, the rough estimate `T ≈ e^(−2αb)` for these parameters
  gives T ≈ 1%, consistent with the small amplitude visible in the
  right-hand region of the plot.
- Try varying `E` relative to `V₀`, or the barrier width `b`, to see how
  sharply the transmitted amplitude depends on both.
