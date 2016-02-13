#
# Java 1.8 & Maven Dockerfile
#

# pull base image.
FROM java:openjdk-8-jdk

# maintainer details
MAINTAINER Maxim Yunusov <myunusov@maxur.org>

ENV DEBIAN_FRONTEND noninteractive

# update packages and install maven
RUN  \  
  sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
  apt-get update && \
  apt-get -y upgrade && \
  apt-get install -y wget curl git graphviz 
  
ENV MAVEN_VERSION 3.3.9

RUN curl -kfsSL https://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar xzf - -C /usr/share \
  && mv /usr/share/apache-maven-$MAVEN_VERSION /usr/share/maven \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven
ENV M3_HOME /usr/share/maven
ENV GRAPHVIZ_DOT /usr/bin/dot

VOLUME /root/.m2  
  
# create working directory
RUN mkdir -p /local/git
WORKDIR /local/git

# run terminal
CMD ["/bin/bash"]