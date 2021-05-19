# Manylinux extended docker images
This repository contains docker manylinux images with pre-installed software. This makes the build procedure faster by reducing the system configuration phase.
You can find the original manylinux docker images visiting the project [sources](https://github.com/pypa/manylinux).
The extended images are *manylinux2010_x86_64* and *manylinux2014_x86_64*, you can find then on the relative DockerHub [repository](https://hub.docker.com/r/micheleantonazzi/manylinux-extended).

## Manylinux2010_x86_64_extended
This docker image uses *manylinux2010_x84_64* as base image. In addition, the following packages are installed:
* The *Development Tools* packages
* Nodejs 12
* CUDA 10.2
* wget, yum-utils, libX*, openssl-devel, bzip2-devel packages

The environment variables (*PATH* and *LD_LIBRARY_PATH*) already include:
* the Python 3.x executables
* the pip3.x executables
* the CUDA binaries and libraries

You can use this docker image typing:
```bash
sudo docker run -i -t -v `pwd` micheleantonazzi/manylinux-extended:manylinux2010_x86_64_extended_0.5.1 /bin/bash
```  

## Manylinux2014_x86_64_extended
This docker image uses *manylinux2014_x84_64* as base image. In addition, the following packages are installed:
* The *Development Tools* packages
* Nodejs 14
* CUDA 11.0
* wget, yum-utils, libX* packages

The environment variables (*PATH* and *LD_LIBRARY_PATH*) already include:
* the Python 3.x executables
* the pip3.x executables
* the CUDA binaries and libraries

You can use this docker image typing:
```bash
sudo docker run -i -t -v `pwd` micheleantonazzi/manylinux-extended:manylinux2014_x86_64_extended_0.5.1 /bin/bash
```  