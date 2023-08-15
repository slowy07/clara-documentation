# Gates

[Source - `include/classFunction/gates.h`](https://github.com/slowy07/clara/blob/main/include/classFunction/gates.h)

The `clara::Gates` class is a singleton that provides a collection of quantum
gates and operations commonly used in quantum computing. It contains gates such
as Pauli-X, Pauli-Y, Pauli-Z, Hadamard, S, T, CNOT, CZ, SWAP, TOFFOLI, Fredkin,
and more. The class also includes methods to generate rotation gates,
generalized Z gates, Fourier transform gates, and Identity gates for qudits.
Additionally, it provides methods to construct multi-parity multiple controlled
gates. The Gates class ensures that gates are initialized only once and can be
accessed globally using the singleton pattern.

## Class Overview

The `Gates` class offers a variety of quantum gates and methods to generate
specialized gates. Some of the included gates are Pauli-X, Pauli-Y, Pauli-Z,
Hadamard, S, T, CNOT, CZ, SWAP, TOFFOLI, and Fredkin gates. Additionally, the
class provides methods to construct rotation gates, generalized Z gates, Fourier
transform gates, and Identity gates for qudits. Multi-parity multiple controlled
gates can also be constructed using the class.

## Gate Matrices

The following gate matrices are available as member variables:

- `Id2`: 2x2 Identity matrix
- `H`: Hadamard gate
- `X`: Pauli-X gate
- `Y`: Pauli-Y gate
- `Z`: Pauli-Z gate
- `S`: S gate
- `T`: T gate
- `CNOT`: Controlled NOT gate
- `CZ`: Controlled Z gate
- `CNOTba`: Controlled NOT with swapped control/target
- `SWAP`: SWAP gate
- `TOF`: Toffoli gate
- `FRED`: Fredkin gate

## Methods

### Rotation Gates

- `Rn(theta, n)`: Generates a rotation gate about a 3-dimensional real unit
  vector `n` by an angle `theta`.
- `RX(theta)`: Generates a 2x2 rotation matrix around the X-axis.
- `RY(theta)`: Generates a 2x2 rotation matrix around the Y-axis.
- `RZ(theta)`: Generates a 2x2 rotation matrix around the Z-axis.

### Generalized Z (Zd) Gate

- `Zd(D)`: Generates a generalized Z gate for qudits of dimension `D`.

### Fourier Transform (Fd) Gate

- `Fd(D)`: Generates a Fourier transform gate for qudits of dimension `D`.

### MODMUL Gate

- `MODMUL(a, N, n)`: Generates a modmul gate for modular multiplication with
  parameters `a`, `N`, and `n`.

### Generalized X (Xd) Gate

- `Xd(D)`: Generates a generalized X gate for qudits of dimension `D`.

### Identity (Id) Gate

- `Id(D)`: Generates an identity gate for qudits of dimension `D`.

### Multi-Parity Multi-Controlled Gates

- `CTRL(A, ctrl, subsys, N, d)`: Generates a multi-parity multi-controlled gate
  matrix based on input matrix `A`, control indices `ctrl`, subsystem indices
  `subsys`, total number of qubits `N`, and local dimension `d`.

### Expansion Methods

- `expandout(A, pos, dims)`: Expands the input matrix `A` into a larger tensor
  product space at the specified position `pos` using the provided dimensions
  `dims`.
- `expandout(A, pos, {dims})`: Alternative expansion method using an initializer
  list for dimensions.
- `expandout(A, pos, N, d)`: Expands the input matrix `A` into a larger
  multi-parity system with `N` total parties and local dimension `d`.

## Example Usage

```cpp title=example_gates.cpp
#include "gates.h"

int main() {
    clara::Gates& gates = clara::Gates::get_instance();
    // generate a hadamard matrix
    cmat hadamard_gate = gates.H;
    // generate controlled-Z gate
    cmat cz_gate = gates.CZ;
    // generate a rotation gate about the X-axis
    cmat rotation_x = gates.RX(0.5);
    // generate a rotation gate about the X-axis
    cmat fourier_gate = gates.Fd(3);

    // generate a multio-controlled gate using matrix A
    cmat matrix_A = ...; // matrix
    std::vector<idx> control_qubits = (0, 1);
    std::vector<idx> subsystem_qubits = {2, 3};
    cmat controlled_matrix = gates.CTRL(matrix_A, control_qubits, subsystem_qubits, 4);
}
```
