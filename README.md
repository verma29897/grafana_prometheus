# PROMETHEUS & GRAFANA WITH NODE EXPORTER
* Prometheus is an open source tool for monitoring and alerting applications
* a multi-dimensional data model with time series data identified by metric name and key/value pairs
* Uses PromQL ( Prometheus Query Language)
* time series collection happens via a pull model over HTTP
* Targets System which you want to monitor can be identified using Service Discovery or by static configuration in the yaml file.

## Security Groups Configured on EC2 Instances
  * Prometheus EC2 Instance
      * Port 9090 — Prometheus Server
      * Port 9100 — Prometheus Node Exporter
      * Port 3000 — Grafana
  * Node EC2 Instances
      * Port 9100 — Prometheus Node Exporter

## Install Prometheus
```bash
git clone
./prometheus/install-prometheus.sh
```

## Install grafana
```bash
./grafana/install-grafana.sh
```
**********************************************************************************************************************************************
# Refreash rate of grafana dashbosard
```bash
vi /etc/grafana/grafana.ini 
[server]
# The http port  to use
http_port = 3000
```
```bash
[dashboards]
min_refresh_interval = 1s
refresh_interval = 1s,15s,1m,15m
```

update and uncommented

```bash
systemctl restart grafana-server
```

for change admin password
```
sudo grafana-cli admin reset-admin-password utk@admin123#
```
**********************************************************************************************************************************************
# send alert notification to gmail
create app password from gmail account

```bash
vi vi /etc/grafana/grafana.ini
#################################### SMTP / Emailing ##########################
[smtp]
enabled = true
host = smtp.gmail.com:587
user = kumar1000@gmail.com
# If the password contains # or ; you have to wrap it with triple quotes. Ex """#password;"""
password = rery roao rggn vzne
;cert_file =
;key_file =
skip_verify = true
from_address = kumar1000@gmail.com
from_name = Grafana
# EHLO identity in SMTP dialog (defaults to instance_name)
;ehlo_identity = dashboard.example.com
# SMTP startTLS policy (defaults to 'OpportunisticStartTLS')
;startTLS_policy = NoStartTLS

[emails]
;welcome_email_on_sign_up = false
;templates_pattern = emails/*.html

#################################### Logging ##########################
```
```bash
systemctl restart grafana-serve
```




## grafana admin password update
```bash
sudo grafana-cli admin reset-admin-password admin
```




