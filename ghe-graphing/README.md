# Running containers docker compose

```
docker-compose build
docker-compose up -d
```

Grafana runs on `http://[dockerhost]:3000` - Login is: `admin/admin`

# GitHub Enterprise collectd config

Enable [collectd forwarding in the GitHub Enterprise management console](https://help.github.com/enterprise/admin/articles/configuring-collectd/#enable-collectd-forwarding-on-github-enterprise), and set `[dockerhost]:25826` as the value.

# Individual Containers
## graphite

```
docker run -d --name graphite --restart=always -p 80:80 -p 2003-2004:2003-2004 -p 2023-2024:2023-2024 -p 8125:8125/udp -p 8126:8126 graphiteapp/graphite-statsd
```

## grafana

```
docker run -d --rm --name grafana -p 3000:3000 -v "$(pwd)"/dashboards:/var/lib/grafana/dashboards -v "$(pwd)"/provisioning:/etc/grafana/provisioning -e "GF_DASHBOARDS_JSON_ENABLED=true" -e "GF_DASHBOARDS_JSON_path=/var/lib/grafana/dashboards" --link graphite grafana/grafana
```

## collectd

```
docker build -t ghe-collectd .
docker run -d -p 25826:25826/udp --link graphite --rm --name ghe-collectd ghe-collectd
```
