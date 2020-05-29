ARG PHP_IMAGE=php:7.4.4-fpm-alpine
FROM ${PHP_IMAGE}

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
EXPOSE 9000

RUN apk add --no-cache freetype libpng libjpeg-turbo freetype-dev nano git libpng-dev libjpeg-turbo-dev libzip-dev $PHPIZE_DEPS 
RUN set -ex \
  && apk --no-cache add \
    postgresql-dev zip unzip tzdata
RUN docker-php-ext-configure gd \
    --with-freetype=/usr/include/ \
    --with-jpeg=/usr/include/ && \
  NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
  docker-php-ext-install -j${NPROC} gd && \
  apk del --no-cache freetype-dev libpng-dev libjpeg-turbo-dev && pecl install mongodb xdebug
## para versoes ateriores a 7.3
# RUN docker-php-ext-configure gd \
#     --with-png-dir=/usr/include/ \
#     --with-freetype-dir=/usr/include/ \
#   --with-jpeg-dir=/usr/include/ && \
#   NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
#   docker-php-ext-install -j${NPROC} gd && \
#   apk del --no-cache freetype-dev libpng-dev libjpeg-turbo-dev && pecl install mongodb xdebug

RUN docker-php-ext-enable mongodb xdebug
RUN docker-php-ext-install pdo_pgsql pdo_mysql exif zip bcmath

#Timezone
RUN echo "America/Bahia" > /etc/TZ && cp /usr/share/zoneinfo/America/Bahia /etc/localtime && echo "America/Bahia" > /etc/timezone && \
sed "s/;date.timezone =/date.timezone = America\/Bahia/g" /usr/local/etc/php/php.ini-development  > /usr/local/etc/php/php.ini && \
sed -i "s/expose_php = On/expose_php = Off/g" /usr/local/etc/php/php.ini  
#Debbug php
RUN echo "xdebug.remote_autostart=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_enable=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_host=host.docker.internal" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null

#Cron

RUN mkdir /etc/periodic/minute && chmod a+x -R /etc/periodic/minute && chmod -R 777 /etc/crontabs/root;
RUN crontab -l | { cat; echo "*       *       *       *       *       run-parts /etc/periodic/minute"; } | crontab -

#ENTRYPOINT [ "php-fpm" ];
# ENTRYPOINT [ "/bin/sh" ];

#CMD ["php-fpm"];
CMD ["sh", "-c", "crond && /usr/local/sbin/php-fpm"]

