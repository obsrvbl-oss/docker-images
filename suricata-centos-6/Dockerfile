FROM centos:6
MAINTAINER Observable Networks <engineering@obsrvbl.com>

RUN yum install -y epel-release

RUN yum install -y autoconf \
    automake \
    file-devel \
    gcc \
    gcc-c++ \
    git \
    libcap-ng \
    libcap-ng-devel \
    libnet \
    libnet-devel \
    libpcap \
    libpcap-devel \
    libtool \
    libyaml \
    libyaml-devel \
    make \
    pcre \
    pcre-devel \
    rpm-build \
    ruby \
    ruby-devel \
    rubygems \
    which \
    tar \
    zlib \
    zlib-devel

RUN curl -O https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py

RUN gem install fpm

RUN git clone https://github.com/OISF/libhtp.git
WORKDIR /libhtp
RUN ./autogen.sh && ./configure && make && make install

WORKDIR /

ENTRYPOINT ["/bin/bash"]
