# logging-tigf
Monitoring &amp; Logging with Telegraf, InfluxDB, Grafana and FluentD

## Usage:

Set your domain and deploy the stack:

```
$ export DOMAIN=mydomain.com
$ docker stack deploy -c docker-compose.yml tig
```

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

## Documentation:

- [Wiki: Configure Custom Exporters](wiki/Custom-Script-for-Telegraf-Input-Exec)

## Endpoints:

- https://grafana.${DOMAIN}

## Screenshots

Add the InfluxDB Logs Datasource:

![image](https://user-images.githubusercontent.com/50801771/63646485-d1d1bb80-c713-11e9-8311-c8955e470795.png)

Add the InfluxDB Metrics Datasource:

![image](https://user-images.githubusercontent.com/50801771/63646487-d72f0600-c713-11e9-8452-c17cd09c6257.png)

View the logs:

![image](https://user-images.githubusercontent.com/50801771/63646494-f6c62e80-c713-11e9-99ae-6820ec046d17.png)

View the Metrics:

![image](https://user-images.githubusercontent.com/50801771/63646579-6983d980-c715-11e9-8467-3f5d763d0fc7.png)
