# Exception

[Source - `include/classFunction/Exception.h`](https://github.com/slowy07/clara/blob/main/include/classFunction/exception.h)

The `Exception` header defines the `Exception` class, which is used to represent
various exceptions that can occur within the Clara library. It offers an
organized enumeration of exception types and their corresponding messages.

## Class overview

the `Exception` inherits from `std::exception` and provides an organized way to
handle exceptions within the clara library

## Enum Type

the `Type` enumeration defins the supported exception types. each corresponds to
a specific exception message

- `UNKNOWN_EXCEPTION`: an unknown exception occured.
- `ZERO_SIZE`: the object has zero size
- `MATRIX_NOT_SQUARE`: the matrix is not square
- `MATRIX_NOT_CVECTOR`: the matrix is not a column vector

## Public Member Function

### `Exception(const std::string& where, const Type& type)`

This constructor creates an exception object wioth the provided location and
exception type.

- **Parameters**
  - `where` `(std::string)`: the location where the exception occured
  - `type` `(Type)`: the type of the exception

### `Exception(const std::string& where, const std::string& custom)`

This constructor creates an exception object with the provided location and a
custom exception message

- **Parameters**
  - `where` `(std::string)`: the location where the exception occured
  - `custom` `(std::string)`: the custom exception message

### `virtual const char* what() const noexcept override`

This member function returns the exception message associated with the exception
object

- **Returns** A pointer to a null-terminated character array representing the
  exception message

## Example Usage

```cpp title=example_exception.cpp
#incldue "exception.h"

void TestFunction() {
    try {
        // code may thrown a exception
        if (/* condition */) {
            throw Exception("TestFunction()", Exception::Type::ZERO_SIZE);
        }
    } except (const Exception& error) {
        std::cerr << "Exception: " << error.what() << std::endl;
    }
}
```
