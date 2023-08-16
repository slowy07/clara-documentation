# Functions

The `functions.h` header provides utility functions for performing various
matrix and mathematical operations. This includes functions for transposing
matrices.

### `dyn_mat<typename Derived::Scalar> transpose(const Eigen::MatrixBase<Derived>& A)`

- Transpose the input matrix
- Parameters:
  - `A`: Eigen matrix to be transposed
- Return: Transposed matrix of `A`
- Throws exception for zero size matrix

### Conjugate

The `conjugate` function, defined in the `functions.h` header, computes the
complex conjugate of a given matrix. The complex conjugate of a matrix involves
taking the complex conjugate of each element of the matrix. This function is
particularly useful when dealing with complex numbers and matrices in
mathematical and scientific computations.

- Parameters:
  - `A`: input matrix for which the complex conjugate is to be computed
- Return: a new matrix representing the complex conjugate of the input matrix
- Throws exception if the input matrix has zero size

#### Basic Usage

```cpp title=conjugate_example.cpp
#include "functions.h"

Eigen::MatrixXcd complexMatrix(2, 2);
complexMatrix << std::complex<double>(1.0, 2.0), std::complex<double>(-3.0, 4.0),
                 std::complex<double>(0.0, -5.0), std::complex<double>(6.0, 7.0);

// Compute the complex conjugate of the matrix
Eigen::MatrixXcd conjugateMatrix = clara::conjugate(complexMatrix);
```

### Adjoint

The `adjoint` function, defined in the `functions.h` header, calculates the
adjoint (conjugate transpose) of a given matrix. The adjoint of a matrix
involves taking the transpose of the matrix and then taking the complex
conjugate of each element of the resulting matrix.

#### Basic Usage

This function is commonly used in linear algebra and quantum mechanics to
perform operations involving complex conjugates and transpositions of matrices

- Parameters:
  - `A`: the input matrix for which the adjoint is to be calculated
- Return: a new matrix
- Throw Exception if the input matrix has a size of zero

```cpp
#include "functions.h"

Eigen::MatrixXcd complexMatrix(2, 2);
complexMatrix << std::complex<double>(1.0, 2.0), std::complex<double>(-3.0, 4.0),
                 std::complex<double>(0.0, -5.0), std::complex<double>(6.0, 7.0);

// Calculate the adjoint (conjugate transpose) of the matrix
Eigen::MatrixXcd adjointMatrix = clara::adjoint(complexMatrix);
```

### Inverse

The `inverse` function, defined in the `functions.h` header, calculates the
inverse of a given matrix. The inverse of a matrix is the matrix that, when
multiplied with the original matrix, results in the identity matrix. This
function is a fundamental operation in linear algebra and is often used in
solving systems of linear equations and performing transformations.

- Parameters: `A`: the input matrix for which the inverse to be calculated
- Returns: a new matrix representing of the input matrix
- Exception:
  - Throws exception if the input matrix has a size of zero
  - Throw other exceptions if the input matrix is singular or not invertible

```cpp
#include "functions.h"

Eigen::MatrixXd squareMatrix(2, 2);
squareMatrix << 2, -1,
                3,  4;

// Calculate the inverse of the matrix
Eigen::MatrixXd inverseMatrix = clara::inverse(squareMatrix);
```

### Trace

The `trace` function, defined in the `functions.h` header, calculates the trace
of a given matrix. The trace of a matrix is the sum of the elements on its main
diagonal. The trace of a matrix is often used in linear algebra to compute
various properties of matrices, such as the determinant and eigenvalues.

- Parameters:
  - `A`: the input matrix for which the trace is to be calculated.
- Returns: trace of the input matrix as a scalar value.
- Throw eception if the input matrix has a size of zero.

```cpp
#include "functions.h"

Eigen::MatrixXd squareMatrix(3, 3);
squareMatrix << 1, 2, 3,
                4, 5, 6,
                7, 8, 9;

// Calculate the trace of the matrix
double matrixTrace = clara::trace(squareMatrix);
```

### Determinant

The `det` function, defined in the `functions.h` header, calculates the
determinant of a given matrix. The determinant of a matrix is a scalar value
that represents a measure of the scaling factor of the matrix transformation.
The determinant is an important value in linear algebra and is used to determine
whether a matrix is invertible and to compute the eigenvalues of the matrix.

- Parameters: `A`: the input matrix for which the determinant is to be
  calculated
- Returns: return the determinant of the input matrix as a scalar value
- Throw exception if the input matrix has a size of zero.

```cpp
#include "functions.h"

Eigen::MatrixXd squareMatrix(3, 3);
squareMatrix << 1, 2, 3,
                4, 5, 6,
                7, 8, 9;

// Calculate the determinant of the matrix
double matrixDeterminant = clara::det(squareMatrix);
```

### Logarithm of Determinant Function Documentation

The `logdet` function, defined in the `functions.h` header, calculates the
logarithm of the determinant of a given matrix. This value is useful in various
mathematical and scientific applications, including statistics and optimization.

- Parameters: `A`: the input matrix for which the logarithm of the determinant
  is to be calculates
- Return: logarithm of the determinant of the input matrix as a scalar value
- Throw exception if the input matrix has a size of zero, if the iunput matrix
  is not square

```cpp
#include "functions.h"

Eigen::MatrixXd squareMatrix(3, 3);
squareMatrix << 1, 2, 3,
                4, 5, 6,
                7, 8, 9;

// Calculate the logarithm of the determinant of the matrix
double logDeterminant = clara::logdet(squareMatrix);
```

### Matrix Sum Function

The `sum` function, defined in the `functions.h` header, calculates the sum of
all elements in a given matrix. This function is useful for obtaining the total
of all elements in a matrix.

- Parameters:
  - `A`: the input matri for which the sum of elements is to be calculated
- Return: sum of all elements in the input matrix as a scalar value
- Throw exception if the input matrix has a size of zero

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

