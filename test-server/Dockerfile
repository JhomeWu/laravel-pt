FROM alpine:3.12
RUN echo http://dl-cdn.alpinelinux.org/alpine/v3.12/community/ >> /etc/apk/repositories \
    && apk upgrade --update \
    && apk add wrk
