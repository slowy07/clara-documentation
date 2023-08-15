# Reversibe (Dynamic_bitset and Bit_circuit classes)

This documentation provides a comprehensive explanation of the `Dynamic_bitset`
and `Bit_circuit` classes in the Clara library. These classes are used for
flexible-size arrays of bits and bit operations within a circuit.

## Dynamic_bitset Class

### Class Overview: `clara::Dynamic_bitset`

- **Brief Description**: Represents a dynamic bitset, a flexible-size array of
  bits for efficient storage and manipulation of binary data.

#### Private Members

1. **Storage Size**: `idx storage_size_`

   - **Description**: Number of storage elements needed for the bitset.

2. **Total Number of Bits**: `idx N_`

   - **Description**: Total number of bits in the bitset.

3. **Storage Vector**: `std::vector<value_type> v_`
   - **Description**: Storage vector for the bitset.

#### Public Member Functions

1. **Constructor**: `Dynamic_bitset(idx N)`

   - **Brief**: Creates a dynamic bitset of a given size.
   - **Parameters**: Total number of bits `N`.

2. **data() const**: `const storage_type& data() const`

   - **Brief**: Gets a const reference to the internal storage container.
   - **Return**: Const reference to the internal storage vector.

3. **size() const noexcept**: `idx size() const noexcept`

   - **Brief**: Gets the number of bits in the bitset.
   - **Return**: Number of bits in the bitset.

4. **storage_size() const noexcept**: `idx storage_size() const noexcept`

   - **Brief**: Gets the number of storage elements used in the bitset.
   - **Return**: Number of storage elements.

5. **count() const noexcept**: `idx count() const noexcept`

   - **Brief**: Counts the number of set bits (ones) in the bitset.
   - **Return**: Count of set bits.

6. **get(idx pos) const noexcept**: `bool get(idx pos) const noexcept`
   - **Brief**: Gets the value of the bit at the specified position.
   - **Parameters**: Position of the bit to retrieve.
   - **Return**: Value of the bit at the given position.

## Basic Usage `Dynamic_bitset`

```cpp title=reversible_dynamic_bitset.cpp
#include "Dynamic_bitset.h"
#include <iostream>

int main() {
  clara::Dynamic_bitset bitset(10); // Create a dynamic bitset of size 10
  bitset.set(2, true);              // Set bit at position 2 to true
  std::cout << "Bit at position 2: " << bitset.get(2) << std::endl;

  return 0;
}
```

## Bit_circuit Class

### Class Overview: `clara::Bit_circuit`

- **Brief Description**: Represent of bit operations derived from
  `Dynamic_bitset`

### Public Member Functions

1. **Constructor**: `Bit_circuit(const Dynamic_bitset& dynamic_bitset)`
   - **Brief**: Constructor that forwards argument to the base `Dynamic_bitset`
     Constructor **Parameters**: Reference to `Dynamic_bitset`
2. **X(idx pos)**: `Bit_circuit& X(idx pos)`
   - **Brief**: Applies the X (NOT) gate to the specified position
   - **Parameters**: Position of the bit to apply the gate to
   - **Return**: Reference to the modified `Bit_circuit`
3. **NOT(idx pos)**: `Bit_circuit NOT(idx pos)`
   - **Brief**: Applies the NOT gate to the specified position
   - **Parameters**: Position of the bit to apply the gate to
   - **Return**: Reference to the modified `Bit_circuit`

## Basic Usage `Bit_circuit`

```cpp title=reversible_Bit_circuit.cpp
#include "Dynamic_bitset.h"
#include "Bit_circuit.h"
#include <iostream>

int main() {
  clara::Dynamic_bitset dynamic_bitset(10);
  clara::Bit_circuit circuit(dynamic_bitset);
  circuit.X(2); // Apply X gate to position 2
  std::cout << "Bit at position 2: " << circuit.get(2) << std::endl;

  return 0;
}
```
