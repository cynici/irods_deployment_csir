#
# Environment for building iRODS 4.2 rule engine plugin
#
#
FROM ubuntu:bionic

ARG DEBIAN_FRONTEND=noninteractive

ARG GIT_URL=https://github.com/jasoncoposky/irods_deployment_csir.git
ARG GIT_BRANCH=master

RUN apt update \
 # http://slides.com/irods/ugm2019-administration-getting-started#/1 \
 && apt-get -y install git g++ make python-dev help2man unixodbc libfuse-dev libcurl4-gnutls-dev libbz2-dev zlib1g-dev libpam0g-dev libssl-dev libxml2-dev libkrb5-dev unixodbc-dev libjson-perl python-psutil python-jsonschema super python-exif odbc-postgresql

RUN apt -y install cmake git

RUN git clone --single-branch --branch $GIT_BRANCH $GIT_URL /src

# && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
