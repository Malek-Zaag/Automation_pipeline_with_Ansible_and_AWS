FROM postgres:17.4-bullseye

ENV POSTGRES_USER=admin
ENV POSTGRES_PASSWORD=admin
ENV POSTGRES_HOST=localhost

VOLUME [ "/var/lib/postgresql/data" ]
WORKDIR /
COPY init.sql /docker-entrypoint-initdb.d/

EXPOSE 5432
