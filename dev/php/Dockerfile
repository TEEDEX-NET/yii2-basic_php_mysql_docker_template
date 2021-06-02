FROM php:8.0.6-fpm

COPY opcache.ini /usr/local/etc/php/conf.d/

#   Install packages
RUN apt-get update && apt-get upgrade -y \
    && apt-get install apt-utils git zip vim libzip-dev libgmp-dev -y\
    && apt-get install libffi-dev libssl-dev libpng-dev libwebp-dev -y \
    && apt-get install libjpeg-dev libfreetype6-dev -y \
#
#   Install php extensions
    && docker-php-ext-install -j$(nproc) sockets zip gmp pcntl bcmath ffi \
    && PHP_OPENSSL=yes pecl install ev xdebug \
    && docker-php-ext-enable ev xdebug \
    && docker-php-ext-configure gd \
       --with-webp=/usr/include/ \
       --with-freetype=/usr/include/ \
       --with-jpeg=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo_mysql \
#
#   Clean installers
    && docker-php-source delete \
    && apt-get autoremove --purge -y && apt-get autoclean -y && apt-get clean -y

# Install composer
RUN curl --silent --show-error https://getcomposer.org/installer | \
    php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /www