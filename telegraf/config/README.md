# Telegraf

# Command

`docker run --net=container:influxdb telegraf`

# Exposed Ports

8125 StatsD
8092 UDP
8094 TCP

# Generate sample config

`$ docker run --rm telegraf telegraf config > $PWD/config/telegraf.conf`

# Run with the config

`$ docker run -v $PWD/config/telegraf.conf:/etc/telegraf/telegraf.conf:ro telegraf`

`$ $  docker run -d --rm --name=telegraf \
      --net=influxdb \
      -v $PWD/config/telegraf.conf:/etc/telegraf/telegraf.conf:ro \      telegraf

$ docker logs -f telegraf`

# Docker Image 

To run the Telegraf Docker image, run the following command.

`$ docker run -d --rm --name=telegraf \
      --net=container:<influx_container_id> \
      -e HOST_PROC=/host/proc \
      -v /proc:/host/proc:ro \
      -v $PWD/config/telegraf.conf:/etc/telegraf/telegraf.conf:ro \
      telegraf`