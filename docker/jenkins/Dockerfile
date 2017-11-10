FROM jenkins/jenkins:latest

USER root

RUN apt-get update && apt-get install -y maven nano

USER jenkins

RUN /usr/local/bin/install-plugins.sh gitlab-plugin git
RUN /usr/local/bin/install-plugins.sh workflow-aggregator sonar


# Instalando docker en jenkins
USER root

RUN apt-get install -y \
     sudo \
     apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common

RUN curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg | sudo apt-key add -

RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
   $(lsb_release -cs) \
   stable"

RUN apt-get update && apt-get install -y docker-ce docker-compose

# Esto es para usar el usuario Jenkins con docker

RUN usermod -aG docker jenkins

USER jenkins
