FROM mysql:8

#Set environment variable(s) in the key-value format
ENV MYSQL_ROOT_PASSWORD=root \
    MYSQL_DATABASE=discovery

COPY src/main/resources/createdb.sql /docker-entrypoint-initdb.d/

HEALTHCHECK --interval=1m CMD mysql -uroot -p${MYSQL_ROOT_PASSWORD} -e "SHOW DATABASES;"