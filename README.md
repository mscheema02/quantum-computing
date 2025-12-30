# Quantum Computing Algorithms (Grover • Quantum Gates • Shor Simulation)

This repository contains three study artifacts (two Jupyter notebooks and one PDF) that demonstrate foundational quantum computing concepts:
- **Grover’s search** via state-vector simulation
- **Basic single-qubit gate identities** using Qiskit statevector snapshots + measurements
- **Shor-style order-finding / period detection** using the **Quantum Fourier Transform (QFT)** and modular periodicity (mini-activity write-up)

---

## Files in this repo

### 1) `grover_algo.ipynb` — Grover’s Algorithm (State-Vector Simulation)
A NumPy-based simulation of **Grover’s search algorithm** using an explicit **state vector** (no circuit framework required).

**What it contains**
- Initialization of an equal superposition state for `n_qubits` (size `N = 2^n`)
- A simple **oracle** step that flips the phase (sign) of the **target/marked** basis state amplitude
- A **diffusion operator** (inversion about the mean amplitude), applying:
  - `a_i ← 2*mean(a) − a_i`
- Iterative application of:
  - **Oracle → Diffuser**
- Printed intermediate results:
  - state vector amplitudes after each step
  - probability distribution (`|amplitude|^2`) showing amplitude amplification over iterations

**Key learning outcomes**
- Why Grover iterations increase the marked-state probability and then “overshoot” if repeated too many times
- How the diffuser acts as a reflection about the global mean amplitude

---

### 2) `QuantumGates.ipynb` — Basic Quantum Gates (Qiskit + State Snapshots)
A Qiskit notebook demonstrating **single-qubit gate behavior** with clear, step-by-step state inspection.

**What it contains**
- Small 1-qubit circuits executed on `AerSimulator`
- Explicit initialization of the qubit state (e.g., `|0⟩` or `|1⟩`)
- A sequence showcasing a common identity:
  - **H → Z → H** (equivalent to applying **X** on a single qubit)
- Multiple `save_statevector(...)` checkpoints to capture statevectors after each stage
- Measurement results (shot counts) confirming the expected final basis state

**Key learning outcomes**
- How to interpret Qiskit circuit diagrams and results
- How statevectors evolve under `H`, `Z`, and composed operations like `HZH`
- Relationship between **phase flips** and **bit flips** through basis changes

---

### 3) `shor's_algo.pdf` — Shor Mini-Activity (QFT + Period / Order Finding Simulation)
A guided activity (PDF) focused on the **Quantum Fourier Transform** and **periodicity detection**, building intuition behind Shor’s approach to factoring via **order finding**.

**What it contains**
- Construction of the **QFT matrix** for an `n`-qubit register (`M = 2^n`)
- A periodic “spike train” state in the computational basis and its transformation under QFT
- Visualization of QFT output probabilities to identify **peaks** and estimate the **period**
- Modular exponentiation sequence simulation:
  - Generating `a^k mod N` until repetition to find the **order r**
- A simplified “Shor simulation” approach:
  - Using a measured/selected lower-register value (“collapse”) to form the periodic upper-register state
  - Predicting where QFT peaks should appear (near multiples of `M/r`)

**Key learning outcomes**
- Why periodic structure in the computational basis becomes peaks after the QFT
- How the **order r** relates to modular cycles and the factoring workflow
- How to infer period/order from peak spacing and resolution limits

---

## Technologies Used
- **Python** (Jupyter / IPython)
- **NumPy** (state-vector representation, linear algebra)
- **Qiskit** (circuit creation, simulation via Aer, statevector inspection)
- **Matplotlib** (probability/peak visualization)
- **Jupyter Notebooks** (`.ipynb`) for interactive execution and outputs
- **PDF** worksheet / write-up for Shor mini-activity documentation
