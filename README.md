# Grafana (MySQL) + Nginx reverse proxy
For educational purposes only :D

### Create a reverse proxy

Creating a config file
```sh
$ nano nginx-revers-storage/conf.d/grafana.conf
```
Add this ...
```sh
upstream grafana_dashboard {
  server    grafana_dashboard:3000;
}
server {
    listen 80;
    listen [::]:80;
    server_name grafana.local;
    location / {
        proxy_pass http://grafana_dashboard;
    }
}
```
