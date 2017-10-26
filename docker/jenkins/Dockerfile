FROM jenkins/jenkins:latest

USER root

RUN apt-get update && apt-get install -y maven nano

USER jenkins

RUN /usr/local/bin/install-plugins.sh gitlab-plugin git workflow-aggregator
RUN /usr/local/bin/install-plugins.sh sonar