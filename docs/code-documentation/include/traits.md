# Traits

This header code defines traits for type checking and compatibility detection
for various types in the context of statistical computations.

## `namespace clara`

The code is wrapped in the `clara` namespace to encapsulate the defined traits.

### `make_void` and `to_void`

These are metafunctions used for template parameter pack expansion.

### `is_iterable<T>`

This trait checks whether a type `T` is compatible with an STL-like iterable
container.

- It provides a `value` constant member that is true if the type `T` is
  iterable, and false otherwise.
- The trait uses SFINAE (Substitution Failure Is Not An Error) to check for the
  existence of `begin()`, `end()`, and `value_type` members in `T`.

### `is_matrix_expression<Derived>`

This trait checks whether a type is an Eigen matrix expression.

- It provides a `value` constant member that is true if the type is an Eigen
  matrix expression, specifically of type `Eigen::MatrixBase<Derived>`.

### `is_complex<T>`

This trait checks whether a type `T` is a complex number type.

- It provides a `value` constant member that is true if the type `T` is a
  complex type, and false otherwise.
- It is specialized for `std::complex<T>`, where `T` is any type.

These traits enable more generic and flexible type checking when using various
types in the statistical computations provided by the library.

### example

```cpp tilte=is_iterable_example.cpp
#include "traits.h"
#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec = {1, 2, 3};

    if (clara::is_iterable<decltype(vec)>::value) {
        std::cout << "The type is iterable!" << std::endl;
    } else {
        std::cout << "The type is not iterable!" << std::endl;
    }

    return 0;
}
```

```cpp title=is_matrix_expression.cpp
#include "traits.h"
#include <iostream>
#include <eigen3/Eigen/Dense>

int main() {
    Eigen::MatrixXd matrix(3, 3);

    if (clara::is_matrix_expression<decltype(matrix)>::value) {
        std::cout << "The type is an Eigen matrix expression!" << std::endl;
    } else {
        std::cout << "The type is not an Eigen matrix expression!" << std::endl;
    }

    return 0;
}
```

```cpp title=is_complex_example.cpp
#include "traits.h"
#include <iostream>
#include <complex>

int main() {
    std::complex<double> complexNumber(2.0, 3.0);

    if (clara::is_complex<decltype(complexNumber)>::value) {
        std::cout << "The type is a complex number type!" << std::endl;
    } else {
        std::cout << "The type is not a complex number type!" << std::endl;
    }

    return 0;
}
```
