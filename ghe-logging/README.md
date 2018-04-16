# Graylog2 log stack

https://github.com/Graylog2/graylog-docker

```
docker-compose up -d
```

Web interface: `http://[dockerhost]:9000` - Login as `admin/admin`

# GitHub Enterprise syslog config

Enable [log forwarding in the GitHub Enterprise management console](https://help.github.com/enterprise/admin/articles/log-forwarding/), and set `[dockerhost]:514` as the value.
