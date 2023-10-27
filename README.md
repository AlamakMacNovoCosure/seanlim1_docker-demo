## Recap
``` bash
docker build . -t flask-app:v2
docker run -dp 8080:8080 flask-app:v2
docker ps -a
docker stop <containerID>
docker rm <containerID>
```

## Images
Pull the following images and compare them:
- alpine
- ubuntu
- nicolaka/netshoot

``` bash
docker images
docker pull <imageName>
```

## Exec
``` bash
docker run nicolaka/netshoot
docker run -d nicolaka/netshoot sleep 99999
docker exec -it <containerID> sh
```

## Run Binaries
``` bash
docker run nicolaka/netshoot curl www.google.com
docker run nicolaka/netshoot whois www.google.com
docker run nicolaka/netshoot dig www.google.com
```

## Volumes
``` bash
docker volume ls
# create shared volume
docker volume create demo
# create container
docker run --mount type=volume,src=demo,target=/tmp -d alpine sleep 99999
docker run --mount type=volume,src=demo,target=/tmp -d alpine sleep 99999
docker exec -it <containerID> sh

# Task: Verify that /app/demo directory in the containers are empty
# Task: Within one of the contaioner, create a file to the /app/demo. Then verify on the other container.
# Task: Stop and remove containers
# Task: Remove network
```

## Networks
``` bash
docker network ls
# create shared network
docker network create demo
# create containers
docker run --network demo -d -p 8080:8080 flask-app
docker run --network demo -d nicolaka/netshoot sleep 99999
docker exec -it <containerID> sh

# Task: Using netshoot, make a request to flask app
# Task: View the logs of flask app
# Task: Create netshoot container in detached mode, to make a request to flask app (every 1 second)
# Task: Stop and remove containers
# Task: Remove network
```

## Docker Compose
``` bash
docker compose up -d
docker compose down
```

## Reference
- [Docker overview](https://docs.docker.com/get-started/overview/)
- [Docker commands](https://docs.docker.com/engine/reference/commandline/cli/) 