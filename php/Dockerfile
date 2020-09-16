FROM php:7.3-fpm

RUN    apt-get update \
    && apt-get install -y

RUN docker-php-ext-install \
    mysqli \
    pdo_mysql

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"