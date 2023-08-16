# Constant Header

This documentation provides an in-depth explanation of the `constants.h` header
in the Clara library. The `constants.h` header contains various constants and
utility functions that are used throughout the Clara library.

## Included Headers

The `constants.h` header includes the following header and types:

- `"classFunction/exception.h"`
- `"types.h"`

## Complex Literal Operators

The header defines custom user-defined literal operators for creating complex
numbers:

- `operator"" _i(unsigned long long int x)`: Creates a complex number with zero
  real part and the provided integer as the imaginary part.
- `operator"" _i(long double x)`: Creates a complex number with zero real part
  and the provided long double as the imaginary part.

These operators facilitate the creation of complex numbers using convenient
notation.

## Constants

### `chop`

The `chop` constant is used in calculations to set numbers with absolute values
smaller than the specified threshold to zero. It is set to `1e-10`.

### `eps`

The `eps` constant is used to determine whether a number or expression in double
precision is considered zero or not. It is set to `1e-12`.

### `maxn`

The `maxn` constant represents the maximum number of allowed qubits. It is used
internally to allocate arrays on the stack and is set to `64`.

### `pi`

The `pi` constant represents the mathematical constant π (pi) and is set to
`3.141592653589793238462643383279502884`.

### `ee`

The `ee` constant represents the mathematical constant e (Euler's number) and is
set to `2.718281828459045235360287471352662497`.

### `infinity`

The `infinity` constant represents positive infinity, which is the maximum value
of a double. It is used to represent unbounded values in certain calculations
and is obtained from `std::numeric_limits<double>::max()`.

## Utility Functions

### `omega`

The `omega` function calculates the complex number omega (ω), which is used in
certain quantum computations. It takes an input value `D` and returns the
complex number omega as `exp(2.0 * pi * 1_i / static_cast<double>(D))`. An
exception of type `exception::OutOfRange` is thrown if `D` is zero.

## Basic Usage

```cpp title=constants_example.cpp
#include "constants.h"

int main() {
    using namespace clara;

    // Example usage of constants
    double smallValue = chop; // Use chop constant to check if a value is small

    // Example usage of omega function
    idx D = 4;
    cplx omegaValue = omega(D); // Calculate omega for a given D

    return 0;
```
