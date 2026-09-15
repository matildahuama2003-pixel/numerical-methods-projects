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
parabolic potential `V(y) = y²` 
reproducing the standard "wavefunctions
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

## Notes / possible extensions

- The second set of wavefunctions is intentionally left unnormalized;
  normalizing each by `1/√(2ⁿ n! √π)` would make peak heights comparable
  across n.
- Try extending the power-series method past n=3 and comparing directly
  against the Hermite-polynomial curves for the same n.
  <img width="1500" height="900" alt="7cf7d568-ce7b-46fa-b192-0d68cf7a9b5a" src="https://github.com/user-attachments/assets/1cfe73c6-3f06-406d-a7a0-09f174b8bc9a" />
  <img width="1200" height="900" alt="qho_recursion_plot" src="https://github.com/user-attachments/assets/6cd42d09-4995-48d8-8cc3-5e1a3c1ae810" />
