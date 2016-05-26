FROM ubuntu:trusty
MAINTAINER tszkitlo 
RUN apt-get update; apt-get install -y openjdk-7-jdk wget supervisor docker.io openssh-server
RUN apt-get install -y maven
RUN apt-get install -y git
ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64/
RUN echo 'root:123321' | chpasswd
RUN mkdir /var/run/sshd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

EXPOSE 22

