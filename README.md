# Docker Monitoring
Monitor your Docker containers using prometheus, node-exporter, and grafana on Windows

## Pre-requisites

* docker-compose

## Setup and Install

```docker-compose up```

Goto http://localhost:3000 for grafana dashboard (default user/pass : admin/admin )

## Configuration

By default, the following ports are exposed:

* Prometheus: 9090
* Grafana 3000
* cAdvisor: 8080

These ports can be customized via the environment variables (or .env file entries) `PROMETHEUS_PORT`, `GRAFANA_PORT`, and `CADVISOR_PORT`, respectively.
