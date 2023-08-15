# IDisplay Interface

The `IDisplay` interface defines a common protocol for displaying objects in a
customized way. Derived classes that require specialized display formatting must
override the `display()` function. This interface allows for a consistent and
flexible approach to object display.


## Basic Usage

```cpp title=example_IDisplay.cpp
#include "IDisplay.h"
#include <iostream>
#include <string>

namespace clara {

class Person : public IDisplay {
 private:
  std::string name;
  int age;

 public:
  Person(const std::string& name, int age) : name(name), age(age) {}

 private:
  // Override the display function from IDisplay
  virtual std::ostream& display(std::ostream& os) const override {
    os << "Person: Name=" << name << ", Age=" << age;
    return os;
  }

 public:
  // Getter functions for name and age (not necessary for the example)
  std::string getName() const { return name; }
  int getAge() const { return age; }
};

}  // namespace clara

int main() {
  clara::Person person("Alice", 30);
  std::cout << person << std::endl;  // Display the person using the operator<<
  return 0;
}
```
