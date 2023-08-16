# Timer

This documentation provides an in-depth explanation of the `Timer` class within
the Clara library. The `Timer` class is designed for accurately measuring time
intervals using the C++ `<chrono>` library. It serves the purpose of
benchmarking code performance and measuring the time taken for specific
operations.

## Class Overview

### `clara::Timer`

- **Brief Description**: Class for measuring time intervals using the C++
  `<chrono>` library.

The `Timer` class offers an efficient and accurate way to measure time intervals
using the C++ `<chrono>` library. It can be utilized to measure the duration of
specific operations or to conduct benchmarking for code performance evaluation.

## Template Parameters

- **`T`**: The type of duration used for measuring time intervals (default:
  `std::chrono::duration<double>`).
- **`CLOCK_T`**: The clock type to be used (default:
  `std::chrono::steady_clock`).

## Public Member Functions

### `Timer()`

- **Brief**: Constructs an instance with the current time as the starting point.

### `void tic()`

- **Brief**: Resets the chronometer, setting the current time as the starting
  and ending point.

### `const Timer& toc()`

- **Brief**: Stops the chronometer, setting the current time as the ending
  point.
- **Return**: Current instance of the `Timer`.

### `double tics()`

- **Brief**: Returns the number of tics (specified by `T`) that passed between
  instantiation/rest and invocation of `clara::Timer::toc()`.

### `template <typename U = T> U get_duration()`

- **Brief**: Returns the duration between the reset and invocation of
  `clara::Timer::toc()`.
- **Template Parameter**:
  - **`U`**: The type of duration to be returned (default: `T`).
- **Return**: Duration between reset and invocation of `clara::Timer::toc()`.

## Inheritance

- **`clara::Timer`** inherits from `clara::IDisplay`.

## Basic Usage

```cpp title=example_timer.cpp
#include "Timer.h"
#include <iostream>

int main() {
  clara::Timer<> timer;

  timer.tic();
  // Perform some operation to measure
  timer.toc();

  std::cout << "Elapsed Time: " << timer.get_duration().count() << " seconds" << std::endl;

  return 0;
```
