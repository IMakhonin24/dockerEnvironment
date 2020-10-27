FROM php:7.3-fpm

WORKDIR /var/www

#Dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libzip-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev \
    libfreetype6 \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl

#Extensions
RUN docker-php-ext-install \
    pdo_mysql \
    mbstring \
    zip \
    exif \
    pcntl

#Composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

#NodeJS
RUN curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh && \
    bash nodesource_setup.sh && \
    rm nodesource_setup.sh && \
    apt-get update && apt-get install -y nodejs

#Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

## Add user for laravel application
#RUN groupadd -g 1000 www
#RUN useradd -u 1000 -ms /bin/bash -g www www
## Copy existing application directory contents
#COPY . /var/www
## Copy existing application directory permissions
#COPY --chown=www:www . /var/www
## Change current user to www
#USER www
## Expose port 9000 and start php-fpm server
#EXPOSE 9000
#CMD ["php-fpm"]
