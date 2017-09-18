FROM ubuntu:xenial
MAINTAINER Christopher Friedt "chrisfriedt@gmail.com"

USER root

RUN apt-get update
RUN apt-get install -y build-essential autotools-dev autoconf libtool clang
RUN apt-get install -y cmake
RUN apt-get install -y libgtest-dev
RUN sh -c 'cd /usr/src/gtest && cmake -DBUILD_SHARED_LIBS=ON && make && cp *.so /usr/lib/'
RUN sh -c 'cd /usr/src/gtest && make clean && rm -Rf CMakeCache.txt CMakeFiles/ && cmake && make && cp *.a /usr/lib/'

WORKDIR /root
