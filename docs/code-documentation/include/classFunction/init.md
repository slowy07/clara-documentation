# Init

The `Init` class in the Clara library is a singleton that facilitates the
initialization of the library by ensuring certain configurations are set up
before using other components. This documentation provides an overview of the
`Init` class and its usage within the Clara library.

## Class Overview

### Class Name: `clara::Init`

- **Brief Description**: Singleton class for initializing the library.

- **Friend Class**: `internal::Singleton<const Init>` - The `Init` class
  provides its initialization capabilities through the friend class
  `internal::Singleton<const Init>`.

#### Private Members

1. **Constructor**:

   - **Brief**: Private constructor for the `Init` class.
   - **Description**: The private constructor initializes the necessary
     configurations for the library. It can only be accessed through the friend
     class `internal::Singleton`.

2. **Destructor**:
   - **Brief**: Private destructor for the `Init` class.
   - **Description**: The private destructor ensures that the singleton instance
     is properly managed. It's designed to be accessed only by the Singleton
     infrastructure.

#### Usage Notes

- The `Init` class is responsible for setting up configurations that should be
  initialized before using other components of the library.
- Developers can customize the initialization process by uncommenting and
  modifying lines within the constructor. For example, adjusting output
  formatting using `std::cout` or other configurations can be done here.

## Basic Usage

```cpp title=example_init.cpp
int main() {
  // The Init class instance will automatically perform the necessary initialization
  clara::Init::GetInstance();

  // code here

  return 0;
}
```
