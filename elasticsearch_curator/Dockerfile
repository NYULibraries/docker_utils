# modified from https://github.com/bobrik/docker-curator
FROM alpine:3.8

RUN addgroup -g 1000 -S docker && \
  adduser -u 1000 -S -G docker docker

ARG BUILD_PACKAGES="py-pip gcc libffi python-dev libffi-dev musl-dev linux-headers openssl-dev"
ARG RUN_PACKAGES="python py-setuptools libssl1.0 py-cffi py-openssl"
RUN apk --no-cache add $RUN_PACKAGES $BUILD_PACKAGES \
  && pip install elasticsearch-curator==5.5.4 \
  && pip install boto3==1.4.8 \
  && pip install requests-aws4auth==0.9 \
  && pip install cryptography==2.1.3 \
  && apk del $BUILD_PACKAGES \
  && sed -i '/import sys/a urllib3.contrib.pyopenssl.inject_into_urllib3()' /usr/bin/curator \
  && sed -i '/import sys/a import urllib3.contrib.pyopenssl' /usr/bin/curator \
  && sed -i '/import sys/a import urllib3' /usr/bin/curator \
  && chown docker:docker /usr/bin/curator

USER docker:docker 

CMD ["/usr/bin/curator"]
