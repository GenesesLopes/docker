FROM php:fpm-alpine

RUN docker-php-ext-install pdo_mysql bcmath
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

EXPOSE 9000

ENTRYPOINT [ "php-fpm" ]

