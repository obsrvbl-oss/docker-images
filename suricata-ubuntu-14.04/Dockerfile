FROM ubuntu:trusty
MAINTAINER Observable Networks <engineering@obsrvbl.com>

RUN apt-get update && apt-get install -y \
    autoconf \
    automake \
    build-essential \
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
    rpm \
    ruby \
    ruby-dev \
    zlib1g \
    zlib1g-dev

RUN curl -O https://bootstrap.pypa.io/get-pip.py
RUN python2.7 get-pip.py

RUN gem install fpm

RUN git clone https://github.com/OISF/libhtp.git
WORKDIR /libhtp
RUN git checkout 0.5.17
RUN ./autogen.sh && ./configure && make && make install

WORKDIR /

ENTRYPOINT ["/bin/bash"]
