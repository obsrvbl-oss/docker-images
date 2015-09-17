FROM centos:6
MAINTAINER Observable Networks <engineering@obsrvbl.com>

RUN yum install -y \
    gcc \
    git \
    rpm-build \
    ruby \
    ruby-devel \
    rubygems \
    tar

RUN curl -O https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py

RUN gem install fpm

ENTRYPOINT ["/bin/bash"]
