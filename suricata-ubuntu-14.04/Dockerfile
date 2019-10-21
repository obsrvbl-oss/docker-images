FROM ubuntu:16.04
LABEL maintainer="Observable Networks <engineering@obsrvbl.com>"

RUN apt-get update && apt-get install -y \
    autoconf \
    automake \
    build-essential \
    cargo \
    curl \
    git \
    libcap-ng0 \
    libcap-ng-dev \
    libpcap-dev \
    libjansson4 \
    libjansson-dev \
    libmagic-dev \
    libnet1-dev \
    libpcre3 \
    libpcre3-dev \
    libtool \
    libyaml-0-2 \
    libyaml-dev \
    make \
    pkg-config \
    python2.7 \
    python-dev \
    python-pip \
    rpm \
    ruby \
    ruby-dev \
    rustc \
    zlib1g \
    zlib1g-dev

RUN pip install awscli

RUN gem install fpm

RUN git clone https://github.com/OISF/libhtp.git
WORKDIR /libhtp
RUN ./autogen.sh && ./configure && make && make install

WORKDIR /

ENTRYPOINT ["/bin/bash"]
