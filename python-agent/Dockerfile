#FROM jenkins/ssh-agent:debian-jdk17 as ssh-agent

#RUN apt-get update
#RUN apt-get install -y python3 python3-pip python3-venv zip

FROM jenkins/ssh-agent:debian-jdk17 as ssh-agent

# Install Python and utilities
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv zip curl unzip && \
    apt-get clean
RUN apt install python3.11-venv
RUN curl -sSLo sonarscanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-5.0.1.3006-linux.zip
RUN unzip sonarscanner.zip -d /opt
RUN ln -s /opt/sonar-scanner-*/bin/sonar-scanner /usr/local/bin/sonar-scanner
# Define SonarScanner version
#ENV SONAR_SCANNER_VERSION=5.0.1.3006
#ENV SONAR_SCANNER_HOME=/opt/sonar-scanner

# Download and install SonarScanner
#RUN curl -L -o /tmp/sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SONAR_SCANNER_VERSION}-linux.zip && \
#    unzip /tmp/sonar-scanner.zip -d /opt && \
#    mv /opt/sonar-scanner-* ${SONAR_SCANNER_HOME} && \
#    ln -s ${SONAR_SCANNER_HOME}/bin/sonar-scanner /usr/local/bin/sonar-scanner && \
#    rm /tmp/sonar-scanner.zip

# Set SonarScanner in PATH
ENV PATH="${SONAR_SCANNER_HOME}/bin:${PATH}"
