FROM mysql

RUN chmod -R 777 var/lib/mysql

ENTRYPOINT [ "docker-entrypoint.sh","mysqld" ]

EXPOSE 3306