// Calculate the sum of all elements in the matrix
double totalSum = clara::sum(matrix);
```

### Matrix Product

The `prod` function, defined in the `functions.h` header, calculates the product
of all elements in a given matrix. This function is useful for calculating the
total product of all elements in a matrix.

- Parameters:
  - `A`: the input matrix for which the product of elements is to be calculated
- Return: the product of all elements in the input matrix as a scalar value
- Throw exception if the input matrix has a size of zero

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

// Calculate the product of all elements in the matrix
double totalProduct = clara::prod(matrix);
```

### Matrix Norm

The `norm` function, defined in the `functions.h` header, calculates the
Frobenius norm (L2 norm) of a given matrix. The Frobenius norm of a matrix is
the square root of the sum of the squares of its elements. This function is
useful for measuring the "size" of a matrix.

- Parameters:
  - `A`: input matrix for which the Frobenius norm is to be calculated
- Return: the Frobenius norm of the input matrix as double value

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

// Calculate the Frobenius norm of the matrix
double matrixNorm = clara::norm(matrix);
```

### Eigenvalue and Eigenvector Calculation Function

The `eig` function, defined in the `functions.h` header, calculates the
eigenvalues and eigenvectors of a given square matrix. Eigenvalues and
eigenvectors are fundamental concepts in linear algebra, with applications in
various fields, including quantum mechanics, structural analysis, and machine
learning. The `eig` function provides an easy way to calculate the eigenvalues
and eigenvectors of a square matrix.

- Parameters:
  - `A`: the input square matrix for which eigenvalues and eigenvectors are to
    be calculated
- Return containing
  - the eigenvalues as a dynamic column vector of complex number
    (`dyn_col_vect<cplx>`).
  - the eigenvectors as a complex matrix (`cmat`).
- Throws exception if the input amtrix haas a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

Eigen::MatrixXcd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

// Calculate eigenvalues and eigenvectors of the matrix
std::pair<clara::dyn_col_vect<clara::cplx>, clara::cmat> eigenData = clara::eig(matrix);
clara::dyn_col_vect<clara::cplx> eigenvalues = eigenData.first;
clara::cmat eigenvectors = eigenData.second;
```

### Eigenvalue Calculation Function

The `evals` function, defined in the `functions.h` header, calculates the
eigenvalues of a given square matrix. Eigenvalues are important values
associated with a matrix and find applications in various mathematical and
scientific fields.

- Parameters:
  - `A`: the input square matrix for which eigenvaleus are to be calculated
- Returns: a dynamic column vector of complexx numbers (`dyn_col_vec<cplx>`)
  representing the eigenvalues of the input matrix
- Throw exception if the input matri has a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

Eigen::MatrixXcd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

// Calculate eigenvalues of the matrix
clara::dyn_col_vect<clara::cplx> eigenvalues = clara::evals(matrix);
```

### Eigenvector calculation Function

The `evects` function, defined in the `functions.h` header, calculates the
eigenvectors of a given square matrix. Eigenvectors are associated with
eigenvalues and play a crucial role in various mathematical and scientific
applications.

- Parameters:
  - `A`: the input square matrix for which eigenvectors are to be calculated
- Return complex matrix (`cmat`) containing the eigenvectors og the input
  matrix. Each column of the matrix corresponds to an eigenvector
- Exception

```cpp
#include "functions.h"

Eigen::MatrixXcd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

// Calculate eigenvectors of the matrix
clara::cmat eigenvectors = clara::evects(matrix);
```

### Hermitian Eigenvector and Eigenvlue Calculation Function

The `heig` function, defined in the `functions.h` header, calculates the
eigenvalues and eigenvectors of a Hermitian matrix. Hermitian matrices have real
eigenvalues and orthogonal eigenvectors, making them important in various
mathematical and scientific applications.

- Parameters:
  - `A`: the input hermitian matrix for which eigenvalues and eigenvectors are
    to be calculated
- Return containing
  1. a real vector (`dyn_col_vect<double>`) containing the eigenvalues of the
     input hermitian matrix
  2. a complex matrix (`cmat`) containing the eigenvectors of the input matri.
     each oclumn of the matrix corresponds to an Eigenvectors
- Throw exception if the input matrix has a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

Eigen::MatrixXcd matrix(3, 3);
matrix << 1, 2, 3,
          2, 5, 6,
          3, 6, 9;

// Calculate eigenvalues and eigenvectors of the Hermitian matrix
std::pair<clara::dyn_col_vect<double>, clara::cmat> eigenvaluesAndEigenvectors = clara::heig(matrix);
```

### Hermitian Eigenvalue Calculation Function

The `hevals` function, defined in the `functions.h` header, calculates the
eigenvalues of a Hermitian matrix. Hermitian matrices have real eigenvalues, and
this function provides a straightforward way to compute them. The `hevals`
function calculates the eigenvalues of a Hermitian matrix.

- Parameters:
  - `A`: the input hermitian matrix for which eigenvalues are to be calculated
- Return real vector (`dyn_col_vect<double>`) containing the eigenvalues of the
  input hermitian matrix
- Throw exception if the input matrix has a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

Eigen::MatrixXcd matrix(3, 3);
matrix << 1, 2, 3,
          2, 5, 6,
          3, 6, 9;

// Calculate the eigenvalues of the Hermitian matrix
clara::dyn_col_vect<double> eigenvalues = clara::hevals(matrix);
```

### Hermitian Eigenvector Function

The `hevects` function, defined in the `functions.h` header, calculates the
eigenvectors of a Hermitian matrix. Eigenvectors associated with distinct
eigenvalues of a Hermitian matrix are orthogonal, making this function useful
for various linear algebra applications.

- Parameters:
  - `A`: input matrix Hermitian matrix for which eigenvectors are to be
    calculated
- Return complex matrix(`cmat`) containing the eigenvectors of the input
  hermitian matrix
- Throw exception if the input matrix has a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

Eigen::MatrixXcd matrix(3, 3);
matrix << 1, 2, 3,
          2, 5, 6,
          3, 6, 9;

// Calculate the eigenvectors of the Hermitian matrix
clara::cmat eigenvectors = clara::hevects(matrix);
```

