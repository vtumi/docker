ARG ALPINE_VERSION=3.16
FROM alpine:${ALPINE_VERSION}

# Install packages
RUN apk add --no-cache nginx

STOPSIGNAL SIGQUIT

EXPOSE 80 443
CMD ["nginx", "-g", "'daemon off;'"]
