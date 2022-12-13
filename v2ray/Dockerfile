
FROM alpine

ARG VERSION=v4.31.0

RUN wget https://github.com/v2fly/v2ray-core/releases/download/${VERSION:-v4.31.0}/v2ray-linux-64.zip \
  && mkdir -p /usr/local/etc/v2ray \
  && unzip v2ray-linux-64.zip -d /usr/local/etc/v2ray \
  && rm v2ray-linux-64.zip \
  && ln -s /usr/local/etc/v2ray/v2ray /usr/local/bin/v2ray \
  && ln -s /usr/local/etc/v2ray/v2ctl /usr/local/bin/v2ctl 