### Singular Value Decomposition (SVD) Function

The `svd` function, defined in the `functions.h` header, computes the Singular
Value Decomposition (SVD) of a given matrix. SVD decomposes a matrix into three
component matrices: U, S, and V, which are useful for various numerical and
linear algebra applications. The `svd` function computes the SVD of a given
matrix and returns the component matrices U, S (diagonal matrix of singular
values), and V.

- Parameters
  - `A`: the input matrixx for which the singular value Decomposition (SVD) is
    to be computed
- Return tuple containing
  - Matrix U (`cmat`): left singular vectors
  - Vector S (`dyn_col_vec<double>`): singular value
  - Matrix V (`cmat`) Right singular vectors
- Throws exception if the input matrix has a size of zero

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 2);
matrix << 1, 2,
          3, 4,
          5, 6;

// Compute the Singular Value Decomposition (SVD) of the matrix
std::tuple<clara::cmat, clara::dyn_col_vect<double>, clara::cmat> svdResult = clara::svd(matrix);

clara::cmat U = std::get<0>(svdResult);
clara::dyn_col_vect<double> S = std::get<1>(svdResult);
clara::cmat V = std::get<2>(svdResult);
```

### Singular Value Decomposition U Matrix Extraction Function

The `svdU` function, defined in the `functions.h` header, computes the left
singular vector matrix U of a given matrix using the Jacobi Singular Value
Decomposition (SVD) algorithm. The left singular vector matrix U is an
orthogonal matrix that spans the same subspace as the columns of the original
matrix.

- Parameters:
  - `A`: inout matri for which the left singular vector matrix U is to be
    computed
- Return complex matrix (`cmat`) containing the left singular vector matrix U of
  the input matrix
- Throw exception if the input matrix has a size of zero

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 2);
matrix << 1, 2,
          3, 4,
          5, 6;

// Compute the left singular vector matrix U
clara::cmat leftSingularVectors = clara::svdU(matrix);
```

### Singular Value Decomposition V Matrix Extraction Function

The `svdV` function, defined in the `functions.h` header, computes the right
singular vector matrix V of a given matrix using the Jacobi Singular Value
Decomposition (SVD) algorithm. The right singular vector matrix V is an
orthogonal matrix that spans the same subspace as the rows of the original
matrix.

- Parameters:
  - `A`: the input matri for which the right singular vector matrix V is to be
    computed
- Return complex matrix (`cmat`) containing the right singular vector matrix V
  of the input matrix

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 2);
matrix << 1, 2,
          3, 4,
          5, 6;

// Compute the right singular vector matrix V
clara::cmat rightSingularVectors = clara::svdV(matrix);
```

### Matrix Function Evaluation Function

The `funm` function, defined in the `functions.h` header, evaluates a complex
matrix function of a given matrix using the provided function pointer `f`. The
function computes the matrix function by diagonalizing the input matrix,
applying the function element-wise to the eigenvalues, and then reconstructing
the matrix using the eigenvectors. The `funm` function computes the matrix
function `f(A)` of a given matrix `A` using the provided complex function
pointer `f`. It returns the resulting matrix.

- Parameters:
  - `A`: the input matrix for which the matrixx function si to be evaluated
  - `f`: a function pointer to the complexx function `f` that will be applied
    element-wise to the eigenvalues of the matrix
- Return comple matrix (`cmat`) containing the result of evaluating the matrix
  function `f(A)`
- Throw exception if the input matrix has a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

// Define a custom complex function
cplx myFunction(const cplx& z) {
    return std::exp(2.0 * z);
}

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

// Compute the matrix function using the custom function
clara::cmat result = clara::funm(matrix, myFunction);
```

### Matrix Square Root Evaluation Function

The `sqrtm` function, defined in the `functions.h` header, computes the square
root of a given matrix using functional calculus. The function computes the
square root of the matrix by applying the `std::sqrt` function element-wise to
the matrix's eigenvalues.

- Parameters:
  - `A`: the input matrix for which the square root matrix is to be computed
- Return complex matrix (`cmat`) containign the square root of the input matrix
- Throw exception if the input matrix has a size of zero, and exception if the
  input matrix is not square.

```cpp
#include "functions.h"

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

// Compute the square root of the matrix
clara::cmat result = clara::sqrtm(matrix);
```

### Matrix Absolute Value Evaluation Function

The `absm` function, defined in the `functions.h` header, computes the absolute
value of a given matrix. The function computes the absolute value of the matrix
by calculating the square root of the product of the matrix and its adjoint.

- Parameters:
  - `A`: the input matrix for which the absolute value matrix is to be computed
- Return complex matrix (`cmat`) containing absolute value of the input matrix
- Throw exception if the input matrix has a size of zero, and exception if the
  input matrix is not square.

```cpp
#include "functions.h"

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

// Compute the absolute value of the matrix
clara::cmat result = clara::absm(matrix);
```

### Matrix Exponential Evaluation Function

The `expm` function, defined in the `functions.h` header, computes the matrix
exponential of a given matrix using functional calculus with the exponential
function.

- Parameters: `A`: the input matrix for which the matrix exponential is to be
  computed
- Return complex matrix (`cmat`) containing the matrix exponential of the input
  matrix
- Throw exception if the input matrix has a size of zero, and if the input
  matrix is not square

```cpp
#include "functions.h"

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

// Compute the matrix exponential
clara::cmat result = clara::expm(matrix);
```

### Matrix Logarithm Evaluation Function

