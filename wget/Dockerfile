FROM alpine:latest
RUN apk add --no-cache --update wget && rm -rf /var/cache/apk/*
COPY entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]
CMD ["wget"]
