FROM php:7.2.12-fpm

RUN apt-get update && apt-get install -y libonig-dev libxml2-dev libzip-dev zip unzip

RUN docker-php-ext-install mbstring zip opcache

WORKDIR /src
