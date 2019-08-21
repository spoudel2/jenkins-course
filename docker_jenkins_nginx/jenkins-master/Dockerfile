FROM jenkins/jenkins:lts
LABEL maintainer="prabhatiitbhu@gmail.com"

USER root

RUN apt-get update && apt-get install -y \
  zip \
  sudo \
  nano \
  build-essential \
  python-dev \
  python-pip \
  python-cffi \
  python3-dev \
  python3-pip \
  python3-cffi \
  libcairo2 \
  libpango-1.0-0 \
  libpangocairo-1.0-0 \
  libgdk-pixbuf2.0-0 \
  libffi-dev \
  shared-mime-info \
  virtualenv \
  default-libmysqlclient-dev \
  mysql-server;

# Install AWS CLI
RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
RUN unzip awscli-bundle.zip
RUN ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
RUN rm awscli-bundle.zip
RUN mkdir /var/jenkins_home/.aws

RUN curl -sL https://deb.nodesource.com/setup_10.x | sudo bash - && \
  apt-get install -y nodejs

# fix npm - not the latest version installed by apt-get
RUN npm install -g npm

# Prep Jenkins Directories
RUN mkdir /var/log/jenkins
RUN mkdir /var/cache/jenkins
RUN chown -R jenkins:jenkins /var/log/jenkins
RUN chown -R jenkins:jenkins /var/cache/jenkins
USER jenkins

# Set Defaults
ENV JENKINS_OPTS="--handlerCountMax=300 --logfile=/var/log/jenkins/jenkins.log  --webroot=/var/cache/jenkins/war"
