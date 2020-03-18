# Docker commands

`$ docker run -p 8086:8086 \
      -v $PWD/db:/var/lib/influxdb \
      influxdb`

`$ docker network create influxdb`

`$ docker run --rm --name influxdb --net=influxdb -p 8086:8086 -v $PWD/config/influxdb.conf:/etc/influxdb/influxdb.conf:ro -v $PWD/db:/var/lib/influxdb influxdb -config /etc/influxdb/influxdb.conf`

# Exposed Ports

The following ports are important and are used by InfluxDB.

8086 HTTP API port
2003 Graphite support, if it is enabled

# Configuration

Generate the default configuration

`$ docker run --rm influxdb influxd config > $PWD/config/influxdb.conf`

# Graphite

`docker run -p 8086:8086 -p 2003:2003 \
    -e INFLUXDB_GRAPHITE_ENABLED=true \
    influxdb`

# HTTP API

Show Databases

`$ curl -G http://localhost:8086/query --data-urlencode "q=SHOW DATABASES"`

Create Database

`$ curl -G http://localhost:8086/query --data-urlencode "q=CREATE DATABASE mydb"`

Inserting in to DB

`$ curl -i -XPOST 'http://localhost:8086/write?db=mydb' --data-binary 'cpu_load_short,host=server01,region=us-west value=0.64 1434055562000000000'`


# CLI/SHELL

Start the container:

`$ docker run --name=influxdb -d -p 8086:8086 influxdb`

Run the influx client in this container:

`$ docker exec -it influxdb influx`

Or run the influx client in a separate container:

`$ docker run --rm --link=influxdb -it influxdb influx -host influxdb`


# Docker Hub

https://hub.docker.com/_/influxdb

