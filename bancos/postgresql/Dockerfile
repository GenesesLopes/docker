ARG PGSQL_IMAGE=postgres:11-alpine
FROM ${PGSQL_IMAGE}

RUN cp /usr/share/zoneinfo/America/Bahia /etc/localtime && echo "America/Bahia" > /etc/timezone \
&& apk add nano

ENV TZ="America/Bahia"
ENV PGTZ="America/Bahia"

#USER postgres

EXPOSE 5432