FROM php:7.3-fpm

#NodeJs
RUN curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh &&
    bash nodesource_setup.sh &&
    rm nodesource_setup.sh

RUN    apt-get update \
    && apt-get install -y \
    zip \
    nodejs

RUN docker-php-ext-install \
    mysqli \
    pdo_mysql





RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer
