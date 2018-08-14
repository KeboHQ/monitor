# Monitoring

This uses on Docker to setup Kebo's monitoring and alerting system including- [Prometheus](https://prometheus.io/docs/introduction/overview/) (plus node and blackbox exporters), [AlertManager](https://prometheus.io/docs/alerting/alertmanager/), [Grafana](https://grafana.com/) and [Traefik](https://traefik.io/).

## Requirements

The setup requires various secret details (API Keys, Passwords, etc) which are provided by a separate .env file. These are used by several configuration files where needed.

The host machine you will be deploying the services to must have [Docker](https://docs.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed.

## Usage

Clone the repository on to the machine, provide the required environment variables (ideally in an .env file) and then use the command `docker-compose up -d`.

## Updating

To update an existing service `docker-compose up -d --no-deps --build [service-name]`.

## Backing up Data

There are three data volumes `prometheus_data` and `grafana_data`, which need to be persisted to maintain state.

## Purpose

We have made this public as a reference for others who might want to do something similar. Feel free to copy it and customise for yourself or let us know about any improvements that we could make.