# Quick Start

## Build
```bash
docker build -t motion:latest ./
```
## Run

Run the container with configs , e.g.,
```bash
docker run -it --rm \
    -p 8081:8081 \
    -p 8080:8080 \
    -v /etc/motion:/usr/local/etc/motion \
    --device /dev/video0  \
    motion:latest
```

