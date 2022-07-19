FROM alpine:latest

RUN apk add --no-cache tzdata && \
    rm -rf /var/cache/apk/*

WORKDIR /app

RUN wget -O UnblockNeteaseMusic.zip https://github.com/cnsilvan/UnblockNeteaseMusic/releases/latest/download/UnblockNeteaseMusic-linux-amd64.zip
RUN unzip UnblockNeteaseMusic.zip
RUN chmod +x UnblockNeteaseMusic

EXPOSE 80 443

CMD ["/app/UnblockNeteaseMusic"]
