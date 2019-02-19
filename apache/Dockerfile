FROM php:apache

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get upgrade -y && apt-get install nano wget libpq-dev -y && \
docker-php-ext-install bcmath pdo_pgsql pdo_mysql && a2enmod rewrite

EXPOSE 80
