# Docker Monitoring
Monitor your Docker containers using prometheus, cAdvisor, node-exporter, and grafana.

## Pre-requisites

* docker-compose

## Setup and Install

```docker-compose up```

Goto http://localhost:3000 for grafana dashboard (default user/pass : admin/admin )

## Problems and hack-fix

Prometheus docker container spinup commented out of docker-compose.yml because docker-compose volumes are completely broken:
The contents of the source folder become directories instead of folders on the target container. If anyone can point me to the fix, I'd be super grateful because NOONE has been able to figure it out on the Web.

This is what happens if you comment the prometheus section back in:

prometheus       | ts=2024-06-23T03:30:42.144Z caller=main.go:537 level=error msg="Error loading config (--config.file=/etc/prometheus/prometheus.yml)" file=/etc/prometheus/prometheus.yml err="read /etc/prometheus/prometheus.yml: is a directory"
prometheus exited with code 2

So, need to spin up the prometheus container outside of docker-compose like so:

```docker run -p 9090:9090 -v ./prometheus/prometheus.yml prom/prometheus```

Is it a Windows issue? "Mystere et boule de gomme", as the Frensh say.

## Configuration

By default, the following ports are exposed:

* Prometheus: 9090
* Grafana 3000
* cAdvisor: 8080

These ports can be customized via the environment variables (or .env file entries) `PROMETHEUS_PORT`, `GRAFANA_PORT`, and `CADVISOR_PORT`, respectively.
