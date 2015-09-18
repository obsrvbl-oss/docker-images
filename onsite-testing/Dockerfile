FROM bradrydzewski/python:2.7
MAINTAINER Observable Networks <engineering@obsrvbl.com>

RUN sudo apt-get update && sudo apt-get install -y \
    nodejs

RUN curl -O https://s3.amazonaws.com/travis-phantomjs/phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN tar xf phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN sudo cp phantomjs /usr/local/bin/phantomjs

ENTRYPOINT ["/bin/bash"]
