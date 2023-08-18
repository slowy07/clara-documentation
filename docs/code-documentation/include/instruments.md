# Instruments

This header file `instruments.h` contains templated functions and classes
related to various quantum measurement operations and instrument-based
measurements. These functions provide functionality to measure quantum states,
perform sequential measurements, and work with different measurement bases. The
header also includes checks and error handling to ensure valid inputs and
consistent dimensions.

## Namespaces

The functions in this header file are defined within the `clara` namespace.

## Template Functions

### `ip`

This function computes the inner product between two quantum states. It supports
both pure and mixed states and handles measurement basis transformations.

#### Parameters

- `phi` : `Eigen::MatrixBase<Derived>`

  - The first quantum state vector/matrix for the inner product.

- `psi` : `Eigen::MatrixBase<Derived>`

  - The second quantum state vector/matrix for the inner product.

- `subsys` : `std::vector<idx>`

  - The indices of the subsystems involved in the measurement.

- `dims` : `std::vector<idx>`
  - The dimensions of the subsystems involved in the measurement.

#### Returns

- `dyn_col_vect<typename Derived::Scalar>`
  - The inner product between the two input quantum states.

### `measure`

This function performs measurements on quantum states using provided measurement
operators (POVMs) or orthonormal bases.

#### Parameters

- `A` : `Eigen::MatrixBase<Derived>`

  - The input quantum state to be measured.

- `Ks` : `std::vector<cmat>` OR `std::initializer_list<cmat>` OR cmat

  - Measurement operators or orthonormal basis vectors (POVMs) for the
    measurement.

- `subsys` : `std::vector<idx>`

  - The indices of the subsystems involved in the measurement.

- `dims` : `std::vector<idx>`

  - The dimensions of the subsystems involved in the measurement.

- `d` : idx (optional)
  - The dimension of the subsystems (default: 2).

#### Returns

- `std::tuple<idx, std::vector<double>, std::vector<cmat>>`
  - A tuple containing the measurement result index, outcome probabilities, and
    resulting post-measurement states.

### `measure_seq`

This function performs sequential measurements on quantum states.

#### Parameters

- `A` : `Eigen::MatrixBase<Derived>`

  - The input quantum state to be measured.

- `subsys` : `std::vector<idx>`

  - The indices of the subsystems involved in the sequential measurement.

- `dims` : `std::vector<idx>`

  - The dimensions of the subsystems involved in the sequential measurement.

- `d` : idx (optional)
  - The dimension of the subsystems (default: 2).

#### Returns

- `std::tuple<std::vector<idx>, double, cmat>`
  - A tuple containing the sequence of measurement result indices, cumulative
    probability, and resulting state after the sequential measurements.

## Error Handling

The functions include error checks for zero-sized matrices, valid dimensions,
and matching dimensions between matrices and subsystems.

```cpp title=instruments_exampl.cpp
#include <iostream>
#include "instruments.h"

int main() {
    using namespace clara;

    // Define quantum state vectors
    clara::ket psi = {1.0, 0.0}; // |0>
    clara::ket phi = {0.0, 1.0}; // |1>

    // Compute inner product between psi and phi
    double innerProduct = ip(psi, phi);
    std::cout << "Inner Product of psi and phi: " << innerProduct << std::endl;

    // Define measurement operators (Pauli matrices)
    clara::cmat PZ0 = clara::Gates::get_instance().PZ(0);
    clara::cmat PZ1 = clara::Gates::get_instance().PZ(1);

    // Perform measurement on the psi state using PZ0 and PZ1
    std::vector<clara::cmat> Ks = {PZ0, PZ1};
    auto measurementResult = measure(psi, Ks);
    idx outcomeIndex = std::get<0>(measurementResult);
    std::cout << "Measurement Outcome Index: " << outcomeIndex << std::endl;

    // Perform sequential measurement on the psi state
    std::vector<idx> subsys = {0};
    auto sequentialMeasurement = measure_seq(psi, subsys);
    std::vector<idx> outcomeSequence = std::get<0>(sequentialMeasurement);
    double cumulativeProbability = std::get<1>(sequentialMeasurement);
    std::cout << "Outcome Sequence: ";
    for (idx outcome : outcomeSequence) {
        std::cout << outcome << " ";
    }
    std::cout << "\nCumulative Probability: " << cumulativeProbability << std::endl;

    return 0;
}
```
