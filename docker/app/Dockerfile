FROM php:7.3-fpm

WORKDIR /var/www

#Dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libzip-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libwebp-dev \
    libxpm-dev \
    libfreetype6 \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl


RUN docker-php-ext-configure gd \
    --with-gd \
    --with-webp-dir \
    --with-jpeg-dir \
    --with-png-dir \
    --with-zlib-dir \
    --with-xpm-dir \
    --with-freetype-dir

#Extensions
RUN docker-php-ext-install \
    mysqli \
    pdo_mysql \
    mbstring \
    zip \
    exif \
    pcntl \
    gd

#Composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

#NodeJS
RUN curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh && \
    bash nodesource_setup.sh && \
    rm nodesource_setup.sh && \
    apt-get update && apt-get install -y nodejs

#todo Скопировать файлы в новый билд
#Download bitrix file
#RUN curl -sL http://dev.1c-bitrix.ru/download/scripts/bitrix_server_test.php -o bitrix_server_test.php
#RUN curl -sL http://www.1c-bitrix.ru/download/scripts/restore.php -o public/restore.php

#Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*