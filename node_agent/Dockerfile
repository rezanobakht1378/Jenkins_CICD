FROM jenkins/ssh-agent:debian-jdk17

USER root

# Install Node.js, Docker CLI, and utilities
RUN apt-get update && \
    apt-get install -y curl zip unzip git docker.io bash && \
    apt-get clean

# Install Node.js LTS (via NodeSource)
#RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - && \
#    apt-get install -y nodejs

RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y nodejs

# Install SonarScanner
RUN curl -sSLo /tmp/sonarscanner.zip \
    https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-5.0.1.3006-linux.zip && \
    unzip /tmp/sonarscanner.zip -d /opt && \
    ln -s /opt/sonar-scanner-*/bin/sonar-scanner /usr/local/bin/sonar-scanner && \
    rm /tmp/sonarscanner.zip

# Set workdir
WORKDIR /workspace

# Add jenkins user to docker group (to run docker commands)
RUN usermod -aG docker jenkins

# Use Jenkins user
USER jenkins

# Verify installations (optional)
# RUN node -v && npm -v && docker --version && sonar-scanner --version