The `logm` function, defined in the `functions.h` header, computes the matrix
logarithm of a given matrix using functional calculus with the natural logarithm
function. The `logm` function calculates the matrix logarithm of a given matrix
`A` using the functional calculus method with the natural logarithm function. It
returns the resulting matrix.

- Parameters:
  - `A`: the input matrix for which the matrix logarithm is to be computed
- Return complex matrix (`cmat`) containing the matrix logarithm of the input
  matrix
- Throw Exception if the input matrixx has a size of zero, and if the input
  matrix is not square

```cpp
#include "functions.h"

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

// Compute the matrix logarithm
clara::cmat result = clara::logm(matrix);
```

### Matrix Sine Function

The `sinm` function, defined in the `functions.h` header, calculates the matrix
sine of a given matrix using functional calculus with the sine function. The
`sinm` function computes the matrix sine of a given square matrix `A` using the
functional calculus method with the sine function. It returns the resulting
matrix.

- Parameters:
  - `A`: the input matrixx for which the matrix sine is to be computed
- Return complex matrix (`cmat`) containing the matrix sine of the input matrix
- Throw exception if the input matrix has a size of zero, and if the input is
  not square

```cpp
#include "functions.h"

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

// Compute the matrix sine
clara::cmat result = clara::sinm(matrix);
```

### Matrixx Cosine Function

The `cosm` function, defined in the `functions.h` header, calculates the matrix
cosine of a given matrix using functional calculus with the cosine function. The
`cosm` function computes the matrix cosine of a given square matrix `A` using
the functional calculus method with the cosine function. It returns the
resulting matrix.

- Parameters:
  - `A`: the input matrix for which the matrix cosine is to be computed
- Return a complex matrix (`cmat`) containing the matrix cosinue of the input
  matrix
- Throw exception if the input matrix has a size of zero, and if the input
  matrix is not square

### Matrix Cosine Function

The `cosm` function, defined in the `functions.h` header, computes the matrix
cosine of a given square matrix using the functional calculus approach with the
cosine function. The `cosm` function computes the matrix cosine of a square
matrix `A` by applying the functional calculus method with the cosine function
to each element of the matrix. The resulting matrix represents the matrix cosine
of the input matrix.

- Parameters:
  - `A`: the input square matrix for which the matrix cosine
- Return complex matrix (`cmat`) representing the matrix cosnue of the input
  matrix
- Throw exception if the input matrix has a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

// Compute the matrix cosine
clara::cmat result = clara::cosm(matrix);
```

### Spectral Matrix Power Function

The `spectralpow` function, defined in the `functions.h` header, computes the
matrix power of a given square matrix using the spectral decomposition method.
The `spectralpow` function calculates the matrix power of a square matrix `A`
raised to a complex exponent `z`. The function decomposes the matrix using its
eigenvalues and eigenvectors, applies the power to each eigenvalue, and
reconstructs the matrix using the spectral decomposition.

- Parameters:
  - `A`: the input square matrix for which the matrix power will be computed
  - `z`: the complex exponent to which the matri will be raised
- Return a complex matrix (`cmat`) representing the matrix `A` raised to the
  power of `z`.
- Throws exception if the input matrix has a size of zero, and exception if the
  input matrix is not square.

```cpp
#include "functions.h"

Eigen::Matrix2cd matrix;
matrix << cplx(1, 2), cplx(3, 4),
          cplx(5, 6), cplx(7, 8);

cplx exponent(2.0, 1.5);

// Compute the matrix power A^z
clara::cmat result = clara::spectralpow(matrix, exponent);
```

### Matrix Power Function

The `powm` function, defined in the `functions.h` header, calculates the matrix
power of a given square matrix using the SQUARE-AND-MULTIPLY algorithm. The
`powm` function computes the matrix power of a square matrix `A` raised to a
positive integer exponent `n`. The function employs the SQUARE-AND-MULTIPLY
algorithm, which efficiently computes the matrix power using binary
exponentiation.

- Parameters:
  - `A`: the input square matrix for which the matrix power will be computed
  - `n`: the positive integer exponent to which the matrix will be raised
- Return a dynamic matrix (`dyn_mat`) representing the matrix `A` raised to the
  power of `n`
- Throws exception if the input matrix, has a size of zero, and exception if the
  input matrix is not square

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

idx exponent = 3;

// Compute the matrix power A^n
clara::dyn_mat<double> result = clara::powm(matrix, exponent);
```

### Schatten p-Norm Function

The `schatten` function, defined in the `functions.h` header, computes the
Schatten p-norm of a given matrix. The `schatten` function calculates the
Schatten p-norm of a matrix `A` using its singular values. The Schatten p-norm
is a generalization of the matrix norm, and it quantifies the "size" of the
matrix based on its singular values. The function is useful for various
applications in numerical linear algebra and signal processing.

- Parameters:
  - `A`: the input matrix for which the schatten p-norm will be computed
  - `p`: the exponent `p` for the schatten p-norm computation. Must be greater
    than or equal to 1
- Return double value representing the schatten p-norm of the matrix `A`
- Throw exception if the input matrix has a size of zero, and exception if the
  value of `p` is less than 1

```cpp
#include "functions.h"

Eigen::MatrixXd matrix(3, 3);
matrix << 1, 2, 3,
          4, 5, 6,
          7, 8, 9;

double p = 2.5;

// Calculate the Schatten p-norm of the matrix
double result = clara::schatten(matrix, p);
```

### Component-Wise Function Application

The `cwise` function, defined in the `functions.h` header, applies a given unary
function component-wise to each element of a matrix. The `cwise` function allows
you to apply a unary function to each element of a matrix in a component-wise
manner. This can be useful for various types of element-wise transformations,
such as applying a mathematical function to each element of a matrix.

- Parameters:
  - `A`: the input matrix for which the component-wise function will applied
  - `f`: a pointer to a unary function that takes an element of the input matrix
    type and returns an element of the desired output scalar type
