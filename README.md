# Monitoring

This uses on Docker to setup Kebo's monitoring and alerting system including- [Prometheus](https://prometheus.io/docs/introduction/overview/) (plus node and blackbox exporters), [AlertManager](https://prometheus.io/docs/alerting/alertmanager/), [Grafana](https://grafana.com/), [NGINX](https://www.nginx.com/) and [Certbot](https://certbot.eff.org/).

Nginx and Certbot are used to provide the relevant HTTP based services and automate SSL certificate provision.

## Requirements

The setup requires some secret details (API Keys, Passwords, etc) which are provided by a separate .env file containing the secret details in environment variables. These are used by the configuration files where needed.

The host machine you will be deploying the services to must have [Docker](https://docs.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed.

## Usage

Clone the repository on to the machine, provide the required environment variables (ideally in an .env file) and then use the command `docker-compose up -d`.

## Updating

To update an existing service `docker-compose up -d --no-deps --build [service-name]`.

## Backing up Data

There are two data volumes `prometheus_data` and `grafana_data`, which need to be persisted to maintain state. The following commands can be used to backup and restore the volumes.

Backup:
`docker run -it -v [volume_name]:/volume -v /tmp:/backup alpine \ tar -cjf /backup/[volume_name].tar.bz2 -C /volume ./`

Restore:
`docker run -it -v [volume_name]:/volume -v /tmp:/backup alpine \ sh -c "rm -rf /volume/* ; tar -C /volume/ -xjf /backup/[volume_name].tar.bz2"`

## Purpose

We have made this public as a reference for others who might want to do something similar. Feel free to copy it and customise for yourself or let us know about any improvements that we could make.