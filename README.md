# Quantum Computing Introduction

Hands-on notebooks from my first steps into quantum computing with **Qiskit**.
I learn by building, so each notebook is an experiment: write a circuit, run it, check the result.

This is the start of a longer path toward quantum computing and quantum machine learning (QML).

## Notebooks

| Notebook | What it covers | 
|---|---|
| `Quantum_Computing_Introduction.ipynb` | Building a 4-qubit circuit, applying X gates, inspecting the `Statevector`, measuring, and sampling 100 shots with `StatevectorSampler` |
| `Quantum_Computing_Arithmetic.ipynb` | Addition, subtraction, multiplication, division and negation on quantum circuits, plus circuit-building experiments and a first look at a QML ansatz |

## What I explored

**1. Introduction**
- Flipping qubits with X gates and reading the resulting state vector (qubits 1 and 3 flipped gives the basis state `|1010>`)
- Measuring and sampling: 100 shots returned `{'1010': 100}`, as expected for a deterministic circuit

**2. Arithmetic**
- **Addition** with Qiskit's `HalfAdderGate`. Example: 2 + 3 gives 5
- **Subtraction** by running an adder backwards (`ModularAdderGate(n).inverse()`). Example: 20 - 2 gives 18
- **Multiplication** with `MultiplierGate`. Example: 2 x 3 gives 6
- **Division**, built from scratch because Qiskit has no ready-made divider. It is restoring long division made of adders, a copy of the "went negative" flag, and a controlled add-back. Example: 13 / 4 gives quotient 3, remainder 1
- **Negation** with two's complement: flip every bit, then add one. Example: 5 becomes `1011`, which reads as -5
- Composing circuits, converting them to gates, adding control qubits, and conditional gates with `if_test`
- A first look at `real_amplitudes`, a parameterized circuit used in QML

All arithmetic circuits were checked against plain Python for every input pair up to 3 bits, and against a few larger examples.

## Known limitations

- Everything runs on simulators, not real quantum hardware (yet)
- The circuits grow quickly with the size of the numbers. Dividing 13 by 4 already needs 17 qubits, so keep inputs small
- Division works for whole numbers with a non-zero divisor
- The notebooks were last run with Qiskit 2.6.0 and Qiskit Aer 0.17.2. The install cell is unpinned, so a future Qiskit release may need small updates

## Run it

**In Google Colab:** click an "Open in Colab" badge above and run the cells from top to bottom.

**Locally:**
```bash
git clone https://github.com/Harsh-L/Quantum-Computing-Introduction.git
cd Quantum-Computing-Introduction
pip install qiskit qiskit-aer pylatexenc matplotlib jupyter
jupyter notebook
```

## Roadmap

- [x] Qubits, gates, state vectors, measurement
- [x] Quantum addition, subtraction, multiplication, division and negation
- [ ] Superposition and entanglement (Bell states)
- [ ] Run circuits on real IBM Quantum hardware
- [ ] Quantum machine learning (QML) basics

## About

I'm Harsh Lad, a Dynamics 365 Business Central consultant in Surat, India, moving into quantum computing.
I'm interested in where quantum methods could meet real business problems.

- [LinkedIn](https://www.linkedin.com/in/harsh-lad)
- [Portfolio](https://harsh-lad.pages.dev)

Feedback and corrections are welcome. Open an issue or message me.

## License

See [LICENSE](LICENSE).
