# Clara Init Header

This documentation provides an in-depth explanation of the `clara.h` header in
the Clara library. The `clara.h` header is the main entry point for the Clara
library, including various utility functions, classes, and singletons used
throughout the library.

## Namespace Overview

All entities in the Clara library are encapsulated within the `clara` namespace.

## Constants

The `clara.h` header introduces a few constants:

- `CLARA_UNUSED_`: A macro to indicate unused variables, which is used based on
  compiler conditions.

## Singleton Instances

### `Init`

The `Init` singleton instance for additional initialization and cleanups.

### `Codes`

The `Codes` singleton instance for initializing codes.

### `Gates`

The `Gates` singleton instance for initializing gates.

### `States`

The `States` singleton instance for initializing states.

### `RandomDevices`

The `RandomDevices` singleton instance for initializing random devices. This
instance is either a global instance or a thread-local instance based on the
compilation settings.

## Order and Dependencies

The header organizes the dependencies and instances in the following order:

1. Various C++ standard and library headers.
2. Clara library headers.
3. Namespace `clara` with singleton instances:
   - `Init`
   - `Codes`
   - `Gates`
   - `States`
   - `RandomDevices`

```cpp title=clara_example.cpp
#include "clara.h"

int main() {
    // Example usage of singleton instances and constants
    clara::init.initialize(); // Initialize Clara library
    const auto& gates = clara::gt; // Access the initialized Gates instance

    // Additional usage examples can be added for other singleton instances

    return 0;
```
