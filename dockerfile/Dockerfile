#
# Environment for building iRODS 4.2 rule engine plugin
#
#
# Use old xenial like VMs to preempt any library issue
#FROM ubuntu:bionic
FROM ubuntu:xenial

ARG DEBIAN_FRONTEND=noninteractive

ARG GIT_URL=https://github.com/jasoncoposky/irods_deployment_csir.git
ARG GIT_BRANCH=master

RUN apt update \
 # http://slides.com/irods/ugm2019-administration-getting-started#/1 \
 && apt-get -y install git g++ make python-dev help2man unixodbc libfuse-dev libcurl4-gnutls-dev libbz2-dev zlib1g-dev libpam0g-dev libssl-dev libxml2-dev libkrb5-dev unixodbc-dev libjson-perl python-psutil python-jsonschema super python-exif odbc-postgresql cmake build-essential \
 && apt -y install wget libssl-dev lsb-release apt-transport-https \
 && wget -qO - https://packages.irods.org/irods-signing-key.asc | apt-key add - \
 && echo "deb [arch=amd64] https://packages.irods.org/apt/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/renci-irods.list \
 && apt update

# && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN apt -y install irods-dev irods-externals-clang3.8-0 irods-runtime
