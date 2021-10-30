
FROM alpine:3

LABEL MAINTAINER="eirture@gmail.com"

ARG VERSION=v0.0.1

RUN set -ex \
    && wget -cq -O /root/socks5-proxy.tgz https://github.com/eirture/socks5-proxy/releases/download/${VERSION}/socks5-proxy-${VERSION:1}-linux-amd64.tar.gz \
    && tar zxf /root/socks5-proxy.tgz -C /root \
    && mv /root/socks5-proxy /usr/local/bin/socks5-proxy \
    && rm -f /root/socks5-proxy.tgz

