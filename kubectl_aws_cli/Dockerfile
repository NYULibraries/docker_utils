FROM alpine:latest

# install aws-cli
RUN apk add --no-cache python3 \
  && pip3 install awscli --upgrade --user \
  && pip3 install awscli==1.14.5 --upgrade --user \
  && ln -s ~/.local/bin/aws /usr/local/bin/aws

# install kubectl
ARG KUBECTL_VERSION=v1.8.7
RUN apk --no-cache add openssl \
  && wget -q -O kubectl https://storage.googleapis.com/kubernetes-release/release/$KUBECTL_VERSION/bin/linux/amd64/kubectl \
  && chmod +x kubectl \
  && mv kubectl /usr/local/bin
