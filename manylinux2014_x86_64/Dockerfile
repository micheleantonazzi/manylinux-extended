FROM quay.io/pypa/manylinux2014_x86_64

# Install development tools
RUN yum groupinstall -y 'Development Tools' \
    && yum install -y wget yum-utils libX* gcc openssl-devel bzip2-devel

# Install Python2.7
RUN wget https://www.python.org/ftp/python/2.7.18/Python-2.7.18.tgz \
    && tar -xf Python-2.7.18.tgz \
    && cd Python-2.7.18 \
    && ./configure \
    && make -j4 \
    && make install \
    && cd .. \
    && wget https://bootstrap.pypa.io/pip/2.7/get-pip.py \
    && python2.7 get-pip.py \
    && rm -rf Python-2.7.18* \
    && rm get-pip.py

# Install nodejs 14
RUN curl -sL https://rpm.nodesource.com/setup_14.x | bash - \
    && yum install -y nodejs

# Install cuda 11.0
RUN yum-config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel7/x86_64/cuda-rhel7.repo \
    && yum clean all \
    && yum install -y cuda-11-0

# Set environment variables to import python 3.x binaries and CUDA
ENV PATH=/opt/python/cp*/bin${PATH:+:${PATH}} \
    PATH=/usr/local/cuda-11.0/bin${PATH:+:${PATH}} \
    LD_LIBRARY_PATH=/usr/local/cuda-11.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

CMD /bin/bash