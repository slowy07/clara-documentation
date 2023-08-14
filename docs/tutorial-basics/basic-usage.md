---
sidebar_position: 1
---

# Basic Usage

## Hello Clara

Quantum state is a mathematical object that represent the state of a quantum system. Quantum system are those that obey the laws of quantum mechanics, and they can be used to perform calculations that are impsossible with classical computers. clara can repersent a state quantum by

```cpp title="hello_clara.cpp"
#include <iostream>

#include "../include/clara.h"
// #include <clara>

using namespace clara;

/*
 * @brief minimal test
 * this code is a simple test to check the functionally
 * of the `clara` library and verify that the quantum
 * state |0> is correctly repersented and displayed
 * it starting point for more complex quantum computing
 * operation using clara function
 */
int main() {
  std::cout << "testing quantum state |0> state: \n";
  /**
   * represent the quantum state `|0>`,
   * in the quantum computing, the state `|0>` represent
   * the basic state qubit, where the qubit is the
   * zero state
   */
  std::cout << disp(st.z0) << std::endl;
}
```
```
testing quantum state |0> state:
1
0
```

