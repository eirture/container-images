
FROM alpine:3

LABEL MAINTAINER="eirture@gmail.com"

ARG VERSION=v0.1.0

RUN set -ex \
    && wget -cq -O /root/tcp-proxy.tgz https://github.com/eirture/tcp-proxy/releases/download/${VERSION}/tcp-proxy-${VERSION}-linux-amd64.tgz \
    && tar zxf /root/tcp-proxy.tgz -C /root \
    && mv /root/tcp-proxy /usr/local/bin/tcp-proxy \
    && rm -f /root/tcp-proxy.tgz


