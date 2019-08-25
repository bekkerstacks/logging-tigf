# logging-tigf
Monitoring &amp; Logging with Telegraf, InfluxDB, Grafana and FluentD

## Logging your Application:

Logs will be pushed to fluentd, which will then push to influxdb. 

- driver: pushing to fluentd
- option: `fluentd-address: 172.18.0.1:24224` (defaults to localhost)
- option: `tag: {type=docker.stack_name=tig.service_name=webapp}`
- option: `fluentd-async-connect: "true"`

To push your logs to influxdb, set this configuration to your compose:

```
    logging:
      driver: fluentd
      options:
        tag: docker.tig.webapp
        fluentd-async-connect: "true"
```
