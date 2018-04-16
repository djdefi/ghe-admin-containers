# Graylog2 log stack

Full docs: https://github.com/Graylog2/graylog-docker

1. Edit `GRAYLOG_WEB_ENDPOINT_URI=http://127.0.0.1:9000/api` in `docker-compose.yml` to be the URL or IP that you use to access the docker host.
2. Create an admin password by running `echo -n "CHANGEME" | shasum -a 256`, then use that sha2 as the `GRAYLOG_ROOT_PASSWORD_SHA2` (admin password) in `docker-compose.yml`.
3. Launch the stack:
  ```
  docker-compose up -d
  ```

4. Login to web interface: `http://[dockerhost]:9000` - Default user/pass: `admin/admin`

## External Ports:
- 5514 tcp/udp for syslog
- 9000 tcp for web interface

# GitHub Enterprise syslog config

Enable [log forwarding in the GitHub Enterprise management console](https://help.github.com/enterprise/admin/articles/log-forwarding/), and set `[dockerhost]:5514` as the value.
