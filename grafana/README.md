# Running your Grafana container
Start your container binding the external port 3000.

`$ docker run -d --name=grafana -p 3000:3000 grafana/grafana`

`$ docker run --rm -d --name=grafana --net=influxdb -p 3000:3000 grafana/grafana`

You can also make sure that it is correctly listening on port 3000.

`$ netstat -tulpn | grep 3000`

# Grafana installation

https://grafana.com/docs/grafana/latest/installation/docker/


`$ docker network inspect bridge | grep influxdb -A 5`