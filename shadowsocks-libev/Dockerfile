FROM shadowsocks/shadowsocks-libev:latest

MAINTAINER eirture@gmail.com

ENV PLUGIN v2ray-plugin
ENV PLUGIN_OPTS server
ARG VERSION=v1.3.0

USER root

RUN set -ex \
    && wget -cq -O /root/v2ray-plugin.tar.gz https://github.com/shadowsocks/v2ray-plugin/releases/download/${VERSION}/v2ray-plugin-linux-amd64-${VERSION}.tar.gz \
    && tar zxf /root/v2ray-plugin.tar.gz -C /root \
    && mv /root/v2ray-plugin_linux_amd64 /usr/local/bin/v2ray-plugin \
    && rm -f /root/v2ray-plugin.tar.gz

CMD exec ss-server \
    -s $SERVER_ADDR \
    -p $SERVER_PORT \
    -k ${PASSWORD:-$(hostname)} \
    -m $METHOD \
    -t $TIMEOUT \
    -d $DNS_ADDRS \
    -u \
    --plugin $PLUGIN \
    --plugin-opts $PLUGIN_OPTS \
    $ARGS

EXPOSE 8388

