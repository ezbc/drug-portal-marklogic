FROM gradle:alpine

MAINTAINER Elijah Bernstein-Cooper <ezbc@ezbc.me>

ARG ODH_INSTALL_PATH

EXPOSE 5005

# set up ODH
WORKDIR /odh

COPY $ODH_INSTALL_PATH /
