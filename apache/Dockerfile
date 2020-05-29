ARG APACHE_IMAGE=webdevops/php-apache-dev:7.4
FROM ${APACHE_IMAGE}
#composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
#instalando softwares auxiliares
RUN apt-get update && apt-get upgrade -y && apt-get install nano tzdata -y 
#Timezone
RUN echo "America/Bahia" > /etc/TZ && cp /usr/share/zoneinfo/America/Bahia /etc/localtime \
&& mkdir /.composer && chmod -R 777 /.composer;

ARG DOCUMENT_ROOT=/var/www
ENV WEB_DOCUMENT_ROOT=${DOCUMENT_ROOT}

COPY vhost.conf /etc/apache2/sites-enabled/vhost.conf

EXPOSE 80 443 9000

WORKDIR ${DOCUMENT_ROOT}

ENTRYPOINT ["/opt/docker/bin/entrypoint.sh"]

CMD ["supervisord"]

