FROM php:apache

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get upgrade -y && apt-get install nano wget libpq-dev zip unzip -y && \
docker-php-ext-install bcmath pdo_pgsql pdo_mysql && a2enmod rewrite

RUN chmod -R 777 /var/www/html

EXPOSE 80 9000
