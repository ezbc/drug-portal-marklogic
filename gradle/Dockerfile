FROM gradle:jre8

MAINTAINER Elijah Bernstein-Cooper <elijah@ezbc.me>

ARG ODH_INSTALL_PATH
ARG CORB_JAR_PATH

EXPOSE 5005

COPY ./odh/$ODH_INSTALL_PATH /opt/odh/
COPY ./corb/$CORB_JAR_PATH /opt/corb/
COPY ./odh/mlcp-9.0.5/ /opt/mlcp/

ENV PATH="/opt/mlcp/bin:${PATH}"
