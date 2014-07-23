FROM ubuntu:trusty
MAINTAINER Dirk Franssen "dirk.franssen@gmail.com"

# One could force a daily or weekly upgrade of all
# packages by changing the REFRESHED_AT date, from time to time.
# Otherwise the first lines would be cached by docker and
# one would always use non up-to-date versions of the OS

ENV REFRESHED_AT 2014-07-23

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get -y install wget man java-common

ENV JVM_ROOT_PATH /usr/lib/jvm
RUN if [ ! -d $JVM_ROOT_PATH ]; then mkdir $JVM_ROOT_PATH; fi

# Installs JDK 8 (8u11-b12 to be exact :-))
# I personally prefer not to depend on a ppa package to install 'a version' of jdk1.8
RUN wget --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    http://download.oracle.com/otn-pub/java/jdk/8u11-b12/jdk-8u11-linux-x64.tar.gz -O /tmp/jdk-8u11-linux-x64.tar.gz
RUN tar -zxf /tmp/jdk-8u11-linux-x64.tar.gz -C $JVM_ROOT_PATH && \
    chown -R root:root $JVM_ROOT_PATH && \
    rm /tmp/jdk-8u11-linux-x64.tar.gz

ENV JAVA_HOME $JVM_ROOT_PATH/jdk1.8.0_11
ENV PATH $JAVA_HOME/bin:$PATH

#see other base image for the java update alternative way. Here just in PATH env
