FROM php:7.3-fpm

RUN    apt-get update \
    && apt-get install -y \
    zip

RUN docker-php-ext-install \
    mysqli \
    pdo_mysql

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer
