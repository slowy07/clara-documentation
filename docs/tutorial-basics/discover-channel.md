---
sidebar_position: 2
---

# Discover Channel Operation On Clara

## Perform various quantum channel operations

Kraus operators are a mathematical tool used to describe the evolution of quantum state. Kraus operators are a set of operators that act on a quantum state and transform it into another quantum state. They are typically used to describe the interaction of a quantum system with its environment. on this code we create some complex quantum computations using quantum states, kraus operator choi matrices, it seems to perform operations related to quantum channels, eigenvalues, and verification of actions. the specific functionallity and meaning of various library functions on clara.

The kraus operators for quantum system are defined as follow
- **Completness relation**: the sum of all kraus operators must be equal to the identity operator. this ensure that the evolution of the quantum state is reversible
- **Positivy**: all kraus oeprator must be positive semidefinite. This ensure that the evolution of the quantum state does not violate the laws of quantum mechanics


```cpp
idx nk = 5; // kraus
idx D = 3; // dimension
```
Description :
Initialize the variables `nk` and `D`, which represent the number of kraus operators and the dimension of the quantum space.<br/><br/>

```cpp
cmat rho_in = randrho(D);
```

Description:
Generate random density matrix `rho_in` with dimension `D`. a density matrix is used to describe the state of a quantum system, which can be mixed (i.e probabilistic) instied of pure.<br/><br/>

```cpp
cmat rho_out = clara::apply(rho_in, Ks);
```
Description:
Applies quantum channel represented by the kraus operator `Ks` to the input state `rho_in`, producing the output state `rho_out`.<br/><br/>

```cpp
cmat choim = kraus2choi(Ks);
```

Description:
Choi Matrix is a mathematical object that represents a completely positive map. Completely positive maps are type of linear map that can be used to describe the evolution of quantum states. The choi matrix of completely positive map is defined as follows
```tex
$\C(T) = Tr_B[T(I_A \otimes |v⟩⟨v|)]
```
where:
- `T` is the completely positive map
- `I_A` is the identity operator on the input Hilbert space of T
- `|v⟩⟨v|` is a pure state on the output Hilbert space of T
- `Tr_B` is the partial trace over the output Hilbert space of T

calculate and display the eigenvalues of the choi matrix and their sum
```cpp
std::cout << "the eigenvalues of the choi matrix are: \n" << disp(transpose(hevals(choim))) << std::endl;
std::cout << "their sum is: " << sum(hevals(choim)) << std::endl;
```
```
the eigenvalues of the choi matrix are:
0   0   0   0   0.131089   0.222444   0.470062   0.851272   1.32513
their sum is: 3
```

