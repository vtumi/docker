FROM php:7-cli-alpine3.8

RUN echo -e "http://mirrors.aliyun.com/alpine/v3.8/main/\n\
http://mirrors.aliyun.com/alpine/v3.8/community/\n\
@community http://mirrors.aliyun.com/alpine/edge/community\n\
@testing http://mirrors.aliyun.com/alpine/edge/testing" > /etc/apk/repositories \
    && apk update
RUN apk add --no-cache tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk del tzdata
