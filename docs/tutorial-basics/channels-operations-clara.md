---
sidebar_position: 3
---

# Channels operations

In this section we will eplain the usage of the clara with provided c++ that
demonstrate various quantum channels operations using `clara` package.

## Code overview

the code perform operations on quantum states and quantum channels using the
`clara` library. It involves various concepts such as partial transpose,
measurement channels, superpoperator matrix, choi matrix, partial trace, and von
Neumann entropy.

## Channels Operations Function

the `ChannelsOperations` function demonstrates the quantum channels oeprations
step by step

**Initial State Creation**

```cpp
cmat rho = st.pb00;
std::cout << "initial state " << std::endl;
std::cout << disp(rho) << std::endl;
```

- the initial quantum state `rho` is set to `st.pb00`
- the state is displayed using `disp` function<br/>

**Partial Transpose**

```cpp
cmat rhoTA = ptranspose(rho, {0});
std::cout << "eigenvalues of the partial transpose of bell-0 state are " << std::endl;
std::cout << disp(transpose(hevals(rhoTA))) << std::endl;
```

- the partial transpose of the quantum state is computed using `ptranspose` with
  the first subsystem transpose
- the eigenvalues of the partially transposed state are calclated and displayed

**Measurement Channel Setup**

```cpp
std::vector<cmat> Ks{PZ0, PZ1};
```

- A measurement channels is set up using two kraus operators `pz0` and `pz1`

**superpoperator matrix**

```cpp
std::cout << "superpoperator matrix of channels: " << std::endl << disp(kraus)
```

- The superpoperator of the measturement channel is computed using `kraus2super`
  and displayed.

**Choi Matrix**

```cpp
std::cout << "choi matrix of the channels: " << std::endl;
std::cout << disp(kraus2choi(Ks)) << std::endl;
```

- The choi matrix of the measurement channels is computed using `kraus2choi` and
  displayed.

**Applying Measurement Channels**

```cpp
cmat rhoOut = apply(rho, Ks, {0});
std::cout << "after applying the measurement channel on the first qubit" << std::endl;
std::cout << disp(rhoOut);
```

- the measurement channel is applied to the quantum state, specifically to the
  first subsystem
- the resulting state `rhoOut` displayed

**Partial Trace and Entropy**

```cpp
cmat rhoA = ptrace(rhoOut, {1});
std::cout << "after partially tracing down the second subsystem " << std::endl
          << disp(rhoA) << std::endl;

double entropies = entropy(rhoA);
std::cout << "entropy: " << entropies << std::endl;
```

- the partial trace is taken over the secon subsystem, resulting in the state
  `rhoA`, which is displayed.
- the von Neumann entropy of the resulting is computed and displayed.

## Other Test

you can test the given code in `example` with docker. Docker is platform that
allow to package and run applications in isolated environment called containers.
Containers are lightweight and portable, making them easy to deploy and manage.

### Docker Setup

make sure to have docker installed on system. If not, the download and install
documenation from the official
[Docker Website](https://www.docker.com/get-started/)

### Dockerfile Explanation

the provided Dockerfile is used to create a Docker image containing the
necessary environment for building and running the C++ program (specifically
`channels operation clara`)

```Dockerfile title=Dockerfile.channels
# CALL BASE IMAGE WITH UBUNTU 18.04
FROM ubuntu:18.04

# COPY FILE TO LOCAL CONTAINER
WORKDIR /app
COPY . .

# INSTALL MODULE
RUN apt-get update && apt install libeigen3-dev libomp-dev gcc -y
WORKDIR /usr/local/include
RUN cp -r /usr/include/eigen3/Eigen .

# BUILD BINARY FILE
WORKDIR /app
RUN g++ -pedantic -std=c++11 -Wall -Wextra -Weffc++ -fopenmp -g3 -DDEBUG -isystem $HOME/eigen -I $HOME/clara/include testing/channels.cpp -o channels

# RUNNING BINARY FILE
ENTRYPOINT ["./channels"]
```

### Build and Run the Docker image

1. create directory that contains the following files
   - `Dockerfile.channels`
   - source file (e.g `example/channels.cpp`)
2. open terminal and navigate to the directory containing file
3. build the docker image using the following command:
   ```sh
   docker build -t quantum-channels -f Dockerfile.channels .
   ```
   this command will build an image named `quantum-channels` using
   `Dockerfile.channels`
4. once the image is built, you can run a docker container with the following
   command:
   ```sh
   docker run -it --rm quantum-channels
   ```
   this command will run the container based on the `quantum-channels` image.
   the `-it` flag allows interactive access, and the `--rm` flag removes the
   container when its stopped
