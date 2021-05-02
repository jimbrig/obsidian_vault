---
creation date: 2021-04-24 11:37
modification date: Saturday 24th April 2021 11:37:38
tags: ["#dba", "#postgres", "#dev"]
author: Jimmy Briggs
---

# PostgreSQL Tools

## PostgreSQL Engine

- [PostgreSQL: The world's most advanced open source database](https://www.postgresql.org/)
	- [PostgreSQL: About](https://www.postgresql.org/about/)
	- [PostgreSQL: Documentation: 13: PostgreSQL 13.2 Documentation](https://www.postgresql.org/docs/13/index.html)
	- [PostgreSQL: Downloads](https://www.postgresql.org/download/)
- [PostgreSQL: Software Catalogue - Administration/development tools](https://www.postgresql.org/download/products/1-administrationdevelopment-tools/)

## CLI

-   [pgcli](https://github.com/dbcli/pgcli) - Postgres CLI with autocompletion and syntax highlighting
-   [pgsh](https://github.com/sastraxi/pgsh) - Branch your PostgreSQL Database like Git
-   [psql](https://www.postgresql.org/docs/current/static/app-psql.html) - The built-in PostgreSQL CLI client
-   [psql2csv](https://github.com/fphilipe/psql2csv) - Run a query in psql and output the result as CSV
-   [nancy](https://gitlab.com/postgres-ai/nancy) - The Nancy CLI is a unified way to manage automated database experiments either in clouds or on-premise
-   [schemaspy](https://github.com/schemaspy/schemaspy) - SchemaSpy is a JAVA JDBC-compliant tool for generating your database to HTML documentation, including Entity Relationship diagrams

## Monitoring



-   [check\_pgactivity](https://github.com/OPMDG/check_pgactivity) - check\_pgactivity is designed to monitor PostgreSQL clusters from Nagios. It offers many options to measure and monitor useful performance metrics.
-   [Check\_postgres](https://github.com/bucardo/check_postgres) - Nagios check\_postgres plugin for checking status of PostgreSQL databases.
-   [Instrumental](https://github.com/Instrumental/instrumentald) - Real-time performance monitoring, including [pre-made graphs](https://instrumentalapp.com/docs/instrumentald/postgresql#suggested-graphs) for ease of setup (Commercial Software)
-   [libzbxpgsql](https://github.com/cavaliercoder/libzbxpgsql) - Comprehensive PostgreSQL monitoring module for Zabbix.
-   [PMM](https://github.com/percona/pmm) - Percona Monitoring and Management (PMM) is a Free and Open Source platform for monitoring and managing PostgreSQL, MySQL, and MongoDB.
-   [Pome](https://github.com/rach/pome) - Pome stands for PostgreSQL Metrics. Pome is a PostgreSQL Metrics Dashboard to keep track of the health of your database.
-   [pgmetrics](https://pgmetrics.io/) - pgmetrics is an open-source, zero-dependency, single-binary tool that can collect a lot of information and statistics from a running PostgreSQL server and display it in easy-to-read text format or export it as JSON and CSV for scripting.
-   [pg\_view](https://github.com/zalando/pg_view) - Open-source command-line tool that shows global system stats, per-partition information, memory stats and other information.
-   [pgwatch2](https://github.com/cybertec-postgresql/pgwatch2) - Flexible and easy to get started PostgreSQL metrics monitor focusing on Grafana dashboards.
-   [pgbench](https://www.postgresql.org/docs/devel/static/pgbench.html) - Run a benchmark test on PostgreSQL.
-   [opm.io](http://opm.io/) - Open PostgreSQL Monitoring is a free software suite designed to help you manage your PostgreSQL servers. It can gather stats, display dashboards and send warnings when something goes wrong.
-   [okmeter.io](https://okmeter.io/pg) - Commercial SaaS agent-based monitoring with a very detailed PostgreSQL plugin. It automatically gathers 100s of stats, displays dashboards on every aspect and sends alerts when something goes wrong (Commercial Software).

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

