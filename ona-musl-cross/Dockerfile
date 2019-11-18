FROM alpine:3.10
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
RUN gem install etc fpm

# Retrieve libpcap and the cross compilers
RUN curl -O https://www.tcpdump.org/release/libpcap-1.9.1.tar.gz
RUN curl -O http://musl.cc/x86_64-linux-musl-cross.tgz
RUN curl -O https://musl.cc/arm-linux-musleabihf-cross.tgz
RUN curl -O https://musl.cc/aarch64-linux-musl-cross.tgz

RUN tar xf libpcap-1.9.1.tar.gz
RUN tar xf x86_64-linux-musl-cross.tgz
RUN tar xf arm-linux-musleabihf-cross.tgz
RUN tar xf aarch64-linux-musl-cross.tgz

# Build libpcap each platform
WORKDIR /libpcap-1.9.1

RUN CC="/x86_64-linux-musl-cross/bin/x86_64-linux-musl-gcc" ./configure \
    --with-pcap="linux" \
    --enable-usb="no" \
    --enable-netmap="no" \
    --enable-dbus="no" \
    --enable-rdma="no" \
    --host="x86_64-linux" \
    --prefix="/x86_64-linux-musl-cross"
RUN make && make install && make distclean

RUN CC="/arm-linux-musleabihf-cross/bin/arm-linux-musleabihf-gcc" ./configure \
    --with-pcap="linux" \
    --enable-usb="no" \
    --enable-netmap="no" \
    --enable-dbus="no" \
    --enable-rdma="no" \
    --host="x86_64-linux" \
    --prefix="/arm-linux-musleabihf-cross"
RUN make && make install && make distclean

RUN CC="/aarch64-linux-musl-cross/bin/aarch64-linux-musl-gcc" ./configure \
    --with-pcap="linux" \
    --enable-usb="no" \
    --enable-netmap="no" \
    --enable-dbus="no" \
    --enable-rdma="no" \
    --host="x86_64-linux" \
    --prefix="/aarch64-linux-musl-cross"
RUN make && make install && make distclean

ENTRYPOINT ["/bin/ash"]
