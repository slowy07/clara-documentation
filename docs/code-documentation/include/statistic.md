# Statistic

The following is an explanation of the C++ header code provided. This code
defines functions for various statistical computations using probability
distributions.

## `namespace clara`

The code is wrapped in the `clara` namespace to encapsulate the defined
functions.

### `uniform(idx N)`

This function generates a vector representing a uniform probability distribution
of size `N`.

- Parameters:

  - `N`: Size of the alphabet for the uniform distribution.

- Returns: A vector of size `N` with each element set to 1/N.

### `marginalX(const dmat& probXY)`

This function computes the marginal distribution of a variable 'X' given a joint
probability distribution.

- Parameters:

  - `probXY`: A matrix representing the joint probability distribution of 'X'
    and 'Y'.

- Returns: A vector representing the marginal distribution of 'X'.

### `marginalY(const dmat& probXY)`

This function computes the marginal distribution of a variable 'Y' given a joint
probability distribution.

- Parameters:

  - `probXY`: A matrix representing the joint probability distribution of 'X'
    and 'Y'.

- Returns: A vector representing the marginal distribution of 'Y'.

### `avg(const std::vector<double>& prob, const Container& X)`

This function calculates the average (expected value) of a random variable 'X'
based on its probability distribution.

- Parameters:

  - `prob`: Probability vector representing the distribution of 'X'.
  - `X`: STL-like container representing values of 'X'.

- Returns: The average value of 'X' based on its probability distribution.

### `cov(const dmat& probXY, const Container& X, const Container& Y)`

This function calculates the covariance between two random variables 'X' and 'Y'
based on their joint probability distribution.

- Parameters:

  - `probXY`: Matrix representing the joint probability distribution of 'X' and
    'Y'.
  - `X`: STL-like container representing values of 'X'.
  - `Y`: STL-like container representing values of 'Y'.

- Returns: The covariance between 'X' and 'Y' based on their joint probability
  distribution.

### `var(const std::vector<double>& prob, const Container& X)`

This function calculates the variance of a random variable 'X' based on its
probability distribution.

- Parameters:

  - `prob`: Probability vector representing the distribution of 'X'.
  - `X`: STL-like container representing values of 'X'.

- Returns: The variance of 'X' based on its probability distribution.

### `sigma(const std::vector<double>& prob, const Container& X)`

This function calculates the standard deviation (sigma) of a random variable 'X'
based on its probability distribution.

- Parameters:

  - `prob`: Probability vector representing the distribution of 'X'.
  - `X`: STL-like container representing values of 'X'.

- Returns: The standard deviation of 'X' based on its probability distribution.

### `cor(const dmat& probXY, const Container& X, const Container& Y)`

This function calculates the correlation coefficient between two random
variables 'X' and 'Y' based on their joint probability distribution.

- Parameters:

  - `probXY`: Matrix representing the joint probability distribution of 'X' and
    'Y'.
  - `X`: STL-like container representing values of 'X'.
  - `Y`: STL-like container representing values of 'Y'.

- Returns: The correlation coefficient between 'X' and 'Y' based on their joint
  probability distribution.
