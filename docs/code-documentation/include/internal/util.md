# Internal Utility

This documentation provides an in-depth explanation of the `internal_util`
header in the Clara library. The `internal_util` header contains utility
functions and structures that are used internally by the library to perform
various mathematical and matrix-related operations.

## Included Headers

The `internal_util` header includes the following headers:

- `<algorithm>`
- `<cassert>`
- `<cmath>`
- `<functional>`
- `<iomanip>`
- `<iterator>`
- `<numeric>`
- `<type_traits>`
- `"constants.h"`
- `"types.h"`

## Namespace

The functions and structures defined in the `internal_util` header are encapsulated within the `clara::internal` namespace.

## Utility Functions

### `n2multiidx`

Converts a linear index to multi-dimensional indices for a given set of dimensions.

- `n`: the linear inde
- `numdims`: the number of dimension
- `dims`: pointer to an array of dimension
- `result`: pointer to an array to store multi-dimensional indices

### `multiidx2n`

Converts multi-dimensional indices to a linear index for a multi-dimensional array

```cpp
idx multiidx2n(const idx* const midx, idx numdims, const idx* const dims);
```

- `midx`: pointer to an array of multi-dimensional indices
- `numdims`: the number of dimension
- `dims`: pointer to an array of dimension

### Kronecker and Direct Sum Operations

Functions for Kronecker and direct sum oeprations on matrices

- `kron2`
- `dirsum2`

### Other Uitility Functions

Other utility functions such as extracting subsystems, determining the number of subsystem, and dimension calculation

- `get_num_subsys`
- `get_dim_subsystem`

## Matrix Formatting

The `Display_Impl_` struct provides methods to display matrix-like objects with customize formatting

```cpp title=example_matrix_formatting.cpp
#include "intenal/util.h"

int main() {
    // Usage example of functions defined in internal_util
    std::vector<clara::idx> dims = {3, 3, 3};
    clara::idx multiIndices[3];
    clara::internal::n2multiidx(5, 3, dims.data(), multiIndices);
    clara::idx linearIndex = clara::internal::multiidx2n(multiIndices, 3, dims.data());

    // Additional usage examples can be added for other utility functions

    return 0;
}
```
