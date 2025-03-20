# StarlinkStatus with docker

Change YOURAPIKEY in docker-compose.yaml to api received from [https://starlinkstatus.space/](https://starlinkstatus.space/).

If you want another Interval you can also set the INTERVAL variable to the interval you wan't in seconds (default: 900).

```yaml docker-compose.yaml
services:
  starlinkstatus:
    container_name: Starlinkstatus
    image: Scootter23/starlinkstatus:latest
    restart: always
    environment:
      - APIKEY=YOURAPIKEY           # Replace YOURAPIKEY e.g APIKEY=a1b2c3d4e5f6
      - INTERVAL=900                # 900 secs = 15min, so when CRONJOB=false this will run every 15 min
      - DISHY=true                  # Set to true to get Dish Stats
      - SPEEDTEST=true              # Set to true to run Speedtests      
```

Next run:
```
docker-compose up -d
```

And you're ready :)
