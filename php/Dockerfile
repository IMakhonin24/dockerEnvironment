FROM php:7.3-fpm

RUN    apt-get update \
    && apt-get install -y \
       libpng-dev \
       libwebp-dev \
       libjpeg62-turbo-dev \
       libpng-dev \
       libxpm-dev \
       libfreetype6-dev

RUN docker-php-ext-configure gd \
    --with-gd \
    --with-webp-dir \
    --with-jpeg-dir \
    --with-png-dir \
    --with-zlib-dir \
    --with-xpm-dir \
    --with-freetype-dir

RUN docker-php-ext-install \
    mysqli \
    pdo_mysql \
    gd

RUN    sed -i 's/;max_input_vars = 1000/max_input_vars = 40000/g' /usr/local/etc/php/php.ini-production \
    && sed -i 's/memory_limit = 128M/memory_limit = 512M/g' /usr/local/etc/php/php.ini-production \
    && sed -i 's/short_open_tag = Off/short_open_tag = On/g' /usr/local/etc/php/php.ini-production \
    && sed -i 's/;mbstring.internal_encoding =/mbstring.internal_encoding = utf-8/g' /usr/local/etc/php/php.ini-production \
    && sed -i 's/;mbstring.func_overload = 0/mbstring.func_overload = 2/g' /usr/local/etc/php/php.ini-production

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"