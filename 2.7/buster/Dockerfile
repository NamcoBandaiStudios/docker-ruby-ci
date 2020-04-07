FROM circleci/ruby:2.7-buster

# OS packages
RUN echo 'APT::Install-Recommends "false";' | sudo tee /etc/apt/apt.conf.d/no-install-recommends >/dev/null && \
  sudo apt-get update && \
  sudo apt-get install -y \
    apt-transport-https \
    default-mysql-client python3-pip python3-setuptools python3-yaml python3-wheel python3-dev && \
  sudo rm -rf /var/lib/apt/lists/*

# Node.js
RUN curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash - && \
  sudo apt-get install nodejs && \
  sudo npm install -g yarn && \
  sudo rm -rf /var/lib/apt/lists/* && \
  sudo rm -rf /tmp/npm-*

# AWS CLI
RUN sudo pip3 install awscli && \
  sudo rm -rf /tmp/pip*

# protobuf-compiler
RUN curl -L -o /tmp/protobuf.tar.gz https://github.com/protocolbuffers/protobuf/releases/download/v3.9.0//protobuf-all-3.9.0.tar.gz && \
    tar xzvf /tmp/protobuf.tar.gz -C /tmp && \
    cd /tmp/protobuf-3.9.0 && \
    ./configure --prefix=/usr && make && sudo make install && sudo rm -rf /tmp/protobuf*

# ChromeDriver
ENV CHROMEDRIVER_PATH /usr/bin/chromedriver
RUN sudo apt-get update && \
  sudo apt-get install -y chromium libgconf-2-4 unzip chromium-driver && \
  sudo rm -rf /var/lib/apt/lists/*
