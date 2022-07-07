ARG ALPINE_VERSION=3.16
FROM alpine:${ALPINE_VERSION}

# Install packages and remove default server definition
RUN apk add --no-cache \
  curl \
  php8 \
  php8-curl \
  php8-dom \
  php8-fpm \
  php8-gd \
  php8-json \
  php8-mbstring \
  php8-mysqli \
  php8-opcache \
  php8-openssl \
  php8-pdo \
  php8-pdo_mysql \
  php8-phar \
  php8-session \
  php8-xml \
  php8-xmlreader \
  php8-zlib

# Add composer
RUN curl -sS https://getcomposer.org/installer | php && \
    chmod +x composer.phar && \
    mv composer.phar /usr/local/bin/composer

STOPSIGNAL SIGQUIT

EXPOSE 9000
CMD ["php-fpm"]
