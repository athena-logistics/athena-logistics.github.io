---
layout: default
title: Hosting Instructions
permalink: '/hosting'
---

# Hosting Instructions

## General

The application has to be hosted behind a Load Balancer that offers HTTPS termination. **The iOS / Android apps will not work without HTTPS.**

### Requirements

* Postgres: 14
* Elixir (only from source): As specified in the [`.tool-versions`](https://github.com/athena-logistics/athena-backend/blob/main/.tool-versions) file
* Erlang (only from source): As specified in the [`.tool-versions`](https://github.com/athena-logistics/athena-backend/blob/main/.tool-versions) file
* NodeJS (only from source): As specified in the [`.tool-versions`](https://github.com/athena-logistics/athena-backend/blob/main/.tool-versions) file

### Environment Variables

* `ECTO_IPV6` - (`true` \| `false`; default `false`) - Connect to the database via IPv6 or IPv4
* `DATABASE_SSL` - (`true` \| `false`; default `false`) - Connect to the database via TLS
* `DATABASE_PREPARE` - (`named` \| `unnamed`; default `named`) - Use named prepared statements for DB (set to `unnamed` when using PgBouncer)
* `DATABASE_URL` - PostgreSQL db URL
* `DATABASE_PORT` - (default: `5432`) PostgreSQL db port (not compatible with `DATABASE_URL`)
* `DATABASE_USER` - (default: `root`) PostgreSQL db user (not compatible with `DATABASE_URL`)
* `DATABASE_PASSWORD` - (default: empty) PostgreSQL db password (not compatible with `DATABASE_URL`)
* `DATABASE_NAME` - (default: `athena_prod`) PostgreSQL db name (not compatible with `DATABASE_URL`)
* `DATABASE_HOST` - (default: `localhost`) PostgreSQL db host (not compatible with `DATABASE_URL`)
* `PORT` - (default: `4000`) Port to run the webserver on
* `EXTERNAL_HOST` - (default: `localhost`) External host of the webserver (used in URLs for QR code)
* `EXTERNAL_PORT` - (default: `4000`) External port of the webserver (used in URLs for QR code)
* `EXTERNAL_SCHEME` - (default: `http`) External port of the webserver (used in URLs for QR code)
* `SECRET_KEY_BASE` - Secret key to sign cookies
* `LOG_LEVEL` - (`debug` \| `info` \| `warn` \| `error`, default: `info`) Log level of the application
* `BASIC_AUTH_USERNAME` - (default: `admin`) Log In user to Admin Area
* `BASIC_AUTH_PASSWORD` - (default: `admin`) Log In password to Admin Area
* `BASIC_AUTH_REALM` - (default: `Admin Area`) Name of Basic Auth prompt to Admin Area

## Docker

The Athena Event Logistics backend is published as a [GitHub Package](https://github.com/athena-logistics/athena-backend/pkgs/container/athena-backend).

```console
docker run \
    --name athena \
    --port 4000:4000 \
    -e "[ENV Variables]" \
    ghcr.io/athena-logistics/athena-backend:[VERSION]
```

*Authentication using `docker login` is required for all GitHub packages.*

## From Source

Athena can be run from source. to do this follow the development instructions in the [README](https://github.com/athena-logistics/athena-backend/blob/main/README.md#development).