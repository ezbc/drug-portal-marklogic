FROM centos:centos7

MAINTAINER Elijah Bernstein-Cooper <elijah@ezbc.me>

ARG ML_INSTALL_PATH
ARG ML_CONVERTERS_PATH

# Get any CentOS updates then clear the Docker cache
RUN yum -y update && \
		yum -y install initscripts && \
		yum -y install glibc.i686 gdb.x86_64 redhat-lsb.x86_64 && \
		yum clean all

# Set the Path
ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/MarkLogic/mlcmd/bin

# Copy the MarkLogic installer to a temp directory in the Docker image being built
COPY $ML_INSTALL_PATH /tmp/MarkLogic.rpm

COPY $ML_CONVERTERS_PATH /tmp/MarkLogicConverters.rpm

# Install MarkLogic then delete the .RPM file if the install succeeded
RUN yum -y install /tmp/MarkLogic.rpm && \
    yum -y install /tmp/MarkLogicConverters.rpm && \
    rm /tmp/MarkLogic.rpm && \
    rm /tmp/MarkLogicConverters.rpm

# Expose MarkLogic Server ports
# These expose ports between Docker Containers.
# Publish your application ports in the Docker run command using -p (See Docker Documentation)
EXPOSE 7997 7998 7999

# Start MarkLogic from the init.d script
# Define default command for Docker to run (which avoids immediate shutdown)  /dev/null is the bit-bucket: the place where you dump anything you don't need.
CMD /etc/init.d/MarkLogic start && tail -f /dev/null
