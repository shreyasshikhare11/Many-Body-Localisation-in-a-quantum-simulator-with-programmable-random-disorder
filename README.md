# Many-Body Localization in a Quantum Simulator with Programmable Random Disorder

This repository contains a single research notebook that studies many-body localization (MBL) in disordered spin chains using both classical exact diagonalization and digital quantum simulation.

The notebook models two complementary setups:

- A 1D disordered XXZ chain with exact diagonalization and Trotterized quantum-circuit dynamics.
- A trapped-ion long-range spin model used to study localization signatures such as imbalance and level-spacing statistics.

The project is intended as a reproducible exploration of the transition between ergodic and localized regimes, with plots of entanglement entropy, imbalance, and spectral diagnostics.

## Repository contents

- `Many_body_localization_in_a_quantum_simulator_with_programmable_random_disorder.ipynb` — main notebook with all simulations, plots, and model implementations.
- `README.md` — project overview and usage instructions.

## What is inside the notebook?

The notebook is organized into several phases and simulation pipelines:

### 1. Disordered XXZ chain

- Exact diagonalization of a 1D XXZ Hamiltonian with random onsite fields.
- Construction of the domain-wall / Néel initial state.
- Time evolution via matrix exponentiation.
- Trotterized quantum-circuit implementation using Qiskit.
- Disorder-averaged entanglement entropy `S_A(t)` as a signature of ergodic vs localized behavior.

### 2. Trapped-ion long-range model

- Long-range XX interactions with power-law decay.
- Onsite random disorder and transverse fields.
- Exact diagonalization of the trapped-ion Hamiltonian.
- Evolution of the Néel state under unitary time dynamics.
- Computation of imbalance `I(t)` and level-spacing ratio `r`.

### 3. Hardware/noisy simulation components

- Disorder generation for random and quasiperiodic fields.
- Initial state configuration helpers.
- Noisy Qiskit execution framework for finite-shot simulation on trapped-ion-like hardware.

## Scientific motivation

The notebook is inspired by the study of many-body localization in systems with programmable disorder and by trapped-ion experimental platforms. It compares:

- thermalizing/ergodic dynamics at weak disorder,
- localized dynamics at strong disorder,
- exact-diagonalization benchmarks against Trotterized circuit evolution.

## Requirements

Python 3.10+ is recommended.

Install dependencies with:

```bash
python -m pip install numpy scipy matplotlib qiskit qiskit-aer jupyter
```

Optional packages used in some parts of the notebook include:

- `qiskit-aer` for noisy simulation support.
- `matplotlib` for plotting.

## Running the notebook

### Option 1: Local Jupyter

```bash
git clone https://github.com/shreyasshikhare11/Many-Body-Localisation-in-a-quantum-simulator-with-programmable-random-disorder.git
cd Many-Body-Localisation-in-a-quantum-simulator-with-programmable-random-disorder
jupyter notebook
```

Then open:

- `Many_body_localization_in_a_quantum_simulator_with_programmable_random_disorder.ipynb`

### Option 2: Google Colab

Upload the notebook to Google Colab and run all cells in order. The notebook already includes installation commands for `qiskit` and `qiskit-aer`.

## Typical workflow

The notebook generally follows this sequence:

1. Install Qiskit and Qiskit Aer.
2. Define Hamiltonians and state-preparation routines.
3. Run exact diagonalization for benchmarking.
4. Build Trotterized circuit models.
5. Compute entanglement entropy or imbalance.
6. Average over disorder realizations.
7. Plot the resulting curves and compare localized vs ergodic regimes.

## Example outputs

The script sections in the notebook produce plots comparing:

- ergodic disorder strength vs MBL disorder strength,
- entanglement growth in XXZ chains,
- imbalance decay in trapped-ion models,
- spectral statistics through the mean level-spacing ratio `r`.

## Notes

- This is a demonstration/research notebook rather than a packaged Python library.
- The code is educational and exploratory, intended for numerical experiments and analysis.
- Some sections are designed to show how disorder and dynamics can be modeled with Qiskit circuits and exact matrix methods.

## License

No explicit license file is present in this repository yet. Please add one if you plan to distribute or publish the project more broadly.

## Author

- shreyasshikhare11

## References

The notebook cites the underlying MBL and trapped-ion literature, including the paper:

- "Many-body localization in a quantum simulator with programmable random disorder" (arXiv:1508.07026)

If you want, I can also rewrite the notebook title/intro cells or turn this repository into a cleaner project structure with a `requirements.txt` and a proper `src/` layout.
