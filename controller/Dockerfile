FROM docker:23-cli as docker-cli

FROM jenkins/jenkins:lts-jdk17

LABEL maintainer="glagasse@glagasse.com"

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /var/jenkins_home/casc.yaml
ENV TZ=America/Los_Angeles

USER root

RUN ln -snf /usr/share/zoneinfo/"${TZ}" /etc/localtime && echo "${TZ}" > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

COPY --from=docker-cli /usr/local/bin/docker /usr/local/bin/docker

USER jenkins

COPY --chown=jenkins:jenkins plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN /bin/jenkins-plugin-cli --plugin-file /usr/share/jenkins/ref/plugins.txt

COPY casc.yaml /var/jenkins_home/casc.yaml

VOLUME /var/jenkins_home
