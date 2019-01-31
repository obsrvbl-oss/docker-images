FROM alpine:3.6
LABEL maintainer="Observable Networks <engineering@obsrvbl.com>"

# Retrieve Alpine packages
RUN apk update && apk add \
    bash \
    bison \
    build-base \
    curl \
    flex \
    git \
    libffi-dev \
    net-snmp-tools \
    openssh \
    perl \
    python \
    python3 \
    ruby \
    ruby-dev \
    ruby-irb \
    ruby-rdoc \
    rpm \
    tar \
    tzdata \
    xz

# Retrieve Python and Ruby packages
RUN curl -O https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py
RUN pip install awscli
RUN gem install fpm

# Retrieve libpcap and the cross compilers
RUN curl -O http://www.tcpdump.org/release/libpcap-1.7.4.tar.gz
RUN curl -O https://s3.amazonaws.com/onstatic/musl-cross/crossx86-arm-linux-musleabihf-1.1.tar.xz
RUN curl -O https://s3.amazonaws.com/onstatic/musl-cross/crossx86-i386-linux-musl-1.1.tar.xz
RUN curl -O https://s3.amazonaws.com/onstatic/musl-cross/crossx86-x86_64-linux-musl-1.1.tar.xz

RUN tar xf libpcap-1.7.4.tar.gz
RUN tar xf crossx86-arm-linux-musleabihf-1.1.tar.xz
RUN tar xf crossx86-i386-linux-musl-1.1.tar.xz
RUN tar xf crossx86-x86_64-linux-musl-1.1.tar.xz

# Build libpcap each platform
WORKDIR /libpcap-1.7.4

RUN CC="/arm-linux-musleabihf/bin/arm-linux-musleabihf-gcc" ./configure \
    --with-pcap="linux" \
    --host="arm-linux" \
    --prefix="/arm-linux-musleabihf"
RUN make && make install && make distclean

RUN CC="/i386-linux-musl/bin/i386-linux-musl-gcc" ./configure \
    --with-pcap="linux" \
    --host="i386-linux" \
    --prefix="/i386-linux-musl"
RUN make && make install && make distclean

RUN CC="/x86_64-linux-musl/bin/x86_64-linux-musl-gcc" ./configure \
    --with-pcap="linux" \
    --host="x86_64-linux" \
    --prefix="/x86_64-linux-musl"
RUN make && make install && make distclean


ENTRYPOINT ["/bin/ash"]
