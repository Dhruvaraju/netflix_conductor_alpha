# Netflix Conductor

POC on Netflix Conductor workflows

## Installation

- Information on installing Netflix Conductor is available at https://conductor.netflix.com/devguide/running/docker.html
- Easiest way is to bring up teh environment using docker

Running Conductor Using Docker

In this article we will explore how you can set up Netflix Conductor on your local machine using Docker compose. The
docker compose will bring up the following:

    Conductor API Server
    Conductor UI
    Elasticsearch for searching workflows

Prerequisites

    Docker: https://docs.docker.com/get-docker/
    Recommended host with CPU and RAM to be able to run multiple docker containers (at-least 16GB RAM)

Steps

1. Clone the Conductor Code

```shell
$ git clone https://github.com/Netflix/conductor.git
```

2. Build the Docker Compose

```shell
$ cd conductor
conductor $ cd docker
docker $ docker-compose build
```

3. Run Docker Compose

```shell
docker $ docker-compose up
```

Once up and running, you will see the following in your Docker dashboard:

    Elasticsearch
    Conductor UI
    Conductor Server

You can access the UI & Server on your browser to verify that they are running correctly:
Conductor Server URL

http://localhost:8080

swagger
Conductor UI URL

http://localhost:5000/

conductor ui

4. Exiting Compose

Ctrl+c will exit docker compose.

To ensure images are stopped execute: docker-compose down.
Alternative Persistence Engines

By default docker-compose.yaml uses config-local.properties. This configures the memory database, where data is lost
when the server terminates. This configuration is useful for testing or demo only.

A selection of docker-compose-*.yaml and config-*.properties files are provided demonstrating the use of alternative
persistence engines.
File Containers
docker-compose.yaml

    In Memory Conductor Server
    Elasticsearch
    UI

docker-compose-dynomite.yaml

    Conductor Server
    Elasticsearch
    UI
    Dynomite Redis for persistence

docker-compose-postgres.yaml

    Conductor Server
    Elasticsearch
    UI
    Postgres persistence
```
docker-compose-prometheus.yaml Brings up Prometheus server
```
For example this will start the server instance backed by a PostgreSQL DB.
```
docker-compose -f docker-compose.yaml -f docker-compose-postgres.yaml up

```
