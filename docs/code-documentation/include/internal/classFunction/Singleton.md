# Singleton

This documentation provides an in-depth explanation of the `Singleton` header in
the Clara library. The `Singleton` header contains an implementation of the
singleton design pattern that ensures a class has only one instance and provides
a global point of access to that instance.

## Class Overview

### `clara::internal::Singleton`

- **Brief Description**: Implementation of a singleton pattern.

The `Singleton` class defines a template for implementing the Singleton pattern.
It ensures that a class has only one instance and provides a mechanism to access
that instance globally. This pattern is useful when you want to ensure that a
certain class has a single instance throughout the program's lifetime.

## Basic Usage

Using the `Singleton` template is simple. To make a class a singleton, follow
these steps:

1. Define a private constructor and destructor for your class.
2. Inherit your class from `clara::internal::Singleton<YourClassType>`.
3. To access the singleton instance, call `YourClassType::get_instance()`.

Here's an example implementation:

```cpp
#include "Singleton.h"

namespace clara {
namespace internal {

class MySingleton : public Singleton<MySingleton> {
    friend class Singleton<MySingleton>;

private:
    MySingleton() {
        // Private constructor
    }
    ~MySingleton() {
        // Private destructor
    }

public:
    // Additional member functions and variables

    void doSomething() {
        // Implementation
    }
};

}  // namespace internal
}  // namespace clara

int main() {
    // Access the singleton instance
    clara::internal::MySingleton& instance = clara::internal::MySingleton::get_instance();

    // Use the singleton instance
    instance.doSomething();

    return 0;
}
```