- Return a matrix of type `dyn_mat<OutputScalar>` with the same dimensions as
  the input matrix, where each element is obtained by applying the function `f`
  to the corresponding element of the input matrix.
- Throw exception if the input matrix has a size of zero

```cpp
#include "functions.h"

Eigen::MatrixXd inputMatrix(3, 3);
inputMatrix << 1, 2, 3,
               4, 5, 6,
               7, 8, 9;

// Define a function to apply component-wise
auto square = [](const double& x) { return x * x; };

// Apply the square function component-wise to the input matrix
clara::dyn_mat<double> result = clara::cwise(inputMatrix, square);
```

### Kron Function

The `kron` function is a template function that performs the Kronecker product
operation on a single input matrix or matrix-like object. It returns a
dynamically allocated matrix of the appropriate type containing the Kronecker
product result.

- Parameters:
  - `head`: a constant refernece to the input matrixx or matrix-like object. The
    input can be any type `T` that provides the necessart interface for
    matrix-like operations, such as Eigen matrices
- Return dynamically allocated matrix of the same scalar types as the input
  matrix. This matrix contains the result of the Kronecker product operation
  applied the input matrix.

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create matrices A and B
MatrixType A; // Initialize A
MatrixType result;

// Call the kron function
result = kron(A);

// 'result' now contains the Kronecker product of matrix A
```

### Kronpow Function

The `kronpow` function computes the Kronecker power of a given matrix `A` to the
power `n`. It returns a dynamically allocated matrix containing the result of
the operation.

- Parameters:
  - `A`: constant reference to the input matrix or matrix-like object of type
    `Eigen::MatrixBase<Derived>`
  - `n`: an intenger representing the power to which the Kronecker product of
    the matrix `A` is raised
- Return dynamically allocated matrixx of the same scalar type as the input
  matrix. This matrix contains the result of the Kronecker power operations
  applied to the input matrix
- Throw exxception if the input matrix has zero size, and if the value of `n`is
  zero

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create a matrix A
MatrixType A; // Initialize A
int power = 3; // Kronecker power

try {
    // Calculate Kronecker power using kronpow
    MatrixType result = kronpow(A, power);
    // 'result' now contains the Kronecker power of matrix A raised to the power of 3
} catch (const exception::ZeroSize& e) {
    // Handle zero-size matrix exception
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range power exception
}
```

### `dirsum` Function

The `dirsum` function computes the direct sum of a list of matrices provided in
a vector. It returns a dynamically allocated matrix that represents the direct
sum of all the input matrices.

- Parameters:
  - `As`: vector containing constant references to input matrices or matrix-like
    objects of type `Derived`. The input matrices represent the component of the
    direct sum
- Return a dynamically allocated matrix of the same scalar type as the input
  matrices. This matrix contains the result of the direct sum operation applied
  to the input matrices.
- Throw exception if any of the input matrices in the vector have zero size

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create matrices A, B, and C
MatrixType A; // Initialize A
MatrixType B; // Initialize B
MatrixType C; // Initialize C
std::vector<MatrixType> matrices = {A, B, C};

try {
    // Calculate direct sum using dirsum
    MatrixType result = dirsum(matrices);
    // 'result' now contains the direct sum of matrices A, B, and C
} catch (const exception::ZeroSize& e) {
    // Handle zero-size matrix exception
}
```

### `dirsumpow` Function

The `dirsumpow` function computes the direct sum power of a given matrix `A` to
the power `n`. It returns a dynamically allocated matrix containing the result
of the operation.

- Parameters:
  - `A`: constant reference to the input matrix or matrix-like object of type
    `Eigen::MatrixBase<Derived>`
  - `n`: integer representing the power to which the direct sum of the matrix
    `A` is raised
- Return a dynamically allocated matrix of the same scalar type as the input
  matrix. This matrix contains the result of the direct sum power operation
  applied to the input matrix
- Throws exception if the input matrixx has zero size, and if the value of `n`
  is zero

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create a matrix A
MatrixType A; // Initialize A
int power = 3; // Direct sum power

try {
    // Calculate direct sum power using dirsumpow
    MatrixType result = dirsumpow(A, power);
    // 'result' now contains the direct sum power of matrix A raised to the power of 3
} catch (const exception::ZeroSize& e) {
    // Handle zero-size matrix exception
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range power exception
}
```

### `reshape` Functions

The `reshape` function reshapes a given matrix `A` to have a new number of rows
and columns, while maintaining the order of its elements. It returns a
dynamically allocated matrix containing the reshaped data.

- Parameters:
  - `A`: constant reference to the input matrix or matrix-like object of type
    `Eigen::MatrixBase<Derived>`
  - `rows`: integer representing the number of rows in the reshaped matrix
  - `cols`: integer representing the number of columns in the reshaped matrix
- Return dynamically allocated matrix of the same scalar types as the input
  matrix. This matri contains the data from the input matrix `A` reshapeed to
  the specified number of rows and columns
- Throws exception if the input matrix has zero size, and if the total number of
  elements in the input matrix does not match the product of the specified
  number of rows and columns for the reshaped matrix.

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create a matrix A
MatrixType A; // Initialize A
int newRows = 3; // New number of rows
int newCols = 4; // New number of columns

