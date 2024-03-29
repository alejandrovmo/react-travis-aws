FROM ubuntu:18.04

LABEL MAINTAINER="Kasun Ranasinghe <kasunranasinghe303@gmail.com>"
LABEL Description="This is a base image, which allows connecting Jenkins agents via JNLP protocols"

USER root
RUN apt-get update
RUN apt-get install -y openjdk-11-jre-headless

RUN apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -  
RUN apt-key fingerprint 0EBFCD88 
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
RUN apt-get update
RUN apt-get install -y docker-ce-cli

ARG VERSION=4.10
ARG user=jenkins
ARG group=jenkins
ARG uid=1000
ARG gid=1000

RUN groupadd -g ${gid} ${group}
RUN useradd -c "Jenkins user" -d /home/${user} -u ${uid} -g ${gid} -m ${user}

ARG AGENT_WORKDIR=/home/${user}/agent

RUN apt-get update && apt-get -y install git-lfs && rm -rf /var/lib/apt/lists/*
RUN curl --create-dirs -fsSLo /usr/share/jenkins/agent.jar https://repo.jenkins-ci.org/public/org/jenkins-ci/main/remoting/${VERSION}/remoting-${VERSION}.jar \
  && chmod 755 /usr/share/jenkins \
  && chmod 644 /usr/share/jenkins/agent.jar \
  && ln -sf /usr/share/jenkins/agent.jar /usr/share/jenkins/slave.jar

USER ${user}
ENV AGENT_WORKDIR=${AGENT_WORKDIR}
RUN mkdir /home/${user}/.jenkins && mkdir -p ${AGENT_WORKDIR}

COPY /files/resolv.conf /etc/resolv.conf

VOLUME /home/${user}/.jenkins
VOLUME ${AGENT_WORKDIR}
VOLUME /var/run/docker.sock
WORKDIR /home/${user}