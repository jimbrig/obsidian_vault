---
creation date: 2021-04-24 11:37
modification date: Saturday 24th April 2021 11:37:38
tags: ["#dba", "#postgres", "#dev"]
author: Jimmy Briggs
---

# PostgreSQL Tools

## Core

### PostgreSQL Engine

- [PostgreSQL: The world's most advanced open source database](https://www.postgresql.org/)
	- [PostgreSQL: About](https://www.postgresql.org/about/)
	- [PostgreSQL: Documentation: 13: PostgreSQL 13.2 Documentation](https://www.postgresql.org/docs/13/index.html)
	- [PostgreSQL: Downloads](https://www.postgresql.org/download/)
- [PostgreSQL: Software Catalogue - Administration/development tools](https://www.postgresql.org/download/products/1-administrationdevelopment-tools/)

## CLI

-   [pgcli](https://github.com/dbcli/pgcli) \- Postgres CLI with autocompletion and syntax highlighting
-   [pgsh](https://github.com/sastraxi/pgsh) \- Branch your PostgreSQL Database like Git
-   [psql](https://www.postgresql.org/docs/current/static/app-psql.html) \- The built-in PostgreSQL CLI client
-   [psql2csv](https://github.com/fphilipe/psql2csv) \- Run a query in psql and output the result as CSV
-   [nancy](https://gitlab.com/postgres-ai/nancy) \- The Nancy CLI is a unified way to manage automated database experiments either in clouds or on-premise
-   [schemaspy](https://github.com/schemaspy/schemaspy) \- SchemaSpy is a JAVA JDBC-compliant tool for generating your database to HTML documentation, including Entity Relationship diagrams

## GUI


-   
    
-   dbeaver -
    
-   Valentina Studio -
    
-   

- pgAdmin4
- Dbeaver
- Beekeeper Studio
- Valentina Studio
- DBTarzan


## Developer Tools

- pgHero
- pgSync
- postgres-ai/database-lab
- DBML, dbdocs.io, dbdiagram.io
- PostgREST
- postGIS
- WAL-G:
	- [wal-g/wal-g: Archival and Restoration for Postgres (github.com)](https://github.com/wal-g/wal-g#configuration)


## Docker
- [postgres (docker.com)](https://hub.docker.com/_/postgres)
- [postgres/Dockerfile](https://github.com/docker-library/postgres/blob/7bd41786539082857396f4d1b4f1cb326ebee8de/13/Dockerfile)
- [postgresai/extended-postgres (docker.com)](https://hub.docker.com/r/postgresai/extended-postgres)

```
docker pull postgresai/extended-postgres
```

- [postgresai/sync-instance (docker.com)](https://hub.docker.com/r/postgresai/sync-instance)

```powershell
docker pull postgresai/sync-instances

docker run \
   --name sync_instance \
   --env PGDATA=/var/lib/postgresql/pgdata \
   --env WALG_GS_PREFIX="gs://{BUCKET}/{SCOPE}" \
   --env GOOGLE_APPLICATION_CREDENTIALS="/etc/sa/credentials.json" \
   --volume {PATH_TO_CREDENTIALS}:/etc/sa/credentials.json \
   --volume /var/lib/dblab/data:/var/lib/postgresql/pgdata:rshared \
   --detach \
   postgresai/sync-instance:13
```


[postgrest/postgrest (docker.com)](https://hub.docker.com/r/postgrest/postgrest)
[postgrestoauth/api (docker.com)](https://hub.docker.com/r/postgrestoauth/api)
[PostgREST Documentation — PostgREST 7.0.1 documentation](https://postgrest.org/en/stable/#)

## Extensions

- [Table of Contents — pgRouting Manual (3.1)](https://docs.pgrouting.org/latest/en/index.html)
- 

***
Links: 
Source:

