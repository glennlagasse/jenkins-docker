FROM docker:23-cli as docker-cli

FROM jenkins/agent:latest-jdk17

LABEL maintainer="glagasse@glagasse.com"

ENV TZ=America/Los_Angeles

USER root

RUN ln -snf /usr/share/zoneinfo/"${TZ}" /etc/localtime && echo "${TZ}" > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

COPY --from=docker-cli /usr/local/bin/docker /usr/local/bin/docker

RUN usermod -a -G root jenkins

USER jenkins
