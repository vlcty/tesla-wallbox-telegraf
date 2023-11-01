# tesla-wallbox-telegraf

A config skeleton to query a Tesla Wallbox gen 3 with Telegraf using board tools only. It collects wifi, lifetime and vital stats.

> **Warning**   
> This software is designed around Europe's three phase power grid. If you are located outside that region this software might not work for you.

All you need to do is adapting the output section to match your needs. Currently it only logs to stdout. The IP address of the wallbox can either be hardcoded or passed by the WALLBOX_HOST environment variable. Unless Tesla changes something this config is pretty stable and does not change.

## Sample integrations

### CLI call

> docker container run --rm -e "WALLBOX_HOST=10.10.0.109" -v ./telegraf.conf:/etc/telegraf/telegraf.conf:ro telegraf:alpine

### Compose file

```
services:
    image: telegraf:alpine
    restart: always
    volumes:
        - ./telegraf.conf:/etc/telegraf/telegraf.conf:ro
    environment:
        WALLBOX_HOST: 192.168.1.220
```
