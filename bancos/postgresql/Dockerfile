FROM postgres:alpine

RUN cp /usr/share/zoneinfo/America/Bahia /etc/localtime && echo "America/Bahia" > /etc/timezone

ENV TZ="America/Bahia"
ENV PGTZ="America/Bahia"

USER postgres

EXPOSE 5432