FROM php:apache

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
EXPOSE 9000

ENTRYPOINT [ "php-fpm" ]
RUN apk add --no-cache freetype libpng libjpeg-turbo freetype-dev nano git libpng-dev libjpeg-turbo-dev libzip-dev $PHPIZE_DEPS openssl-dev
RUN set -ex \
  && apk --no-cache add \
    postgresql-dev zip unzip tzdata
RUN docker-php-ext-configure gd \
    --with-gd \
    --with-freetype-dir=/usr/include/ \
    --with-png-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/ && \
  NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
  docker-php-ext-install -j${NPROC} gd && \
  apk del --no-cache freetype-dev libpng-dev libjpeg-turbo-dev && pecl install mongodb
RUN docker-php-ext-enable mongodb
RUN docker-php-ext-install pdo_pgsql pdo_mysql mysqli pgsql exif zip bcmath
RUN echo "America/Bahia" > /etc/TZ && cp /usr/share/zoneinfo/America/Bahia /etc/localtime && echo "America/Bahia" > /etc/timezone && \
sed "s/;date.timezone =/date.timezone = America\/Bahia/g" /usr/local/etc/php/php.ini-development  > /usr/local/etc/php/php.ini && \
sed -i "s/expose_php = On/expose_php = Off/g" /usr/local/etc/php/php.ini  
#autocomplete Terminal
ARG AUTOCOMPLETE=false
RUN if [ ${AUTOCOMPLETE} = true ]; then \
  apk add --no-cache zsh && \
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" && \
  git clone https://github.com/zsh-users/zsh-autosuggestions.git /root/.oh-my-zsh/custom/plugins/zsh-autosuggestions && \
  git clone https://github.com/zsh-users/zsh-syntax-highlighting.git /root/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting && \
  sed -i "s/plugins=(git)/plugins=(git zsh-autosuggestions zsh-syntax-highlighting)/g" /root/.zshrc \
;fi




