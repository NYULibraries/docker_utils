# Docker Utils

Utility Docker images, mostly for use in Circle

## CircleCI Docker

Built on docker's docker image, we install some dependencies we typically use in Circle: docker-compose, aws cli, and rsync.

## Kubectl AWS CLI

Alpine image with kubectl and aws cli installed

## Wget

Just an alpine image with wget, inspired by [appropriate/curl](https://github.com/appropriate/docker-curl).

## Stress

Fedora image with stress and some system utilities installed for stress testing and monitoring resource usage in clusters
