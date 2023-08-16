# IOManip Header

This documentation provides an in-depth explanation of the `IOManip` header in
the Clara library. The `IOManip` header contains several classes that define
ostream manipulators for formatting various types of data. These manipulators
enhance the formatting and display capabilities when working with output
streams.

## Class Overview

### `clara::internal::IOManipRange`

- **Brief Description**: Ostream manipulators for formatting ranges of elements
  from an input iterator.

The `IOManipRange` class provides ostream manipulators to format ranges of
elements from an input iterator. This is particularly useful when displaying
sequences of data in a specific format.

### `clara::internal::IOManipPointer`

- **Brief Description**: Ostream manipulators for formatting arrays pointed to
  by a pointer.

The `IOManipPointer` class offers ostream manipulators to format arrays pointed
to by a pointer. This class enables you to customize the display of array data
when writing to output streams.

### `clara::internal::IOManipEigen`

- **Brief Description**: Ostream manipulator for formatting Eigen matrices and
  complex numbers.

The `IOManipEigen` class introduces an ostream manipulator to format Eigen
matrices and complex numbers. This manipulator enhances the display of these
types of data by providing customizable formatting options.

## IOManipRange

The `IOManipRange` class provides the capability to format a range of elements
from an input iterator and customize the display format. The constructor accepts
parameters to define the range, separator, and start/end strings.

## IOManipPointer

The `IOManipPointer` class allows you to format arrays pointed to by a pointer.
This enables you to control the appearance of array data when writing to output
streams. The constructor takes the array pointer, number of elements, separator,
and start/end strings as parameters.

## IOManipEigen

The `IOManipEigen` class is designed to enhance the display of Eigen matrices
and complex numbers. It offers a way to customize the formatting of these types
of data, providing a better representation in the output streams. The
constructor accepts an Eigen matrix or a complex number and an optional
threshold for truncating small values.

## Basic Usage

```cpp title=example_IOManip.cpp
#include "IOManip.h"
#include <iostream>
#include <vector>
#include <complex>

int main() {
    std::vector<int> intArray = {1, 2, 3, 4, 5};

    // Format and display the range of elements
    std::cout << clara::internal::IOManipRange(intArray.begin(), intArray.end(), ", ") << std::endl;

    double doubleArray[] = {1.1, 2.2, 3.3, 4.4, 5.5};

    // Format and display the array pointed to by a pointer
    std::cout << clara::internal::IOManipPointer(doubleArray, sizeof(doubleArray) / sizeof(double), ", ") << std::endl;

    std::complex<double> complexNumber(3.0, 4.0);

    // Format and display the complex number
    std::cout << clara::internal::IOManipEigen(complexNumber) << std::endl;

    return 0;
}
```
