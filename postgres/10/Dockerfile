FROM postgres:10-alpine

COPY multiple-database.sh /docker-entrypoint-initdb.d/

CMD ["postgres"]

EXPOSE 5432