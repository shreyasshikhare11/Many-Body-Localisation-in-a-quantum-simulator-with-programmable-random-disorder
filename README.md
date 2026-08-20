# Many-Body-Localisation-in-a-quantum-simulator-with-programmable-random-disorder

This repository contains tools, simulators, and analysis code for studying many-body localisation (MBL) using trapped-ion / programmable quantum simulator models with random disorder. The codebase includes exact diagonalization engines, Trotterized circuit builders, hardware noise models, and analysis utilities for entanglement and measurement-based observables.

Repository layout

```
mbl_trapped_ion_sim/
│
├── README.md
├── requirements.txt
├── pyproject.toml
│
├── src/
│   └── mbl_sim/
│       ├── __init__.py
│       ├── config.py          # Disorder topologies & initial state generators
│       ├── exact_diag.py      # XXZ & long-range exact diagonalization engines
│       ├── circuits.py        # Parameterized Suzuki-Trotter circuit builders
│       ├── hardware.py        # Qiskit Aer noise models & hardware execution engine
│       └── observables.py     # Entanglement entropy, skin depth & randomized measurements
│
├── tests/
│   ├── __init__.py
│   ├── test_exact_diag.py    # Verification of Hamiltonians & spectral statistics
│   ├── test_circuits.py      # Gate count, depth, and Trotter unitaries tests
│   └── test_observables.py   # Statevector vs. randomized measurement parity tests
│
└── main.py                    # Integrated MBL instability sweep & execution script
```

Quick overview

- Language: Python
- Purpose: Provide simulation and analysis workflows to explore MBL phenomena in small-to-intermediate-sized quantum simulators and to compare circuit-based dynamics with exact diagonalization where feasible.

Highlights

- Exact diagonalization (XXZ & long-range Hamiltonians) for spectral statistics and eigenstate properties.
- Parameterized Trotter circuit generation for trotterized time evolution experiments.
- Noise & hardware modeling using Qiskit Aer backends (optional) to assess experimental robustness.
- Observables including entanglement entropy, localization measures (e.g., inverse participation ratio / skin depth), and methods for randomized measurements.

Requirements

- Python 3.8+
- NumPy, SciPy, Numba (optional), Matplotlib
- Qiskit (optional, for hardware simulations and noise models)

Install

1. Clone the repository

   git clone https://github.com/shreyasshikhare11/Many-Body-Localisation-in-a-quantum-simulator-with-programmable-random-disorder.git
   cd Many-Body-Localisation-in-a-quantum-simulator-with-programmable-random-disorder

2. Create and activate a virtual environment

   python -m venv .venv
   source .venv/bin/activate    # macOS / Linux
   .\.venv\Scripts\activate   # Windows (PowerShell)

3. Install dependencies

   pip install -r requirements.txt

If you don't have a requirements.txt yet, a minimal set is:

```
numpy
scipy
matplotlib
qiskit-aer    # optional
numba          # optional, for performance
pytest
```

Usage

- Run the integrated sweep:

  python main.py --config configs/example.yaml

- Use the package API from Python:

```python
from mbl_sim import config, exact_diag, circuits, observables

H = exact_diag.build_xxz_hamiltonian(num_spins=8, J=1.0, delta=1.0, long_range_alpha=1.5)
energies, states = exact_diag.diagonalize(H)
S = observables.entanglement_entropy(states[0], subsystem_size=4)
```

- Run tests:

  pytest -q

Development notes

- Tests in tests/ verify Hamiltonian construction, Trotter unitary assembly, and randomized measurement estimators. Run them often when changing numeric routines.
- Follow the docstrings in src/mbl_sim/ for function-level usage. Consider adding notebook examples in notebooks/ to demonstrate common workflows and figures.

Contributing

Contributions are welcome. Please open issues for bug reports and feature requests, and send pull requests for changes. Include tests for any numerical or algorithmic changes.

License

Please add a LICENSE file to define the project license (MIT, Apache-2.0, etc.). If you want, I can add an MIT license now.

Authors

- shreyasshikhare11 (owner)

Contact

Open an issue or reach out via GitHub.
