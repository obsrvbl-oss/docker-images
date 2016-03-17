FROM python:2.7
MAINTAINER Observable Networks <engineering@obsrvbl.com>

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y \
    nodejs \
    npm \
    ruby-dev \
    rubygems \
    byacc \
    gfortran \
    libblas-dev \
    liblapack-dev \
    libffi-dev \
    libssl-dev \
    wamerican \
    tshark \
    netcat \
    postgresql-client

RUN ln -s /usr/bin/nodejs /usr/local/bin/node
RUN echo '{ "allow_root": true }' > /root/.bowerrc

RUN mkdir /root/.wireshark/ && chmod a+rx /root/.wireshark/

RUN curl -O https://s3.amazonaws.com/onstatic/phantomjs-2.1.1-linux-x86_64.tar.bz2
RUN tar xf phantomjs-2.1.1-linux-x86_64.tar.bz2
RUN cp phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/local/bin/phantomjs

RUN curl -O https://s3.amazonaws.com/onstatic/site-packages/nfdump-1.6.14-x86_64
RUN mv nfdump-1.6.14-x86_64 /usr/bin/nfdump
RUN chmod +x /usr/bin/nfdump

RUN pip install -U 'pip>=6.0' 'setuptools>=18.6.1'

RUN gem install ghi

ENTRYPOINT ["/bin/bash"]
