FROM php:7.2.0-fpm-alpine3.7

COPY repositories /etc/apk/repositories

# Mysql
RUN docker-php-ext-install pdo_mysql

# gd
RUN apk add --no-cache libpng-dev libjpeg-turbo-dev freetype-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

# mcrypt
RUN apk add --no-cache -t .build autoconf g++ make \
    apk add --no-cache libmcrypt-dev \
    && pecl install mcrypt-1.0.1 \
    && docker-php-ext-enable mcrypt \
    && apk del -t .build

# Redis
RUN set -x \
    && apk add --no-cache -t .build git \
    && mkdir -p /usr/src/php/ext/ \
    && git clone -b master https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis \
    && docker-php-ext-install redis \
    && apk del -t .build
