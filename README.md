# Blackbody Radiation: Classical vs. Quantum

A short notebook comparing two theoretical predictions for the spectral energy
density of blackbody radiation the **Rayleigh–Jeans law** (classical) and
**Planck's law** (quantum) and visualizing the divergence between them
known as the **ultraviolet catastrophe**.

## Background

At the end of the 19th century, classical physics predicted that a hot
object should radiate energy that increases without bound as frequency
increases the Rayleigh–Jeans law. Experimentally, this isn't what
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

## Notes / possible extensions

- The frequency range currently plotted (0–10¹⁴ Hz) sits mostly in the
  infrared. Extending it further into the UV (10¹⁵–10¹⁶ Hz) makes the
  classical curve's divergence from the Planck curve much more dramatic.
- Try varying `T` to see how the peak of the quantum curve shifts with
  temperature (Wien's displacement law).
  <img width="1500" height="900" alt="blackbody_extended" src="https://github.com/user-attachments/assets/7b8b1763-bd33-4b97-bdc0-9d5abc2de5a1" />
