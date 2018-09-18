ARG DOCKER_VERSION=18.06.1-ce-git
ARG DOCKER_COMPOSE_VERSION=1.22.0

FROM docker:${DOCKER_VERSION}

# install rsync, docker-compose, aws-cli
RUN apk add --no-cache python3 rsync \
  && pip3 install docker-compose==${DOCKER_COMPOSE_VERSION} \
  && pip3 install awscli --upgrade --user \
  && ln -s ~/.local/bin/aws /usr/local/bin/aws
