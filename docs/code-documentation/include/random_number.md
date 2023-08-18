## Random Number Generation

This C++ header file provides various functions for generating random numbers and matrices with specific distributions. Let's go through each function and its usage.

## `rand(double a, double b)`

This function generates a random real number uniformly distributed in the interval `[a, b]`.

- Parameters:
  - `a`: The lower bound of the interval.
  - `b`: The upper bound of the interval.

- Returns: A random real number within `[a, b]`.

- Notes:
  - Throws an exception if `a` is greater than or equal to `b`.
  - Uses `std::uniform_real_distribution` for uniform distribution.
  - If `NO_THREAD_LOCAL_` is defined, uses the global random number generator.

## `rand(bigint a, bigint b)`

This function generates a random big integer uniformly distributed in the interval `[a, b]`.

- **Parameters**:
    - `a`: the lower bound of the interval
    - `b`: the upper bound of the interval
- **Returns**: a random big integer `[a, b]`
- **Notes**
    - throws an exception if `a` is greater than `b`
    - uses `std::uniform_int_distribution` for uniform distribution
    - if `NO_THREAD_LOCAL_` is defined, uses the global random number generator

```cpp title=random_number_example.cpp
#include random_number.h

using namespace clara;

int main() {
    clara::bigint lower_bound = 0;
    clara::bigint upper_bound = 100;
    clara::bigint result = clara::rand(lower_boumd, upper_bound);
    std::cout << result;

    return 0;
}
```
