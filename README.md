# PostrgreSQL Docker with PLV8 embed

This image is based on the official [Postgres 10](https://hub.docker.com/_/postgres/) and embed the [PLV8](https://plv8.github.io/) extension.

> PLV8 is a trusted Javascript language extension for PostgreSQL. It can be used for stored procedures, triggers, etc.

# Start a postgres plv8 instance

`$ docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d waldo2188/postgres-plv8`

This image includes EXPOSE 5432 (the postgres port), so standard container linking will make it automatically available to the linked containers. The default postgres user and database are created in the entrypoint with initdb.

## Activate PLV8 extension

Remeber, you must activate this extension in each database where you want use it.

`docker exec some-postgres psql -U postgres -c "CREATE EXTENSION IF NOT EXISTS plv8;"`

Now you can check if the extension is well activated :

`docker exec some-postgres psql -U postgres -c "SELECT plv8_version();"`

