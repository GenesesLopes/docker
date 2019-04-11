FROM mysql

RUN chmod -R 777 var/lib/mysql && rm /etc/localtime && ln -s /usr/share/zoneinfo/America/Bahia /etc/localtime && echo "America/Bahia" > /etc/timezone

ENTRYPOINT [ "docker-entrypoint.sh","mysqld" ]

EXPOSE 3306