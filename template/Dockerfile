FROM registry.centos.org/centos:8

 
ENV LC_ALL=en_US.UTF-8 \
    LANG=en_US.UTF-8 

RUN INSTALL_PKGS="nginx" && \
    yum -y --setopt=tsflags=nodocs install $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum -y clean all --enablerepo='*'

ENTRYPOINT ["/bin/bash"]

