# Input Output

The `input_output.h` library provides functions for input and output operations
related to matrices and complex numbers. It includes functions for displaying,
saving, and loading Eigen matrices, as well as formatting ranges of elements and
complex numbers for display.

## Function Overview

### `disp` Functions

The `disp` functions are used to create `IOManip` objects that facilitate the
display of various types of data.

- `disp(const Eigen::MatrixBase<Derived>& A, double chop = clara::chop)`
- `disp(cplx z, double chop = clara::chop)`
- `disp(InputIterator first, InputIterator last, const std::string& separator, const std::string& start = "[", const std::string& end = "]")`
- `disp(const Container& c, const std::string& separator, const std::string& start = "[", const std::string& end = "]")`
- `disp(const PointerType& p, idx N, const std::string& separator, const std::string& start = "[", const std::string& end = "]")`

### `save` and `load` Functions

These functions are used for saving and loading Eigen matrices from binary
files.

- `void save(const Eigen::MatrixBase<Derived>& A, const std::string& fname)`
- `dyn_mat<typename Derived::Scalar> load(const std::string& fname)`

## Usage Considerations

- The functions provide utilities for displaying Eigen matrices, complex
  numbers, ranges of elements, and pointers to elements.
- The `save` and `load` functions enable saving and loading of Eigen matrices
  to/from binary files.

## Basic Usage

```cpp title=input_output_example.cpp
#include "input_output.h"
#include <iostream>
#include <complex>
#include <vector>
#include <Eigen/Dense>

int main() {
    // Example for displaying Eigen matrix
    Eigen::MatrixXd mat(3, 3);
    // Initialize matrix 'mat' with some values

    std::cout << "Displaying Eigen matrix:" << std::endl;
    std::cout << clara::disp(mat) << std::endl;

    // Example for displaying complex number
    std::complex<double> complexNum(3.14, 2.17);
    std::cout << "Displaying complex number:" << std::endl;
    std::cout << clara::disp(complexNum) << std::endl;

    // Example for displaying a range of elements
    std::vector<int> vec = {1, 2, 3, 4, 5};
    std::cout << "Displaying a range of elements:" << std::endl;
    std::cout << clara::disp(vec.begin(), vec.end(), ", ") << std::endl;

    // Example for saving and loading Eigen matrix
    clara::save(mat, "matrix.bin");
    Eigen::MatrixXd loadedMatrix = clara::load<Eigen::MatrixXd>("matrix.bin");
    std::cout << "Loaded matrix:" << std::endl;
    std::cout << clara::disp(loadedMatrix) << std::endl;

    return 0;
}
```
