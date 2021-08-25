# mini-node-exporter

Hi, mini-node-exporter is a project as the interview for [mentorship program of Chaos Mesh on LFX Mentorship 2021 fall](https://mentorship.lfx.linuxfoundation.org/project/8db683b0-0273-4a83-9ed9-4c33ee2cfcf0).

You could upload your codes via GitHub(or other platform), and email me(strruiling@gmail.com) the repo link. Or just email me the codes by `tar` or `zip` pack.

Please finish this project before [Mon, August 30, 2021 12:00 +8:00](https://time.is/compare/1200_30_Aug_2021_in_Shanghai).

## Overview

First of all, we do not restrict the programing language and frameworks, use any tech stack as your wish.

Build, and run an application on **linux**, it could expose several metrics of the host. Then use the prometheus to scrape this exporter, and draw a dashboard on grafana.

There are two goals of this small project:

1. build a web application that exposes several metrics 
1. collect and make a dashboard for the exposed metrics

### Goal 1

Build one web application called `mini-node-exporter`, it should listen on `0.0.0.0:23333`, and expose several endpoints:

- `/info/hostname` show the hostname with plain text
- `/info/uptime` show the uptime of the system in seconds with plain text
- `/info/load` show the load average in 1m, 5m and 15m with JSON, example `{"1m": 0.57, "5m":0.80, "15m":0.77}`
- `/metrics` expose metrics that could be scraped by prometheus

Required metrics that should be exposed in `/metrics`:

- `node_load`: load average, with a label for three duraion, for example:
- `node_uptime`: uptime of the system in seconds

example:

```
# TYPE node_load gauge
node_load{duration="1m"} 0.57
node_load{duration="5m"} 0.80
node_load{duration="15m"} 0.77
# TYPE node_uptime gauge
node_uptime 9246.58
```

optional bonus:

- build a docker image for the application, publish it on DockerHub, and provide the `Dockerfile` in the repo

### Goal 2

Startup the monitoring stack of prometheus and grafana, and show these metrics on a grafana dashboard.

You should:

- execute `mini-node-exporter` on your host
- execute prometheus on your host, and configure it for collecting metrics from `mini-node-exporter`
- execute grafana on your host, and configure it for using prometheus as the datasource
- create a grafana dashboard for showing these metrics provided by `mini-node-exporter`, in any forms.

Please let it collector data for several minutes and take a screenshot of your grafana dashboard, email me the screenshot. :P

optional bonus:

- orcherating the monitroing stack and `mini-node-exporter` application by docker-compose/vagrant/kubernetes or any other forms, provides the manifest files in the repo

## References

some information that might be helpful:

- https://prometheus.io/docs/prometheus/latest/getting_started/
- https://prometheus.io/docs/prometheus/latest/configuration/configuration/
- https://prometheus.io/docs/instrumenting/clientlibs/
- https://man7.org/linux/man-pages/man5/proc.5.html

## Other

Happy Coding!
