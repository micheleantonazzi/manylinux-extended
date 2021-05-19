FROM quay.io/pypa/manylinux2010_x86_64

# Install development tools
RUN yum groupinstall -y 'Development Tools' \
    && yum install -y wget yum-utils libX* gcc openssl-devel bzip2-devel

# Install Python2.7
RUN wget https://www.python.org/ftp/python/2.7.18/Python-2.7.18.tgz \
    && tar -xf Python-2.7.18.tgz \
    && cd Python-2.7.18 \
    && ./configure  --enable-unicode=ucs4 \
    && make -j4 \
    && make install \
    && cd .. \
    && wget https://bootstrap.pypa.io/pip/2.7/get-pip.py \
    && python2.7 get-pip.py \
    && rm -rf Python-2.7.18* \
    && rm get-pip.py

# Install nodejs 12
RUN export LDFLAGS=-lrt \
    && wget https://nodejs.org/dist/v12.16.0/node-v12.16.0.tar.gz \
    && tar -xf node-v12.16.0.tar.gz \
    && cd node-v12.16.0 \
    && ./configure --prefix=/usr \
    && make -j8 \
    && make install \
    && cd .. \
    && rm -rf node-v12.16.0*

# Install cuda 10.2
RUN yum-config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel6/x86_64/cuda-rhel6.repo \
    && yum clean all \
    && yum install -y cuda

# Set environment variables to import python 3.x binaries and CUDA
ENV PATH=/opt/python/cp*/bin${PATH:+:${PATH}} \
    PATH=/usr/local/cuda-10.2/bin${PATH:+:${PATH}} \
    LD_LIBRARY_PATH=/usr/local/cuda-10.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

CMD /bin/bash