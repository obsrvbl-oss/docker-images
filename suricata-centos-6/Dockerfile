FROM centos:6
LABEL maintainer="Observable Networks <engineering@obsrvbl.com>"

RUN curl -L -O "https://static.rust-lang.org/rustup/dist/x86_64-unknown-linux-gnu/rustup-init" \
    && chmod +x rustup-init \
    && ./rustup-init -y \
    && source $HOME/.cargo/env

RUN yum install -y epel-release

RUN yum install -y autoconf \
    automake \
    file-devel \
    gcc \
    gcc-c++ \
    git \
    jansson-devel \
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
    python-devel \
    python-pip \
    rpm-build \
    ruby \
    ruby-devel \
    rubygems \
    which \
    tar \
    zlib \
    zlib-devel

RUN pip install awscli

RUN gem install rake -v 10.5.0
RUN gem install childprocess -v 1.0.1
RUN gem install json -v 1.8.3
RUN gem install ffi -v 1.9.18
RUN gem install fpm -v 1.4.0

RUN git clone https://github.com/OISF/libhtp.git
WORKDIR /libhtp
RUN ./autogen.sh && ./configure && make && make install

WORKDIR /

ENTRYPOINT ["/bin/bash"]
