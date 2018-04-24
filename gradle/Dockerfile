FROM gradle:alpine

MAINTAINER Elijah Bernstein-Cooper <ezbc@ezbc.me>

ARG ODH_INSTALL_PATH
ARG CORB_JAR_PATH

EXPOSE 5005

COPY ./odh/$ODH_INSTALL_PATH /opt/odh/
COPY ./corb/$CORB_JAR_PATH /opt/corb/
