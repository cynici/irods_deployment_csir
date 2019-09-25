#
# Environment for building iRODS rule engine plugin
#
#
# Use old xenial like VMs to preempt any library issue
#FROM ubuntu:bionic
FROM ubuntu:xenial

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update \
 # http://slides.com/irods/ugm2019-administration-getting-started#/1 \
 && apt-get -y install git g++ make python-dev help2man unixodbc libfuse-dev libcurl4-gnutls-dev libbz2-dev zlib1g-dev libpam0g-dev libssl-dev libxml2-dev libkrb5-dev unixodbc-dev libjson-perl python-psutil python-jsonschema super python-exif odbc-postgresql cmake build-essential \
 && apt -y install wget libssl-dev lsb-release apt-transport-https
 
#
# Default values overriddable using docker build args
# Releases must be available at
# https://packages.irods.org/apt/dists/xenial/main/binary-amd64/Packages 
# https://packages.irods.org/apt/dists/bionic/main/binary-amd64/Packages 
#
ARG IRODS_VERSION=4.2.6
ARG CLANG_VERSION=3.8

RUN wget -qO - https://packages.irods.org/irods-signing-key.asc | apt-key add - \
 && echo "deb [arch=amd64] https://packages.irods.org/apt/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/renci-irods.list \
 && apt update \
 && apt -y install irods-dev=${IRODS_VERSION} irods-runtime=${IRODS_VERSION} irods-externals-clang${CLANG_VERSION} 

# && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
