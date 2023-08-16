# Codes

The `Codes` class in the `ClassFunction` namespace provides a collection of
code-related functionality for various quantum error-correcting codes. It
includes codeword generation for different types of codes, such as five-qubit,
seven-qubit Steane, and nine-qubit Shor codes.

## Class Definition

```cpp title=codes.h
class Codes final : public internal::Singleton<const Codes> {
```

the `Codes` class is defined as a final class, inherting from the
`internal::Singleton` class template. This ensure that only one instance of the
`Codes` class is available troughout the program

## Public Enum

```cpp title=codes.h
enum class Type { FIVE_QUBIT = 1, SEVEN_QUBIT_STEANE, NINE_QUBIT_SHOR };
```

the `Type` enum defines the different types of quantum error-correcting codes
that `Codes` class support. it includes `FIVE_QUBIT`, `SEVEN_QUBIT_STEANE`, and
`NINE_QUBIT_SHOR`

## Public Methods

```cpp title=codes.h
ket codeword(Type type, idx i) const;
```

the `codeword` method generates the codeword corresponding to the specified code
type and index. it returns `ket` object representing the codeword

- `type`: the type of qyuantum error-correcting code(from the `Type` enum)
- `i`: the index of the codeword to generate.
- `return`: object repersenting the codeword for the given code type and index
- `Exception`: with type `NO_CODEWORD` thrown when an invalid or unsupported
  code type or index is provided

## Private Constructor

```cpp title=codes.h
private:
    Codes() {}
```

the private constructor ensure that object of the `Codes` class cannot be
created directly. the `internal::Singleton` pattern guarantees that the class
has a single, globally accessible instance.
