FROM debian:jessie

ENV DB_NAME=maindb
ENV DB_USER=main
ENV DB_PASSWORD=password

USER root
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y mysql-server
COPY docker-entrypoint.sh docker-entrypoint.sh
COPY install.sh install.sh
COPY init.sql /docker-entrypoint-initdb.d/
RUN ./install.sh
CMD DB_NAME=${DB_NAME} DB_USER=${DB_USER} DB_PASSWORD=${DB_PASSWORD}
ENTRYPOINT ./docker-entrypoint.sh
EXPOSE 3306