# Installation

Clara is a powerful and versatile project that can be installed on various
operating systems, including Linux, macOS, and Windows. Please note that while
installation on Linux and macOS is straightforward, Windows installation
involves a few additional steps.

## installation instruction (Eigen)

### Linux (debian Based)

Update the package repository from ubuntu by 
```sh
sudo apt-get update
```
install Eigen library using the following command by
```sh
sudo apt-get install libeigen3-dev
```
Copy the header files to the appropriate locations
```sh
sudo cp -r /usr/local/include/eigen3/Eigen /usr/local/include
```

### Linux (Arch Based)

install the eigen package using favorite package like ``yay`` or ``pacman``
```sh
sudo pacman -S eigen
```
for information about the eigen package you can check this [link](https://archlinux.org/packages/extra/any/eigen/), on the next step you can following from ubuntu package by move the the Eigen to the appropriate locations.

### Windows

You can install on windows using ``Cygwin`` by folowing this official page [Cygwin](https://cygwin.com/install.html).
during the Cygwin installation process,ensure that you select CMake and g++ packages. once Cygwin is installed, open the Cygwin terminal and proceed with the steps mentioned for the respective operating systems (Linux or macOS).

### macOS

Installation on macOS little bit tricky but you can install Eigen

install ``wget`` if you don't have, information about  ``wget``, you can check [here](https://www.gnu.org/software/wget/)
```sh
brew install wget
```
after that, you can install eigen
```sh
brew install eigen
```
copy from brew package by
```sh
sudo cp -r /usr/local/Cellar/eigen/{version_eigen}/include/eigen3/Eigen /usr/local/include
```
after that, export local C and C++ include path by
```sh
export C_INCLUDE_PATH=/usr/local/include
export CPLUS_INCLUDE_PATH=/usr/local/include

# you can check by
# ls /usr/local/include
```

if you have problem on compile cause ``libintl.h``, you can adding to ``usr/loca/include`` from [libintl.h](https://sites.uclouvain.be/SystInfo/usr/include/libintl.h.html) using ``wget`` by:
```sh
wget -P /usr/local/include https://opensource.apple.com/source/zfs/zfs-59/zfs_lib/libintl.h
```

## Getting started on Clara

to get started with the clara prooject

```sh
git clone https://github.com/slowy07/clara.git
```
navigate to the project directory
```sh
cd clara
```
