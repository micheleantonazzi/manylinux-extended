FROM quay.io/pypa/manylinux2010_x86_64

# Install development tools
RUN yum groupinstall -y 'Development Tools' \
    && yum install -y wget yum-utils libX*

# Install nodejs 10
RUN curl -sL https://rpm.nodesource.com/setup_10.x | bash - \
    && yum install -y nodejs

# Install cuda 10.2
RUN yum-config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel6/x86_64/cuda-rhel6.repo \
    && yum clean all \
    && yum install -y cuda

# Set environment variables to import python 3.x binaries and CUDA
ENV PATH=/opt/python/cp*/bin${PATH:+:${PATH}} \
    PATH=/usr/local/cuda-10.2/bin${PATH:+:${PATH}} \
    LD_LIBRARY_PATH=/usr/local/cuda-10.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

CMD /bin/bash