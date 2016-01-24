FROM python:2.7
MAINTAINER Observable Networks <engineering@obsrvbl.com>

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y \
    nodejs \
    rubygems \
    byacc \
    gfortran \
    libblas-dev \
    liblapack-dev \
    libffi-dev \
    libssl-dev \
    wamerican \
    tshark \
    postgresql-client

RUN curl -O https://s3.amazonaws.com/travis-phantomjs/phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN tar xf phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN cp phantomjs /usr/local/bin/phantomjs

RUN curl -O https://s3.amazonaws.com/onstatic/site-packages/nfdump-1.6.14-x86_64
RUN mv nfdump-1.6.14-x86_64 /usr/bin/nfdump
RUN chmod +x /usr/bin/nfdump

RUN pip install -U 'pip>=6.0' 'setuptools>=18.6.1'

RUN gem install ghi

ENTRYPOINT ["/bin/bash"]
