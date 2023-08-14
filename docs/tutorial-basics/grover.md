---
sidebar_position: 4
---

# Lets Make Grover's Algorithm !

Grover's algorithm is a quantum algorithm that provides quadatric speedup for
unstructed search problems

## Overview

the provide code demonstrates the implementeation Grover's algorithm using
`clara` library. The algorithm aims to marked element within a database of
quantum states using quantum operations.

## Grover's Algorithm steps

The code implements Grover's algorithm in the following steps

### Quantum System Setup

- the number of qubit `n` used in the algorithm is defined
- local dimension for qubits are set as a vector with all elements being 2,
  representing standard quantum bits (qubits)

```cpp title=grover_search.cpp
clara::idx n = 4;
std::vector<clara::idx> dims(n, 2);
```

### Database Size Calculation

- the size of the quantum state database is calculated as 2^n

```cpp title=grover_search.cpp
clara::idx N = std::round(std::pow(2, n));
```

### Randomly Marked Element

- a random element `marked` from the database is selected
- the binary representation of the marked element is displayed using the
  `clara::n2multiidx` function

```cpp title=grover_search.cpp
clara::idx marked = clara::randidx(0, N - 1);
```

### Initial Quantum State

- the computational state `psi` is initialized to |0>^n state, where all qubits
  are in the |0> state

```cpp title=grover_search.cpp
clara::ket psi = clara::mket(clara::n2multiidx(0, dims));
```

### Applying Hadamard Gate

hadamard gate is quatum gate that acts on a single qubit. it is one most
important gates in quantum computing, and it is used in a variety of quantum
algorithm. The hadamard gate is represented by following matrix:

```
H = 1/√2 ⋅ (|0⟩⟨0| + |1⟩⟨1|)
```

the hadamard gate has the following effect on a qubit:

- it puts the qubit into a superposition of two basis states, |0⟩ and |1⟩.
- its flip the phase of the qubit if it is in the |1⟩ gate.
  <br/>

- the hadamard gate `H` is applied to each qubit `n` times using the
  `clara::kronpow` function
- the represent the superposition of all possible states

```cpp title=grover_search.cpp
psi = (clara::kronpow(clara::gt.H, n) * psi).eval();
```

### Diffusion operator

- the diffusion operator `G` is calculated using the projection of `psi` into
  itself.
- the operator amplifies the amplitude of the marked element in the
  superposition

```cpp title=grover_search.cpp
clara::cmat G = 2 * clara::prj(psi) - clara::gt.Id(N);
```

### Grover algorithm Execution

- the number of queries is determined based on the square root of the database
  size `N`.
- the grover algorithm is executed in a loop for `nqueries` times
- the oeracle operation inverts the amplitude of the marked element, followed by
  the duffision operator

```cpp title=grover_search.cpp
clara::idx nqueries = std::ceil(clara::pi / 4 * std::sqrt(N));
for (clara::idx i = 0; i < nqueries; ++i) {
  // Apply oracle first
  psi(marked) = -psi(marked);
  // Apply diffusion operator
  psi = (G * psi).eval();
}
```

### Measurement and Result

- the probability of the marked state is calculated and printed
- the probabilities of all results in the superposition are displayed
- a sample result is obtained and correctness is verified

```cpp title=grover_search.cpp
auto measured = clara::measure(psi, gt.Id(N));
std::cout << "Probability of marked state: " << std::get<1>(measured)[marked] << std::endl;
std::cout << "Probability of all results: ";
std::cout << clara::disp(std::get<1>(measured), ", ") << std::endl;
```

<br/>
the provided grover search the implementation of grover's algorithm using quantum operations, including applying gatesm creating superposition, and using oracle and diffusion operators. the algorithm is executed on a quantum state database to search for a marked element, showcasing the principles of quantum search algorithm.
