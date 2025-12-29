FROM jenkins/jenkins:lts-jdk17
LABEL maintainer="rezanobakht1378@gmail.com"

USER root
RUN mkdir /var/log/jenkins

RUN mkdir /var/cache/jenkins
RUN chown -R jenkins:jenkins /var/log/jenkins

RUN chown -R jenkins:jenkins /var/cache/jenkins

RUN apt-get update
#RUN apt-get install -y python3 python3-pip
USER jenkins
ENV JAVA_OPTS="-Xmx4096m"
ENV JENKINS_OPTS="--logfile=/var/log/jenkins/jenkins.log --webroot=/var/cache/jenkins/war --prefix=/jenkins"
