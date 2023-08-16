# Entropies

The `entropy.h` header provides functions to calculate various types of entropy
measures, such as von Neumann entropy, Shannon entropy, Renyi entropy, Tsallis
entropy, quantum mutual information, and mutual information between subsystems
of a quantum system.

### Included Libraries

- `<cmath>`: Provides mathematical functions like `log2` and `pow`.
- `<limits>`: Provides constants like infinity.
- `"classFunction/exception.h"`: Includes exception handling for custom
  exceptions.
- `"classFunction/gates.h"`: Includes functionality related to gates.
- `"constants.h"`: Includes constant definitions.
- `"functions.h"`: Includes general mathematical functions.
- `"internal/util.h"`: Includes utility functions for internal use.
- `"types.h"`: Includes type definitions.
- `Eigen`: Matrix and linear algebra library.

### Namespace

All functions are defined in the `clara` namespace.

## Functions

### `double entropy(const Eigen::MatrixBase<Derived>& A)`

- Calculates the von Neumann entropy of a density matrix `A`.
- Parameters:
  - `A`: Eigen matrix representing the density matrix.
- Returns: Von Neumann entropy with logarithm in base 2.
- Throws exceptions for zero size matrix and non-square matrix.

### `double renyi(const Eigen::MatrixxBase<Derived>& A, double alpha)`

- Calculates the Renyi entropy of a density matrix `A`
- Parameters:
  - `A`: Eigen Matrix representing the density matrix
  - `alpha`: Parameter for Renyi entropy calculation
- Returns: Renyi entropy with logarithm in base 2
- Throws exception for zero size matrux, non-square matrix, and negative alpha

```cpp
Eigen::MatrixXd densityMatrix;
double alpha = 2.0;

// Calculate Renyi α-entropy for the density matrix with α = 2
double renyiEntropy = clara::renyi(densityMatrix, alpha);
```

### `double renyi(const std::vector<double>& prob, double alpha)`

- Calculates the Renyi α-entropy of a probability distribution.
- Parameters:
  - `prob`: Vector of probability distribution values
  - `alpha`: Parameter for Renyi entropy calculation
- Returns: Renyi entropy with logarithm base 2
- Throws exception for zero size probability distribution and invalid alpha

```cpp
std::vector<double> probabilityDistribution = {0.2, 0.3, 0.5};
double alpha = 0.5;

// Calculate Renyi α-entropy for the probability distribution with α = 0.5
double renyiEntropy = clara::renyi(probabilityDistribution, alpha);
```

### `double tsallis(const Eigen::MatrixBase<Derived>& A, double q)`

- Calculates the Tsallis q-entropy of a density matrix `A`.
- Parameters:
  - `A`: Eigen matrix representing the density matrix
  - `q`: Parameter for Tsallis q-entropy calculation
- Returns: Tsallis q-entropy
- Throws exception for zero size matrix, non-square matrix, and negative q.

```cpp
Eigen::MatrixXd densityMatrix;
double q = 2.0;

// Calculate Tsallis q-entropy for the density matrix with q = 2
double tsallisEntropy = clara::tsallis(densityMatrix, q);
```

### `double tsallis(const std::vector<double>& prob, double q)`

- Calculates the tsallis q-entropy for probability distribution.
- Parameters:
  - `prob`: Vector of probability distribution values.
  - `q`: Parameter for Tsallis q-entropy calculation.
- Returns: tsallis q-entropy.
- Throws exception for zero size probability distribution and invalid q.

```cpp
std::vector<double> probabilityDistribution = {0.2, 0.3, 0.5};
double q = 1.5;

// Calculate Tsallis q-entropy for the probability distribution with q = 1.5
double tsallisEntropy = clara::tsallis(probabilityDistribution, q);
```

### `double qmutualinfo(const Eigen::MatrixBase<Derived>& A, const std::vector<idx>& subsysA, const std::vector<idx>& subsysB, const std::vector<idx>& dims)`

- Calculates the quantum mutual information between two subsystem of composite
  quantum system.
- Parameters:
  - `A`: Eigen matrix representing the density matrix of the composite system
  - `subsysA`: indices of subsystem A
  - `subsysB`: indices of subsystem B
  - `dims`: vector of dimension of the subsystem
- Returns: Quantum mutual information
- Throws exception for zero size matri, invalid dimension, non-square matrix,
  and mismatched dimension and subsystem

```cpp
Eigen::MatrixXd densityMatrix = ...;
std::vector<idx> subsystemA = {0, 1};
std::vector<idx> subsystemB = {2, 3};
std::vector<idx> dimensions = {2, 2, 2, 2};

// Calculate quantum mutual information between subsystem A and B
double mutualInfo = clara::qmutualinfo(densityMatrix, subsystemA, subsystemB, dimensions);
```

### `double qmutualinfo(const Eigen::MatrixBase<Derived>& A, const std::vector<idx>& subsysA, const std::vector<idx>& subsysB, idx d = 2)`

- Calculates the quantum mutual information ebtween two subsystem of a composite
  quantum system
- Parameters:
  - `A`: Eigen matrix representing the density matrix of the composite system
  - `subsysA`: indices of subsystem A
  - `subsysB`: indices of subsystem B
  - `d`: dimension of the subsystem (default is 2)
- Returns: Quantum mutual information
- Throws exception for zero size matrix, invalid dimension, non-square matrix,
  and mismatched dimension and subsystem

```cpp
Eigen::MatrixXd densityMatrix = ...;
std::vector<idx> subsystemA = {0, 1};
std::vector<idx> subsystemB = {2, 3};
idx dimension = 2;

// Calculate quantum mutual information between subsystem A and B
double mutualInfo = clara::qmutualinfo(densityMatrix, subsystemA, subsystemB, dimension);
```
