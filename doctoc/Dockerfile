FROM node:20-alpine
ENV NPM_CONFIG_LOGLEVEL warn
RUN node --version
RUN npm  --version
RUN npm install -g doctoc && rm -rf ~/.npm

WORKDIR /app

ENTRYPOINT ["doctoc"]
