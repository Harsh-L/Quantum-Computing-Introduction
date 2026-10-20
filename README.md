# Quantum Computing Introduction

Hands-on notebooks from my first steps into quantum computing with **Qiskit**.
I learn by building, so each notebook is an experiment: write a circuit, run it, check the result.

This is the start of a longer path toward quantum computing and quantum machine learning (QML).

## Notebooks

| Notebook | What it covers |
|---|---|
| `Quantum_Computing_Introduction.ipynb` | Small experiments to understand what a qubit really is: superposition, measurement, state vectors, interference and phase |
| `Quantum_Computing_Arithmetic.ipynb` | Addition, subtraction, multiplication, division and negation on quantum circuits, plus circuit-building experiments and a first look at a QML ansatz |

## What I explored

**1. Core qubit concepts (Introduction notebook)**

Each experiment starts with a question, and I try to predict the answer before running it.

- **Superposition:** one Hadamard (H) gate, then measure. 1000 shots gave `{'1': 511, '0': 489}`, close to 50/50
- **Randomness:** running the same circuit 5 times gives different counts each time (between 469 and 514 zeros out of 1000). Every single measurement is random
- **State vectors:** after one H gate, the state is `[0.707, 0.707]`, which is 1/√2 for both 0 and 1
- **X then H:** gives `[0.707, -0.707]`. Same 50/50 counts when measured, but notice the minus sign
- **H twice:** 1000 out of 1000 shots return `0`. Not random at all. The two paths interfere and cancel out
- **Two qubits:** H on both gives an equal superposition of all 4 outcomes (`0.5` each). H on only qubit 0 gives just `00` and `01`, because qubit 1 never leaves 0
- **Valid states:** amplitudes must have squares that add up to 1. `[0.6, 0.8]` is valid (probabilities 0.36 and 0.64), while `[0.5, 0.5]` and `[1, 1]` are not
- **Phase:** `|+>` and `|->` both measure 50/50, with exactly the same probabilities. Add one more H and `|+>` becomes `0` while `|->` becomes `1`. The difference is hidden in the phase

**2. Arithmetic**
- **Addition** with Qiskit's `HalfAdderGate`. Example: 2 + 3 gives 5
- **Subtraction** by running an adder backwards (`ModularAdderGate(n).inverse()`). Example: 5 - 2 gives 3
- **Multiplication** with `MultiplierGate`. Example: 2 x 3 gives 6
- **Division**, built from scratch because Qiskit has no ready-made divider. It is binary long division made of adders: subtract the divisor, check if the result went negative, and add it back if it did. Example: 10 / 4 gives quotient 2, remainder 2
- **Negation** with two's complement: flip every bit, then add one. Example: 5 becomes `1011`, which reads as -5
- Composing circuits, converting them to gates, adding control qubits, and conditional gates with `if_test`
- A first look at `real_amplitudes`, a parameterized circuit used in QML

The arithmetic circuits are checked against plain Python for every input pair up to 3 bits.

## Known limitations

- Everything runs on simulators, not real quantum hardware (yet)
- The arithmetic circuits grow quickly with the size of the numbers. Dividing 10 by 4 already needs 17 qubits, so keep inputs small
- Division works for whole numbers with a non-zero divisor
- Built with Qiskit 2.x. The install cells are unpinned, so a future Qiskit release may need small updates

## Run it

**In Google Colab:** open a notebook here on GitHub, click the "Open in Colab" badge at the top, and run the cells from top to bottom.

**Locally:**
```bash
git clone https://github.com/Harsh-L/Quantum-Computing-Introduction.git
cd Quantum-Computing-Introduction
pip install qiskit qiskit-aer pylatexenc matplotlib jupyter
jupyter notebook
```

## Roadmap

- [x] Qubits, gates, state vectors, measurement
- [x] Superposition and interference with the Hadamard gate
- [x] Quantum addition, subtraction, multiplication, division and negation
- [ ] Phase and the Z gate (in progress)
- [ ] Entanglement (Bell states)
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
