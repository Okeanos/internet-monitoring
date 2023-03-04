# A docker stack which monitors your home network

Here's a quick start to set up a Docker [Prometheus](http://prometheus.io/) stack containing Prometheus, Grafana
and  [github-exporter](https://github.com/infinityworksltd/github-exporter) to collect and graph GitHub statistics.

## Pre-requisites

- [Docker](https://docs.docker.com/engine/installation/)
  - [Docker Compose](https://docs.docker.com/compose/install/)

## Installation

Clone the project to your Docker host.

```shell
cp .env.template .env
```

Now edit the `.env` file and set the Grafana admin password.

Afterwards modify the preconfigured settings for

- Grafana:
  - `grafana/provisioning/*`
- Prometheus:
  - `prometheus/alert.rules`
  - `prometheus/prometheus.yml`

Add the following entry to your `hosts` file:

```txt
127.0.0.1 internet-monitoring.test
```

You can then start the stack with:

```shell
docker compose up -d
```

Open a browser and navigate to [http://internet-monitoring.test](http://internet-monitoring.test) to access Grafana. A
Traefik dashboard is available
at [http://internet-monitoring.test:8080/dashboard/](http://internet-monitoring.test:8080/dashboard/).

## Acknowledgements

Forked from [Brian Christner's GitHub Repo Monitoring](https://github.com/vegasbrianc/github-monitoring).

Additional projects were used to inspire this version:

- [Jeff Geerling's Internet Pi](https://github.com/geerlingguy/internet-pi)
- [Max Rydahl Andersen's Internet Monitoring](https://github.com/maxandersen/internet-monitoring)
