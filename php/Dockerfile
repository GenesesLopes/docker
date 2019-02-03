FROM php:fpm-alpine

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
EXPOSE 9000

ENTRYPOINT [ "php-fpm" ]

RUN docker-php-ext-install bcmath
RUN set -ex \
  && apk --no-cache add \
    postgresql-dev
RUN docker-php-ext-install pdo_pgsql
RUN docker-php-ext-install pdo_mysql 


