FROM bradrydzewski/python:2.7
MAINTAINER Observable Networks <engineering@obsrvbl.com>
USER ubuntu
WORKDIR /home/ubuntu

RUN sudo apt-get update && sudo apt-get install -y \
    nodejs \
    npm \
    rubygems

RUN sudo ln -s /usr/bin/nodejs /usr/local/bin/node
RUN sudo npm install --global npm

RUN curl -O https://s3.amazonaws.com/travis-phantomjs/phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN tar xf phantomjs-2.0.0-ubuntu-12.04.tar.bz2
RUN sudo cp phantomjs /usr/local/bin/phantomjs

RUN sudo gem install ghi

ENTRYPOINT ["/bin/bash"]