try {
    // Reshape matrix A using reshape
    MatrixType result = reshape(A, newRows, newCols);
    // 'result' now contains the reshaped matrix with 3 rows and 4 columns
} catch (const exception::ZeroSize& e) {
    // Handle zero-size matrix exception
} catch (const exception::DimsMismatchMatrix& e) {
    // Handle dimension mismatch exception
}
```

### `comm` Function

The `comm` function calculates the commutator of two square matrices, `A` and
`B`. It returns a dynamically allocated matrix containing the result of the
commutator operation, which is defined as `A * B - B * A`.

- Parameters:
  - `A`: constant reference to the first input matrix or matrix-like object of
    type `Eigen::MatrixBase<Derived>`
  - `B`: constant reference to the second input matrix or matrix-like object of
    type `Eigen::MatrixBase<Derived2>`
- Return dynamically allocated matrix of the same scalar type as the input
  matrices. This matri contains the result of the commutator operation
  (`A * B - B * A`) applied to the input matrices.
- Throw Exception if the scalar types of matrices `A` and `B` are not the same,
  if either of the input matrices has zero size, if either of the input matrices
  is not a square matrix and if the dimensions of matrices `A` and `B` are not
  equal.

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create matrices A and B
MatrixType A; // Initialize A
MatrixType B; // Initialize B

try {
    // Calculate commutator using comm
    MatrixType result = comm(A, B);
    // 'result' now contains the commutator of matrices A and B
} catch (const exception::TypeMismatch& e) {
    // Handle type mismatch exception
} catch (const exception::ZeroSize& e) {
    // Handle zero-size matrix exception
} catch (const exception::MatrixNotSquare& e) {
    // Handle non-square matrix exception
} catch (const exception::DimsNotEqual& e) {
    // Handle dimension mismatch exception
}
```

### `anticomm` Function

The `anticomm` function calculates the anticommutator of two square matrices,
`A` and `B`. It returns a dynamically allocated matrix containing the result of
the anticommutator operation, which is defined as `A * B + B * A`.

- Parameters:
  - `A`: constant reference to the first input matrix or matrix-like object of
    type `Eigen::MatrixBase<Derived1>`
  - `B`: constant refernece to the second input matrix or matrix-like object of
    type `Eigen::MatrixBase<Derived2>`
- Return dynamically allocated matrix of the same scalar type as the input
  matrices. This matrix contains the result of the anticommutator
  (`A * B + B * A`) applied to the input matrices.
- Throw exception if the scalar type of matrices `A` and `B` are not the same,
  if the either of the input marcies has zero size, if either of the input
  matrices is not a square matrix, and if the dimension of matrices `A` and `B`
  are not equal.

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create matrices A and B
MatrixType A; // Initialize A
MatrixType B; // Initialize B

try {
    // Calculate anticommutator using anticomm
    MatrixType result = anticomm(A, B);
    // 'result' now contains the anticommutator of matrices A and B
} catch (const exception::TypeMismatch& e) {
    // Handle type mismatch exception
} catch (const exception::ZeroSize& e) {
    // Handle zero-size matrix exception
} catch (const exception::MatrixNotSquare& e) {
    // Handle non-square matrix exception
} catch (const exception::DimsNotEqual& e) {
    // Handle dimension mismatch exception
}
```

### `prj` Functions

The `prj` function calculates the projection matrix of a given column vector `A`
onto its own subspace. It returns a dynamically allocated matrix representing
the projection.

- Parameters:
  - `A`: constant reference to the input column vector or vector-like object
    type `Eigen::MatrixBase<Derived>`
- Return a dynamically allocated matrix of the same scalar type as the input
  vector. This matrix represent the projection of the input vector `A` into its
  own subspace
- Throw exception if the input vector has zero size, and if the input is not a
  column vector.

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create a column vector A
VectorType A; // Initialize A

try {
    // Calculate projection using prj
    MatrixType result = prj(A);
    // 'result' now contains the projection matrix of vector A onto its own subspace
} catch (const exception::ZeroSize& e) {
    // Handle zero-size vector exception
} catch (const exception::MatrixNotCvector& e) {
    // Handle non-column vector exception
}
```

### `grams` Functions

he `grams` function performs the Gram-Schmidt orthogonalization process on a
list of input column vectors. It returns a dynamically allocated matrix
containing the resulting orthogonalized vectors.

- Parameters:
  - `A`: vector containing constant references to input column vector or
    vector-lke objects
- Return a dynamically allocated matrix of the same scalar type as the input
  vectors. This matrix contains the resulting orthogonalized vectors obtained
  through the Gram-Schmidt process.
- Throw exception if eigher the input vector list or any of the input vectors
  have zero size, if the first vector in the list not a column vectors, and if
  the dimensions of vectors in the list are not equal to the dimensional of the
  first vector

```cpp
#include "functions.h" // Include the appropriate matrix library

// Create column vectors A, B, and C
VectorType A; // Initialize A
VectorType B; // Initialize B
VectorType C; // Initialize C
std::vector<VectorType> vectors = {A, B, C};

try {
    // Perform Gram-Schmidt orthogonalization using grams
    MatrixType result = grams(vectors);
    // 'result' now contains the orthogonalized vectors obtained through the Gram-Schmidt process
} catch (const exception::ZeroSize& e) {
    // Handle zero-size vector exception
} catch (const exception::MatrixNotCvector& e) {
    // Handle non-column vector exception
} catch (const exception::DimsNotEqual& e) {
    // Handle dimension mismatch exception
}
```

### `n2multiidx` Functions

The `n2multiidx` function converts a linear index `n` into a multi-index
representation, given a set of dimensions. It returns a vector containing the
multi-index corresponding to the linear index.

- Parameters:
  - `n`: integer representing the linear index to be converted
  - `dims`: vector of integers representing the dimensions of the
    multi-dimensional space
- Return vector of integers containing the multi-index representation of the
  given linear index `n` with respect to the specified dimension.
- Throw exception if the dimension vector `dims` is empty or contains a zero
  elements, if the value of `n` is greater than or equal to the total number of
  elements in the multi-dimensional space defined by the dimensions.

```cpp
#include "functions.h" // Include the appropriate library

// Define dimensions and linear index
std::vector<idx> dimensions = {3, 4, 5}; // Dimensions of the multi-dimensional space
idx linearIndex = 17; // Linear index to convert

try {
    // Convert linear index to multi-index using n2multiidx
    std::vector<idx> multiIndex = n2multiidx(linearIndex, dimensions);
    // 'multiIndex' now contains the multi-index representation of the linear index 17
} catch (const exception::DimsInvalid& e) {
    // Handle invalid dimensions exception
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range linear index exception
}
```

