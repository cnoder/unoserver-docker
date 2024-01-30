# Unoserver Docker Image

Docker image for unoserver
## Changes from unoserver-docker
- Rewritten entrypoint: Supports interactive, remote, and docker exec.
- Customizable Port: Default 2002 Port for Running Multiple Instances on a Single Machine.

## How to use it

### Build image:

    docker build -t your-image-name .
If you already have the ghcr.io/unoconv/unoserver-docker image locally.

    docker build -f Dockerfile_local -t  <your-image-name> .
### How to run:

you can run as origin image ghcr.io/unoconv/unoserver-docker

```shell
docker run -it -v <your directory>:/data/ <your-image-name> unoconvert /data/document.docx /data/document.pdf
```

You can run it in the background also.
if we use port 2008,and use contain name unoserver-background-docker
```shell
docker run --name unoserver-background-docker -e UNOSERVER_PORT=2008 -d -v <your directory>:/data/ <your-image-name>
```
If you don't want to install Unoserver on your host machine.
```shell
docker exec unoserver-background-docker unoconvert --port 2008 /data/example.docx /data/example.pdf 
```
or we can use local unoserver cli on host machine. it can connect container port 2008
```shell
unoconvert --port 2008 /data/example.docx /data/example.pdf 
```
### todo
-[ ] we also can start several containers by docker compose
```shell
docker composer up
```

-[ ] use supervisor numprocs  to start multiple instances in a container.

-[ ] use nginx proxy multiple instances.

### Requirements

You need the following tools:

- A bash compliant command line

- Docker & Docker composer installed and in your path

