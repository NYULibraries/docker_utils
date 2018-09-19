ARG DOCKER_VERSION=${DOCKER_VERSION}

FROM docker:${DOCKER_VERSION}

ARG DOCKER_COMPOSE_VERSION=${DOCKER_COMPOSE_VERSION}

# install rsync, docker-compose, aws-cli
RUN apk add --no-cache python3 rsync \
  && pip3 install docker-compose==${DOCKER_COMPOSE_VERSION} \
  && pip3 install awscli --upgrade --user \
  && ln -s ~/.local/bin/aws /usr/local/bin/aws
