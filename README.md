# Inner World Systems (IWS) - Minimal Framework Simulation

This repository contains the numerical simulation code for the minimal formulation of the Inner World System (IWS) framework, as described in the paper *"Inner World Systems: A Minimal Hybrid Dynamical Framework for Non-Teleological Adaptive Systems"*.

## Structure
- `model.py`: Core mathematical definitions, continuous dynamics, and event-driven restructuring logic.
- `experiments.py`: Main script to run the 3 comparative regimes (No-geometry, No-Kairos, Full IWS).
- `plotting.py`: Utilities to generate the macroscopic indicators and phase-space projection figures.

The scripts reproduce:

Figure 2 – system dynamics
Figure 3 – state projection

## Requirements
```bash
pip install numpy matplotlib
```
## Parameterization

You can override default parameters directly from the command line to test robustness or explore new configurations:
Bash

```bash
# Run for 10000 steps instead of 5000, with 50 nodes
python experiments.py --steps 10000 --nodes 50

# Change the strength of the memory-induced geometry (lambda parameter)
python experiments.py --lambda_metric 5.0

# Use a specific set of random seeds
python experiments.py --seeds 1 2 3
```
