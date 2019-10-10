FROM jenkins/jenkins
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
COPY config.xml.override /usr/share/jenkins/ref/config.xml.override
COPY credentials.xml /usr/share/jenkins/ref/credentials.xml
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state
COPY hudson.tasks.Maven.xml /usr/share/jenkins/ref/
USER root
RUN apt-get update && apt-get install -y apt-transport-https dirmngr maven lsb-core software-properties-common
RUN uname -a
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
RUN apt-get update && apt-get install -y docker-ce docker-ce-cli containerd.io
RUN curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose
USER jenkins
