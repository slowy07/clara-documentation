# Types

The following header code defines several type aliases using the C++ `using`
keyword. These aliases are intended to provide more meaningful names for various
types and structures used in the Clara library.

## Type Aliases:

### `idx`

- Alias for the size type used for indexing and dimension.
- It is an abbreviation for `std::size_t`.

### `bigint`

- Alias for a signed integer type with a larger size, suitable for representing
  larger integers.
- It is an abbreviation for `long long int`.

### `ubigint`

- Alias for an unsigned integer type with a larger size, suitable for
  representing large positive integers.
- It is an abbreviation for `unsigned long long int`.

### `cplx`

- Alias for a complex number type using double precision.
- It is defined using the `std::complex<double>` type.

### `ket`

- Alias for a column vector of complex numbers using the Eigen library.
- It is defined using `Eigen::VectorXcd`, representing a column vector of
  complex double values.

### `bra`

- Alias for a row vector of complex numbers using the Eigen library.
- It is defined using `Eigen::RowVectorXcd`, representing a row vector of
  complex double values.

### `cmat`

- Alias for a matrix of complex numbers using the Eigen library.
- It is defined using `Eigen::MatrixXcd`, representing a matrix of complex
  double values.

### `dmat`

- Alias template for dynamically sized matrices with elements of type `Scalar`.
- It is defined using `Eigen::MatrixXd`, representing dynamically sized matrices
  with double values.

### `dyn_mat<Scalar>`

- Alias template for dynamically sized matrices with elements of type `Scalar`.
- It is defined using `Eigen::Matrix<Scalar, Eigen::Dynamic, Eigen::Dynamic>`,
  where `Scalar` is a placeholder for the actual data type.

### `dyn_col_vect<Scalar>`

- Alias template for dynamically sized column vectors with elements of type
  `Scalar`.
- It is defined using `Eigen::Matrix<Scalar, Eigen::Dynamic, 1>`.

### `dyn_row_vect<Scalar>`

- Alias template for dynamically sized row vectors with elements of type
  `Scalar`.
- It is defined using `Eigen::Matrix<Scalar, 1, Eigen::Dynamic>`.

These type aliases provide convenient names for various types commonly used in
the Clara library, making the code more readable and expressive.
