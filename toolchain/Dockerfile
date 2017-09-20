FROM ubuntu:xenial
MAINTAINER Christopher Friedt "chrisfriedt@gmail.com"

USER root

# the usual
RUN apt-get update && apt-get install -y git
RUN apt-get update && apt-get install -y build-essential
RUN apt-get update && apt-get install -y autotools-dev
RUN apt-get update && apt-get install -y autoconf
RUN apt-get update && apt-get install -y libtool

# Just an alternative toolchain (it's generally good if code can compile with both gcc and clang)
RUN apt-get update && apt-get install -y clang

# cmake is a build dependency for Google Test Framework (gtest) as well as other projects
RUN apt-get install -y cmake

# install gtest headers
RUN apt-get install -y libgtest-dev

# build & install gtest shared libraries and static libraries
RUN sh -c 'cd /usr/src/gtest && cmake -DBUILD_SHARED_LIBS=ON && make && cp *.so /usr/lib/'
RUN sh -c 'cd /usr/src/gtest && make clean && rm -Rf CMakeCache.txt CMakeFiles/ && cmake && make && cp *.a /usr/lib/'

# dash is kind of annoying, so get rid of it
RUN rm /bin/sh && ln -sf /bin/bash /bin/sh

WORKDIR /root

