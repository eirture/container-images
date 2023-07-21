FROM nsqio/nsq:v1.2.1 AS source

FROM alpine:latest

RUN mkdir -p /data
WORKDIR      /data

COPY --from=source /usr/local/bin/*nsq* /usr/local/bin/
RUN ln -s /usr/local/bin/*nsq* / \
 && ln -s /usr/local/bin/*nsq* /bin/

