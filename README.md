# Manylinux extended docker images
This repository contains docker manylinux images with pre-installed software. This makes the build procedure faster by reducing the system configuration phase.
You can find the original manylinux docker images visiting the project [sources](https://github.com/pypa/manylinux).
The extended images are *manylinux2010_x86_64* and *manylinux2014_x86_64*, you can find then on the relative DockerHub [repository](https://hub.docker.com/r/micheleantonazzi/manylinux-extended).

## Manylinux2010_x86_64_extended
This docker image uses *manylinux2010_x84_64* as base image. In addition, the following packages are installed:
* The *Development Tools* packages
* The libX* packages
* Nodejs 10
* CUDA 10.2

The environment variables (*PATH* and *LD_LIBRARY_PATH*) already include:
* the Python 3.x executables
* the pip3.x executables
* the CUDA binaries and libraries

## Manylinux2014_x86_64_extended
This docker image uses *manylinux2014_x84_64* as base image. In addition, the following packages are installed:
* The *Development Tools* packages
* The libX* packages  
* Nodejs 14
* CUDA 11.0

The environment variables (*PATH* and *LD_LIBRARY_PATH*) already include:
* the Python 3.x executables
* the pip3.x executables
* the CUDA binaries and libraries