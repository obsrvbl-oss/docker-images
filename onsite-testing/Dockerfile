FROM bradrydzewski/python:2.7
LABEL maintainer="Observable Networks <engineering@obsrvbl.com>"
USER ubuntu
WORKDIR /home/ubuntu

RUN sudo apt-get update && sudo apt-get install -y \
    rubygems

RUN curl -O https://nodejs.org/dist/v4.4.2/node-v4.4.2-linux-x64.tar.xz
RUN sudo tar xf node-v4.4.2-linux-x64.tar.xz -C /usr/local

RUN curl -O https://s3.amazonaws.com/travis-phantomjs/phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN tar xf phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN sudo cp phantomjs /usr/local/bin/phantomjs

RUN sudo gem install ghi

ENTRYPOINT ["/bin/bash"]
