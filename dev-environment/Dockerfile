# syntax=docker/dockerfile:1
### It is important to put this syntax specification at the start!!
### https://docs.docker.com/build/dockerfile/frontend/
### https://stackoverflow.com/questions/75309371/dockerfile-with-heredoc-running-in-bash

### ARG and ENV declaration and initialisation
ARG BASE_IMAGE=alpine
ARG ALPINE_LATEST=latest
ARG ALPINE_PENULTIMATE=3.20.5

### Base image
FROM ${BASE_IMAGE}:${ALPINE_PENULTIMATE}


### Installation phase

###### Utilties install
RUN <<EOF
apk update
apk add bash wget zsh git
EOF

###### setup ohmyzsh open-source, community-driven framework for managing your Zsh configuration
RUN <<EOF
bash -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
echo 'PROMPT=%B%F{blue}[DOCKER]%f%b$PROMPT' >> /root/.zshrc
EOF

###### install programming tools and debugger
RUN <<EOF
apk update
apk add coreutils build-base gcc g++ cmake
apk add pthread
apk add gdb strace tcpdump valgrind iputils net-tools
EOF

###### install thread safe queue FIFO c library
RUN <<EOF
cd /tmp/
git clone https://github.com/Taymindis/lfqueue.git
cd lfqueue
mkdir build
cd build
cmake ..
make
make install
EOF

###### install thread safe stack LIFO c library
RUN <<EOF
cd /tmp/
git clone https://github.com/Taymindis/lfstack.git
cd lfstack
mkdir build
cd build
cmake ..
make
make install
EOF

###### install thread atomic threadpool c library
RUN <<EOF
cd /tmp/
git clone https://github.com/Taymindis/atomic_threadpool.git
cd atomic_threadpool
git clone https://github.com/Taymindis/lfqueue.git
mkdir build
cd build
cmake ..
make
make install
EOF

### Environment configuration

USER root

### Metadata about the image specified here in the Dockerfile
LABEL \
	author="jya0 <jyao@student.42abudhabi.ae>" \
	maintainer="jya0 <jyao@student.42abudhabi.ae>" \
	version="1.1" \
	description="This Dockerfile builds a dev environment to write and test website portfolio."