### `multiidx2n` Functions

The `multiidx2n` function converts a multi-index representation to a linear
index, given a set of dimensions. It returns a non-negative integer index
corresponding to the provided multi-index and dimensions.

- Parameters:
  - `midx`: vector of integers representing the multi-index
  - `dims`: vector of integers representing the dimensions of the
    multi-dimensional space.
- Return a non-negative integer index representing the linear index
  corresponding to the provided multi-index and dimensions
- Throw exception if the dimension vector `dims` is empty or contains a zero
  elements, and if any elements of the multi-index vector `midx` exceeds the
  corresponding dimension in the `dims` vector

```cpp
#include "functions.h" // Include the appropriate library

// Define dimensions and multi-index
std::vector<idx> dimensions = {3, 4, 5}; // Dimensions of the multi-dimensional space
std::vector<idx> multiIndex = {1, 2, 3}; // Multi-index to convert

try {
    // Convert multi-index to linear index using multiidx2n
    idx linearIndex = multiidx2n(multiIndex, dimensions);
    // 'linearIndex' now contains the linear index corresponding to the multi-index {1, 2, 3}
} catch (const exception::DimsInvalid& e) {
    // Handle invalid dimensions exception
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range multi-index exception
}
```

### `mket` Functions

The `mket` function constructs a ket vector representing a quantum state with a
specified subsystem configuration. It returns a dynamically allocated ket vector
with a single non-zero entry at the position corresponding to the multi-index
specified by the mask.

- Parameters
  - `mask`: vector of integers representing the multi-index specifying the
    subsystem configuration
  - `dims`: vector of integeres representing the dimensions of each subsystem
- Return a dynamically allocated ket vector, which is a quantum state with a
  single non-zero entry at the position corresponding to the specified
  multi-index

```cpp
#include "functions.h" // Include the appropriate library

// Define subsystem configuration and dimensions
std::vector<idx> subsystemConfig = {1, 2, 0}; // Multi-index specifying subsystem configuration
std::vector<idx> dimensions = {3, 4, 2}; // Dimensions of the subsystems

try {
    // Create ket vector representing the quantum state using mket
    ket quantumState = mket(subsystemConfig, dimensions);
    // 'quantumState' now contains the ket vector representing the quantum state with the specified subsystem configuration
} catch (const exception::ZeroSize& e) {
    // Handle zero-size subsystem configuration exception
} catch (const exception::DimsInvalid& e) {
    // Handle invalid dimensions exception
} catch (const exception::SubsysMismatchdims& e) {
    // Handle subsystem and dimension mismatch exception
}
```

### `mprj` Functions

The `mprj` function constructs a projection operator that projects a quantum
state onto a specified subsystem configuration. It returns a dynamically
allocated complex matrix representing the projection operator.

- Parameters:
  - `mask`: A vector of integeres representing the multi-index specifying the
    subsystem configuration
  - `dims`: A vector integeres representing the dimension of each subsystem
- Returns a dynamically allocated complex matrix, which is a projection operatio
  that projects a quantum state into the specified subsystem configuration
- Throw exception if the number of subsystem `N` is zero or the dimension vector
  `dims` is empty or contains a zero element.

```cpp
#include "functions.h" // Include the appropriate library

// Define subsystem configuration and dimensions
std::vector<idx> subsystemConfig = {1, 2, 0}; // Multi-index specifying subsystem configuration
std::vector<idx> dimensions = {3, 4, 2}; // Dimensions of the subsystems

try {
    // Create projection operator using mprj
    cmat projectionOperator = mprj(subsystemConfig, dimensions);
    // 'projectionOperator' now contains the complex matrix representing the projection operator for the specified subsystem configuration
} catch (const exception::ZeroSize& e) {
    // Handle zero-size subsystem configuration or dimension exception
} catch (const exception::SubsysMismatchdims& e) {
    // Handle subsystem and dimension mismatch exception
}
```

### `abssq` Function

The `abssq` function calculates the squared magnitudes of the elements in a
container or an Eigen matrix and returns them as a vector of double values.

- Parameters
  - `c`: container (e.g vector, array) of elements for which squared magnitures
    are to be calculated
  - `A`: an eigen matri whose squared magnitudes of lements are to be calculated
- Return a vector of double value containing the squared magnitureds of the
  elements in the provided container of Eigen matrix
- Throw exception if the input container or eigen matrix has zero size

```cpp
#include "functions.h" // Include the appropriate library

// Create a vector or array of elements
std::vector<double> elements = {2.5, -3.1, 1.0};

try {
    // Calculate squared magnitudes of elements using abssq
    std::vector<double> squaredMagnitudes = abssq(elements);
    // 'squaredMagnitudes' now contains the squared magnitudes of the elements
} catch (const exception::ZeroSize& e) {
    // Handle zero-size container exception
}
```

### `sum` Functions

he `sum` function calculates the sum of elements in a range defined by the
provided input iterators. It returns the computed sum value.

- Parameters:
  - `first`: iterator pointing to the beginning of the range
  - `last`: input iterator pointing one position past the end of the range
- Return the sum of elements in the specified range

```cpp
#include "functions.h" // Include the appropriate library

// Create an array of numbers
double numbers[] = {1.5, 2.0, 3.2, 0.8};

// Calculate the sum of numbers using sum
double totalSum = sum(std::begin(numbers), std::end(numbers));
// 'totalSum' now contains the sum of elements in the array
```

### `prod` Functions

The `prod` function calculates the product of elements in a range defined by the
provided input iterators. It returns the computed product value.

- Parameters:
  - `first`: input iterator pointing to the beginning of the range
  - `last`: input iterator pointing one position past the end of the range
- Return the product of elements in the specified range

