VERSION 0.6

FROM nginx:alpine
WORKDIR /srv/app

ARG EARTHLY_GIT_HASH
ARG REPO=bfolkens/nginx-redirector

build:
  RUN apk add --update --no-cache bash

  COPY bin/startup.sh /usr/local/bin/startup.sh

  EXPOSE 80

  CMD ["/usr/local/bin/startup.sh"]

  SAVE IMAGE --push $REPO/nginx-redirector:latest
  SAVE IMAGE --cache-from=$REPO/nginx-redirector:latest --push $REPO/nginx-redirector:$EARTHLY_GIT_HASH
