FROM php:7.4.3-fpm

MAINTAINER Koji Kashiwabara

RUN apt-get update && apt-get install -y libonig-dev libxml2-dev

RUN docker-php-ext-install mbstring

WORKDIR /src
