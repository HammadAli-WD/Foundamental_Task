
# Dockerfile

# base image
FROM ubuntu:18.04

# Install Node.js
RUN apt-get update
RUN apt-get -y install curl
RUN apt-get -y install sudo
RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo
RUN curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
RUN apt-get install -y build-essential
RUN apt-get install -y nodejs

# Install Yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update
RUN sudo apt-get install yarn

RUN mkdir -p /app
WORKDIR /app

COPY package*.json /app
RUN yarn install
COPY . /app

RUN yarn add next@canary --force

# start app
EXPOSE 3000
# CMD ls
CMD yarn dev
