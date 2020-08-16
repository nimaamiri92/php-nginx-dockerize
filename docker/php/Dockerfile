FROM php:7.2.8-fpm

LABEL maintainer="majid8911303@gmail"

ARG WWW_DATA_USER_ID
ARG NEWRELIC_ENABLED
ARG NEWRELIC_KEY

ENV PHP_REDIS_EXTENSION_VERSION 4.1.1
ENV XDEBUG_VERSION 2.6.0


RUN apt-get update && apt-get install -y \
    gcc \
    musl-dev \
    autoconf \
    zlib1g-dev \
    zip \
    vim \
    unzip \
    wget \
    git \
    libssl1.0-dev \
    libpng-dev \
    libxml2-dev \
    && docker-php-ext-install -j$(nproc) pdo pdo_mysql bcmath zip pcntl gd soap

## Isntall XDEBUG

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug


#Add npm and nodejs
RUN curl -sL https://deb.nodesource.com/setup_8.x |  bash - && apt-get install -y build-essential nodejs

# Installing composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer
