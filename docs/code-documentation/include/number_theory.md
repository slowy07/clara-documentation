# Number Theory

The `number_theory.h` header file provides a collection of functions related to number theory in C++. These functions cover various aspects of number theory, including prime numbers, modular arithmetic, greatest common divisors (GCD), least common multiples (LCM), continued fractions, and more.

## Function `x2contfrac`

- **Description**: Computes the simple continued fraction expansion of a given real number `x` up to a specified number of terms.
- **Parameters**:
  - `x`: The real number for which the expansion is computed.
  - `N`: The maximum number of terms in the expansion.
  - `cut`: The cutoff value to terminate the computation early (default: 1e5).
- **Returns**: A vector of integers representing the continued fraction expansion.

## Function `contfrac2x`

- **Description**: Computes the real representation of a given simple continued fraction
- **Parameters**:
    - `cf`: A vector of integers representing the continued fraction
    - `N`: The maximum number of terms to use in the expansion (default: -1)
- **Returns**: The real representation of the simple continued fraction

## Function `gcd`

- **Description**: Computes the greates common divisors (GCD) of two integers
- **Parameters**:
    - `a`, `b`: the two integeres for which the GCD is computed
- **Returns**: The GCD of the two integers

## Function `gcd` (Overloaded for a List)

- **Description**: Computes GCD of a list of integers
- **Parameters**
    - `as`: A vector of integers for which the GCD is calculated
- **Returns**: The GCD of all integers in the vector

## Function `isprime`

- **Description**: Primality test based on the Miller-Rabin algorithm
- **Parameters**:
    - `p`: the integer to be test for Primality
    - `k`: the number of iterations for the Miller-Rabin (default: 80)
- **Returns**: `true`if `p` is most likely prime, `false` otherwise

## Function `randprime`

- **Description**: generate a random prime number in a given range using the Miller-Rabin test
- **Parameters**:
    - `a`, `b`: the range for the random prime number
    - `N`: the number of iterations to find a prime number 
- **Returns**: random prime number in specified range