```cpp
#include "functions.h" // Include the appropriate library

// Create an array of numbers
double factors[] = {2.0, 3.0, 1.5, 0.5};

// Calculate the product of factors using prod
double totalProduct = prod(std::begin(factors), std::end(factors));
// 'totalProduct' now contains the product of elements in the array
```

### `rho2pure` Functions

The `rho2pure` function transforms a Hermitian matrix representing a quantum
state into a pure state vector. It calculates the most significant eigenvector
associated with the largest non-zero eigenvalue of the Hermitian matrix and
returns it as a pure state vector.

- Parameters
  - `A`: eigen matrix representing the Hermitian quantum state
- Return dynamically allocated column vector, which represent the pure state
  vector associated with the most significant eigenvector of the Hermitian
  matrix

```cpp
#include "functions.h" // Include the appropriate library

// Create a Hermitian matrix representing a quantum state
dyn_mat<double> quantumState = ...; // Initialize your matrix

try {
    // Transform Hermitian matrix into a pure state vector using rho2pure
    dyn_col_vect<double> pureStateVector = rho2pure(quantumState);
    // 'pureStateVector' now contains the pure state vector associated with the most significant eigenvector
} catch (const exception::ZeroSize& e) {
    // Handle zero-size matrix exception
} catch (const exception::MatrixNotSquare& e) {
    // Handle non-square matrix exception
}
```

### `complement` Functions

The `complement` function computes the complement of a given subset of indices
with respect to a larger index range. It returns a vector containing the indices
that are not present in the input subset.

- Parameters
  - `subsys`: vector of indices representing the subset for which the complement
    needs to be calculated
  - `N`: the size of the integer index range
- Return vector containing the indices that are not present in the input
  `subsys` subset.
- Throws exception if the value of `N` is less than the size of the input
  `subsys` vector

```cpp
#include "functions.h" // Include the appropriate library

// Define a subset of indices and the larger index range
std::vector<idx> subsetIndices = {1, 3};
idx largerRangeSize = 5;

try {
    // Calculate the complement of the subset indices using complement
    std::vector<idx> complementIndices = complement(subsetIndices, largerRangeSize);
    // 'complementIndices' now contains the indices not present in the subset
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range exception
}
```

### `rho2bloch` Functions

The `rho2bloch` function computes the Bloch vector components corresponding to a
given density matrix representing a qubit state. It returns a vector containing
the X, Y, and Z components of the Bloch vector.

- Parameters:
  - `A`: Eigen matri representing the density matri of the qubit state
- Return vector containing X, Y and Z components of the Bloch vector associated
  with the qubit state
- Throw exceptions if the input matrix `A` is not a valid qubit matrix

```cpp
#include "functions.h" // Include the appropriate library

// Create a density matrix representing a qubit state
dyn_mat<std::complex<double>> qubitDensityMatrix = ...; // Initialize your matrix

try {
    // Calculate the Bloch vector components using rho2bloch
    std::vector<double> blochVector = rho2bloch(qubitDensityMatrix);
    // 'blochVector' now contains the X, Y, and Z components of the Bloch vector
} catch (const exception::NotQubitMatrix& e) {
    // Handle not qubit matrix exception
}
```

### `bloch2rho` Functions

The `bloch2rho` function constructs a qubit density matrix from a given Bloch
vector. It calculates the qubit density matrix using the components of the Bloch
vector and returns the resulting density matrix.

- Parameters:
  - `r`: vector containing the X, Y, and Z components of the bloch vector
- Return a complex-valued matrix representing the qubit density matrix
- Throw exception if the input vector `r` is not 3-dimensional

```cpp
#include "functions.h" // Include the appropriate library

// Define the Bloch vector components
std::vector<double> blochVector = {0.5, -0.3, 0.7};

try {
    // Create the qubit density matrix using bloch2rho
    cmat densityMatrix = bloch2rho(blochVector);
    // 'densityMatrix' now contains the qubit density matrix corresponding to the Bloch vector
} catch (const exception::CustomException& e) {
    // Handle custom exception due to incorrect dimensionality of 'r'
}
```

### `operator*" _ket` Functions

The `operator"" _ket` user-defined literal enables the creation of a quantum ket vector directly from a binary string representation. It constructs a quantum ket vector using the binary representation and returns it.

- Return a dynamically allocated ket vector representing the quantum state defined by the binary string
- Throw exception if the input binary representation contains character than '0' and '1'

```cpp
#include "functions.h" // Include the appropriate library

// Create a quantum ket vector using the user-defined literal
ket ketVector = "101_ket"_ket;

try {
    // 'ketVector' now contains the quantum ket vector representing the binary state "101"
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range exception due to invalid binary representation
}
```

### `operator*" _bra` Function

The `operator"" _bra` user-defined literal enables the creation of a quantum bra vector directly from a binary string representation. It constructs a quantum bra vector using the binary representation and returns it.

- Return a dynamically allocated bra vector representing the quantum state defined by the binary string
- Throw exception if the input binary representation contains characters other then '0'and '1'

```cpp
#include "functions.h" // Include the appropriate library

// Create a quantum bra vector using the user-defined literal
bra braVector = "101_bra"_bra;

try {
    // 'braVector' now contains the quantum bra vector representing the binary state "101"
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range exception due to invalid binary representation
}
```

### `operator"" _prj` Function

The `operator"" _prj` user-defined literal enables the creation of a qubit projector matrix directly from a binary string representation. It constructs a qubit projector matrix using the binary representation and returns it.

- Return complex-valud matrix representing the qubit projector matrix
- Throw exceptions if the input binary representation contains characters other than '0' and '1'.

```cpp
#include "functions.h" // Include the appropriate library

// Create a qubit projector matrix using the user-defined literal
cmat projectorMatrix = "101_prj"_prj;

try {
    // 'projectorMatrix' now contains the qubit projector matrix for the binary state "101"
} catch (const exception::OutOfRange& e) {
    // Handle out-of-range exception due to invalid binary representation
}
```
