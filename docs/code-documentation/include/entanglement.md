# Entanglement

The Clara Entanglement Library provides functions for calculating various
entanglement measures and properties of bipartite pure and mixed quantum states.
It is designed to work with Eigen matrices and expressions.

## Overview

The library includes functions to calculate the following entanglement measures
and properties:

- **Schmidt Coefficients**: Calculate the Schmidt coefficients of a bipartite
  pure state 'A'.
- **Schmidt Basis**: Calculate the Schmidt basis vectors on Alice's or Bob's
  side for a bipartite pure state 'A'.
- **Squared Schmidt Coefficients (Schmidt Probabilities)**: Calculate the
  squared Schmidt coefficients (Schmidt probabilities) for a bipartite state
  'A'.
- **Entanglement**: Calculate the entanglement of a bipartite pure state 'A'
  using various measures.
- **G-Concurrence**: Calculate the G-concurrence of a bipartite pure state 'A'.
- **Negativity**: Calculate the negativity of a bipartite mixed state 'A'.
- **Logarithmic Negativity**: Calculate the logarithmic negativity of a
  bipartite mixed state 'A'.
- **Wootters Concurrence**: Calculate the Wootters concurrence of a bipartite
  mixed state 'A'.

### `schmidtA`

Calclate the schmidt basis on Alice's side for a bipartite pure state 'A'

```cpp
template <typename Derived>
cmat schmidtA(const Eigen::MatrixBase<Derived>& A, const std::vector<idx>& dims);
```

- `A`: Eigen matrix represention the bipartite pure state
- `dims`: vector containing the dimension of the two subsystem

## Basic Usage

```cpp title=entanglement_example.cpp
#include "entanglement.h"
#include <Eigen/Dense>

int main() {
  Eigen::MatrixXd bipartiteState(3, 4);
  std::vector<clara::idx> dimensions = {3, 4};

  // Calculate Schmidt Coefficients
  clara::dyn_col_vect<double> schmidtCoeffs = clara::schmidtcoeffs(bipartiteState, dimensions);

  // Calculate Schmidt Basis on Alice's Side
  clara::cmat schmidtMatrixA = clara::schmidtA(bipartiteState, dimensions);

  // Calculate Squared Schmidt Coefficients (Schmidt Probabilities)
  std::vector<double> schmidtProbs = clara::schmidtprobs(bipartiteState, dimensions);

  // Calculate Entanglement
  double entanglementValue = clara::entanglement(bipartiteState, dimensions);

  // Calculate G-Concurrence
  double gConcurrenceValue = clara::gconcurrence(bipartiteState);

  // Calculate Negativity
  double negativityValue = clara::negativity(bipartiteState, dimensions);

  // Calculate Logarithmic Negativity
  double logNegativityValue = clara::lognegativity(bipartiteState, dimensions);

  // Calculate Wootters Concurrence
  double concurrenceValue = clara::concurrence(bipartiteState);

  return 0;
}
```
