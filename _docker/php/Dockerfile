FROM php:8.3-fpm-alpine

RUN apk add --update linux-headers

# ensure www-data user exists
RUN set -x ; \
  addgroup -g 82 -S www-data ; \
  adduser -u 82 -D -S -G www-data www-data && exit 0 ; exit 0

ADD ./_docker/php/php.ini /usr/local/etc/php/php.ini

#
# ensure www-data user exists
RUN set -x ; \
  addgroup -g 82 -S www-data ; \
  adduser -u 82 -D -S -G www-data www-data && exit 0 ; exit 0

# Installing dependencies
RUN apk --update add wget \
      curl \
      build-base \
      libmemcached-dev \
      libmcrypt-dev \
      libxml2-dev \
      pcre-dev \
      zlib-dev \
      autoconf \
      cyrus-sasl-dev \
      libgsasl-dev \
      oniguruma-dev \
      openssl \
      openssl-dev \
      gmp gmp-dev \
      nano \
      zip \
      libzip-dev \
      && pecl install xdebug redis \
      && docker-php-ext-enable xdebug

# Install extensions
RUN docker-php-ext-install pcntl gmp zip

#Install GD package:
RUN apk add --update --no-cache freetype-dev libjpeg-turbo-dev jpeg-dev libpng-dev; \
    docker-php-ext-configure gd --with-jpeg=/usr/include/ --with-freetype=/usr/include/ && \
    docker-php-ext-install gd

# Clean up
RUN rm /var/cache/apk/*

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /application
