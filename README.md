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
    machine-data/apache_exporter apache_exporter --scrape_uri=http://apache/server-status?auto
```

Full list of flags:

```
  -insecure
        Ignore server certificate if using https. (default false)
  -log.level value
        Only log messages with the given severity or above. Valid levels: [debug, info, warn, error, fatal, panic]. (default info)
  -scrape_uri string
        URI to apache stub status page. (default "http://localhost/server-status/?auto")
  -telemetry.address string
        Address on which to expose metrics. (default ":9117")
  -telemetry.endpoint string
        Path under which to expose metrics. (default "/metrics")
  -version
        Version of the Apache exporter.
```

 If your server-status page is secured by http auth, add the credentials to the scrape URL following this example:

```
http://user:password@localhost/server-status?auto
```

## Collectors

Apache metrics:

```
# HELP apache_accesses_total Current total apache accesses (*)
# TYPE apache_accesses_total counter
# HELP apache_scoreboard Apache scoreboard statuses
# TYPE apache_scoreboard gauge
# HELP apache_sent_kilobytes_total Current total kbytes sent (*)
# TYPE apache_sent_kilobytes_total counter
# HELP apache_cpu_load CPU Load (*)
# TYPE apache_cpu_load gauge
# HELP apache_up Could the apache server be reached
# TYPE apache_up gauge
# HELP apache_uptime_seconds_total Current uptime in seconds (*)
# TYPE apache_uptime_seconds_total counter
# HELP apache_workers Apache worker statuses
# TYPE apache_workers gauge
```

Exporter process metrics:

```
# HELP http_request_duration_microseconds The HTTP request latencies in microseconds.
# TYPE http_request_duration_microseconds summary
# HELP http_request_size_bytes The HTTP request sizes in bytes.
# TYPE http_request_size_bytes summary
# HELP http_response_size_bytes The HTTP response sizes in bytes.
# TYPE http_response_size_bytes summary
# HELP process_cpu_seconds_total Total user and system CPU time spent in seconds.
# TYPE process_cpu_seconds_total counter
# HELP process_max_fds Maximum number of open file descriptors.
# TYPE process_max_fds gauge
# HELP process_open_fds Number of open file descriptors.
# TYPE process_open_fds gauge
# HELP process_resident_memory_bytes Resident memory size in bytes.
# TYPE process_resident_memory_bytes gauge
# HELP process_start_time_seconds Start time of the process since unix epoch in seconds.
# TYPE process_start_time_seconds gauge
# HELP process_virtual_memory_bytes Virtual memory size in bytes.
# TYPE process_virtual_memory_bytes gauge
```

Metrics marked '(*)' are only available if ExtendedStatus is On in apache webserver configuration. In version 2.3.6, loading mod_status will toggle ExtendedStatus On by default.


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
