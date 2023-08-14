###########################################
#  Operating System
###########################################

# Ubuntu 20.04 AMD64
FROM ubuntu:20.04

# Ubuntu 20.04 ARM64
# FROM arm64v8/ubuntu:focal

# Ubuntu 22.04 AMD64
# FROM ubuntu:jammy

# Ubuntu 22.04 ARM64
# FROM arm64v8/ubuntu:jammy

ENV DEBIAN_FRONTEND=noninteractive

# Install language
RUN apt-get update && apt-get install -y \
  locales \
  && locale-gen en_US.UTF-8 \
  && update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 \
  && rm -rf /var/lib/apt/lists/*
ENV LANG en_US.UTF-8

# Install timezone
RUN ln -fs /usr/share/zoneinfo/UTC /etc/localtime \
  && export DEBIAN_FRONTEND=noninteractive \
  && apt-get update \
  && apt-get install -y tzdata \
  && dpkg-reconfigure --frontend noninteractive tzdata \
  && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get -y upgrade \
    && rm -rf /var/lib/apt/lists/*

# Install common programs
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    gnupg2 \
    lsb-release \
    sudo \
    software-properties-common \
    wget \
    && rm -rf /var/lib/apt/lists/*


###########################################
#  Behavior Tree CPP library
###########################################

RUN apt-get update && \
    apt-get install -y -q git \
    build-essential \
    cmake \
    python3 \
    libzmq3-dev \
    libboost-dev

# Version 3
RUN git clone --branch v3.8 https://github.com/BehaviorTree/BehaviorTree.CPP.git

RUN cd BehaviorTree.CPP && \
    mkdir build; cd build && \
    cmake .. && \
    make && \
    sudo make install &&\
    cd ..
