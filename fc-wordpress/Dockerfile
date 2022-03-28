ARG ALPINE_VERSION=3.15
FROM alpine:${ALPINE_VERSION}
# Setup document root
WORKDIR /mnt/www/wordpress

# Install packages and remove default server definition
RUN apk add --no-cache \
  curl \
  nginx \
  php8 \
  php8-curl \
  php8-dom \
  php8-fpm \
  php8-gd \
  php8-mbstring \
  php8-mysqli \
  php8-opcache \
  php8-openssl \
  php8-pdo \
  php8-pdo_sqlite \
  php8-session \
  php8-sqlite3 \
  php8-xml \
  php8-xmlreader \
  php8-zlib \
  supervisor

# Create symlink so programs depending on `php` still function
RUN ln -s /usr/bin/php8 /usr/bin/php

# Configure nginx
COPY config/nginx.conf /etc/nginx/nginx.conf

# Configure PHP-FPM
COPY config/fpm-pool.conf /etc/php8/php-fpm.d/www.conf
COPY config/php.ini /etc/php8/conf.d/custom.ini

# Configure supervisord
COPY config/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Make sure files/folders needed by the processes are accessable when they run under the nobody user
RUN chown -R 10003:10003 /mnt/www/wordpress /run /var/lib/nginx /var/log/nginx

# Switch to use a non-root user from here on
USER 10003:10003

# Expose the port nginx is reachable on
EXPOSE 9000

# Let supervisord start nginx & php-fpm
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]

# Configure a healthcheck to validate that everything is up&running
HEALTHCHECK --timeout=10s CMD curl --silent --fail http://127.0.0.1:9000/fpm-ping
