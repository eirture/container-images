
FROM alpine:3.18

ENV OPENSSL_CONF=/etc/ssl/openssl.cnf

RUN apk add --no-cache openconnect && \
    rm -rf /var/cache/apk/* && \
    sed -i '/providers = provider_sect/a\
ssl_conf = ssl_sect\n\
\n\
[ssl_sect]\n\
system_default = system_default_sect\n\
\n\
[system_default_sect]\n\
Options = UnsafeLegacyRenegotiation' /etc/ssl/openssl.cnf
