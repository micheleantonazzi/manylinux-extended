FROM quay.io/pypa/manylinux2010_x86_64

# Import python 3.x binaries
RUN export PATH=/opt/python/cp*/bin${PATH:+:${PATH}}

# Install development tools
RUN yum groupinstall -y 'Development Tools' \
    && yum install -y wget

# Install cuda 10.2
RUN yum-config-manager --add-repo https://developer.download.nvidia.com/compute/cuda/repos/rhel6/x86_64/cuda-rhel6.repo \
    && yum clean all \
    && yum install -y cuda \
    && export PATH=/usr/local/cuda-10.2/bin${PATH:+:${PATH}} \
    && export LD_LIBRARY_PATH=/usr/local/cuda-10.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

CMD /bin/bash