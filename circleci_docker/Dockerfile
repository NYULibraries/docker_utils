ARG DOCKER_VERSION=${DOCKER_VERSION}

FROM docker:${DOCKER_VERSION}-ce-git

ARG DOCKER_COMPOSE_VERSION=${DOCKER_COMPOSE_VERSION}

# install rsync, docker-compose, aws-cli, bash
# Bash used for BASH_ENV environment variables workaround https://circleci.com/docs/2.0/env-vars/#using-bash_env-to-set-environment-variables
RUN apk add --no-cache python3 rsync bash \
  && pip3 install docker-compose==${DOCKER_COMPOSE_VERSION} \
  && pip3 install awscli --upgrade --user \
  && ln -s ~/.local/bin/aws /usr/local/bin/aws
