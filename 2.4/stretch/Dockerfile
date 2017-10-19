FROM circleci/ruby:2.4-stretch

# OS packages
RUN echo 'APT::Install-Recommends "false";' | sudo tee /etc/apt/apt.conf.d/no-install-recommends >/dev/null && \
  sudo apt-get update && \
  sudo apt-get install -y protobuf-compiler mysql-client python-pip python-setuptools python-yaml python-dev && \
  sudo apt-get install -y apt-transport-https && \
  sudo rm -rf /var/lib/apt/lists/*

# Node.js
RUN curl -sL https://deb.nodesource.com/setup_4.x | sudo bash - && \
  sudo apt-get install nodejs && \
  sudo npm install -g yarn && \
  sudo rm -rf /var/lib/apt/lists/* && \
  sudo rm -rf /tmp/npm-*

# AWS CLI
RUN sudo pip install awscli && \
  sudo rm -rf /tmp/pip*

# ChromeDriver
ENV CHROMEDRIVER_PATH /usr/local/bin/chromedriver
RUN sudo apt-get update && \
  sudo apt-get install -y chromium libgconf-2-4 unzip && \
  sudo rm -rf /var/lib/apt/lists/*
RUN curl -L -o /tmp/chromedriver.zip https://chromedriver.storage.googleapis.com/2.33/chromedriver_linux64.zip && \
  cd /tmp && \
  unzip chromedriver.zip && \
  sudo cp /tmp/chromedriver /usr/local/bin/chromedriver && \
  rm -f /tmp/chromedriver*
