# Supported tags and respective `Dockerfile` links

- `0.5`, `0.5.0`, `latest` [(Dockerfile)](https://github.com/machine-data/docker-apache_exporter/blob/master/Dockerfile)

# apache_exporter on Docker

This repository holds a build definition and supporting files for building a Docker image to run [apache_exporter](https://github.com/Lusitaniae/apache_exporter).
It is published as automated build `machine-data/apache_exporter` on [Docker Hub](https://registry.hub.docker.com/u/machinedata/apache_exporter/).

## What is apache_exporter?

[apache_exporter](https://github.com/Lusitaniae/apache_exporter) exports apache mod_status statistics via HTTP for Prometheus consumption.

## Quickstart

In the minimal configuration you just need to pass the `-scrape_uri` parameter.


```sh
$ docker run -d -p 9117:9117 \
    machine-data/apache_exporter apache_exporter -scrape_uri=http://apache/server-status?auto
```

## Ports

- `9117`: The default port where apache_exporter is listening.

## Legal

apache_exporter is a creation of [Lusitaniae](https://github.com/Lusitaniae/apache_exporter) and was originally developed by [neezgee](https://github.com/neezgee)
It is licensed under the [MIT license](https://github.com/Lusitaniae/apache_exporter/blob/master/LICENSE).

docker-apache_exporter is licensed under the [Apache 2.0 license](https://github.com/machine-data/docker-apache_exporter/blob/master/LICENSE), was created by [Jodok Batlogg](https://github.com/jodok).
Copyright 2018 [Crate.io, Inc.](https://crate.io).

## Contributing

Thanks for considering contributing to docker-apache_exporter!
The easiest way to contribute is either by filing an [issue on Github](https://github.com/machine-data/docker-apache_exporter/issues) or to [fork the repository](https://github.com/machine-data/docker-apache_exporter/fork) to create a pull request.
