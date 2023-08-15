# States Class

This documentation provides a detailed explanation of the `States` class within
the Clara library. The `States` class implements commonly used quantum states
and provides essential functionalities for quantum state manipulation.

## Class Overview

### `clara::States`

- **Brief Description**: Const singleton class that implements commonly used
  quantum states.

The `States` class provides an efficient and consistent implementation of a
variety of quantum states, including computational states, Bell states, GHZ
states, and more. It implements various state vectors and projectors, making it
a valuable tool for quantum state manipulation.

## Public Member Functions

### `mes(idx d = 2)`

- **Brief**: Returns the maximally entangled state of 2 qudits.
- **Parameters**: Dimension of the qudits (`d`, default is 2).
- **Return**: Maximally entangled state
  \(\frac{1}{\sqrt{d}}\sum\_{j=0}^{d-1}|jj\rangle\) of 2 qudits.

### `zero(idx n, idx d = 2)`

- **Brief**: Returns the zero state of \(n\) qudits.
- **Parameters**: Number of qudits (`n`), dimension of the qudits (`d`, default
  is 2).
- **Return**: Zero state \(|0\rangle^{\otimes n}\) of \(n\) qudits.

### `one(idx n, idx d = 2)`

- **Brief**: Returns the one state of \(n\) qudits.
- **Parameters**: Number of qudits (`n`), dimension of the qudits (`d`, default
  is 2).
- **Return**: One state \(|1\rangle^{\otimes n}\) of \(n\) qudits.

### `jn(idx j, idx n, idx d = 2)`

- **Brief**: Returns the \(|j\rangle^{\otimes n}\) state of \(n\) qudits.
- **Parameters**: Eigenvalue to represent in the state (`j`), number of qudits
  (`n`), dimension of the qudits (`d`, default is 2).
- **Return**: \(|j\rangle^{\otimes n}\) state of \(n\) qudits.

### `plus(idx n)`

- **Brief**: Returns the plus state of \(n\) qubits.
- **Parameters**: Number of qubits (`n`).
- **Return**: Plus state \(|+\rangle^{\otimes n}\) of \(n\) qubits.

### `minus(idx n)`

- **Brief**: Returns the minus state of \(n\) qubits.
- **Parameters**: Number of qubits (`n`).
- **Return**: Minus state \(|-\rangle^{\otimes n}\) of \(n\) qubits.

## Basic Usage

```cpp title=example_states.cpp
#include "states.h"
#include <iostream>

int main() {
  const clara::States& states = clara::States::instance();

  clara::ket maximallyEntangled = states.mes(2);
  std::cout << "Maximally Entangled State: " << maximallyEntangled << std::endl;

  clara::ket zeroState = states.zero(3, 2);
  std::cout << "Zero State: " << zeroState << std::endl;

  clara::ket oneState = states.one(2, 3);
  std::cout << "One State: " << oneState << std::endl;

  clara::ket plusState = states.plus(2);
  std::cout << "Plus State: " << plusState << std::endl;

  clara::ket minusState = states.minus(1);
  std::cout << "Minus State: " << minusState << std::endl;

  return 0;
```
