
FROM ubuntu:20.04

LABEL MAINTAINER='Jie Liu <eirture@gmail.com>'

RUN set -ex \
    && apt update \
    && apt install -y wget \
    && wget -cq -O ./mongosh.deb https://downloads.mongodb.com/compass/mongodb-mongosh_1.0.4_amd64.deb \
    && apt install -y ./mongosh.deb \
    && rm mongosh.deb \
    && apt-get clean autoclean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

