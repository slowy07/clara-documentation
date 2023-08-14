---
sidebar_position: 1
---

# Installation

## Eigen Installation
Clara running with [Eigen support](https://eigen.tuxfamily.org/) which you need to install eigen first to make sure clara works very well

### Linux
For debian based distro, you can barely install with [`apt`](https://wiki.debian.org/Apt) package manager by
```sh
sudo apt-get update # update package
sudo apt-get install libeigen3-dev
```
After that you can check the eigen by check the header by
```sh
ls /usr/local/include/eigen3
```
And then you can copy the header into local header path by
```sh
cp -r /usr/local/include/eigen3/Eigen /usr/local/include
```

<br/>

For Arch based distro, you can barely install with [`pacman`](https://wiki.archlinux.org/title/pacman) package manager by
```sh
sudo pacman -S eigen
```
After that you can do the step same like ubuntu step by copying to local header.

information about eigen package on arch you can check [here](https://archlinux.org/packages/extra/any/eigen/).

### MacOS

Sometimes, getting eigen, to work on macOS might require a little twist. Here set of commands that could to help you to install eigen successfully

Install eigen using [`brew`](https://brew.sh/) package manager
```sh
brew install eigen
```
after that you can check the eigen by using `ls` command by
```sh
ls /usr/local/Cellar/eigen/eigen_version/include/eigen3
```
``eigen_version``: is the version of eigen installed ex `3.4.0_1`.<br/>
copy the header to local header by
```sh
sudo cp -r /usr/local/Cellar/eigen/eigen_version/eigen3/Eigen /usr/local/include
```

by following these commands, you'll be able to install Eigen on your macOS system. the process might be a bit unconvetional, but it does the job

## Clara Initialization

After intialization [`eigen`](https://eigen.tuxfamily.org/), you can clone clara by
```sh
git clone https://github.com/slowy07/clara
```
you can clone into your project. and for usage you can check on [Tutorial - Usage](/docs/category/tutorial---usage)
