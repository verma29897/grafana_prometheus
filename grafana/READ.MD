dashboard id's 
11074 


# refreash dashboard 

## vi /etc/grafana/grafana.ini
```bash
#################################### Dashboards History ##################
[dashboards]
# Minimum dashboard refresh interval. When set, this will restrict users to set the refresh interval of a dashboard lower than given interval. Per default this is 5 seconds.
# The interval string is a possibly signed sequence of decimal numbers, followed by a unit suffix (ms, s, m, h, d), e.g. 30s or 1m.

min_refresh_interval = 1s
refresh_intervals = 1s,5s,10s,30s,1m,5m,15m,30m,1h
```


