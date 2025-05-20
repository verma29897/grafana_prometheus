# Download the Apache Node Exporter
 
## Here you need to download the Apache2 node exporter by execute the given command step by step.
```bash
apt-get update
cd /tmp 
curl -s https://api.github.com/repos/Lusitaniae/apache_exporter/releases/latest   | grep browser_download_url   | grep linux-amd64 | cut -d '"' -f 4 | wget -qi -
tar -xzvf apache_exporter-*.linux-amd64.tar.gz
sudo cp -ivr  apache_exporter-*.linux-amd64/apache_exporter /usr/local/bin
sudo chmod +x /usr/local/bin/apache_exporter
apache_exporter --version
```
## after that we need to create apache_exporter.service systemD file in /etc/systemd/system/ execute teh given command for the same.
```bash
sudo vim /etc/systemd/system/apache_exporter.service
```
```bash
[Unit]
Description=Prometheus Apache Exporter
Documentation=https://github.com/Lusitaniae/apache_exporter

[Service]
ExecStart=/usr/local/bin/apache_exporter --insecure --scrape_uri=http://localhost/server-status/?auto --web.listen-address=0.0.0.0:9100 --telemetry.endpoint=/metrics

SyslogIdentifier=apache_exporter
Restart=always

[Install]
WantedBy=multi-user.target
```

## Save and exit from the vim text editor, and Restart the apache_expoter_service.
```bash
sudo systemctl daemon-reload
sudo systemctl start apache_exporter.service
sudo systemctl enable apache_exporter.service
```

source --> https://www.techbeginner.in/2021/01/install-and-configure-apache-node-exporter-with-prometheus-on-ubuntu-16-04-18-04-20-4-lts.html



allow from firewall 
```bash
ufw status
ufw allow 9100
```
