FROM registry.centos.org/centos:8


ENV GOBIN=/root/gobin
ENV PATH=/usr/local/go/bin:$PATH

RUN INSTALL_PKGS="git wget unzip make" && \
    yum -y --setopt=tsflags=nodocs install $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum -y clean all --enablerepo='*'

#Install terraform 

RUN mkdir /root/gobin
COPY Makefile.install  /root/Makefile
WORKDIR /root
RUN make 

FROM registry.centos.org/centos:8
RUN mkdir -p /root/.terraform.d/plugins
COPY --from=0 /root/terraform /usr/local/bin/terraform
COPY --from=0 /root/gobin/terraform-provider-upcloud /root/.terraform.d/plugins

copy entrypoint.sh /entrypoint.sh 
WORKDIR /root
ENTRYPOINT ["/entrypoint.sh"]



