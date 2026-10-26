# Task 1: Docker image with Git

## Dockerfile
- Base image: alpine
- Installs git using `apk add`

## Commands
1. `docker build -t ZohiabZafar/devops:q1.v1 .`
2. `docker images`
3. `docker run -dit --name q1container ZohaibZafar/devops:q1.v1`
4. `docker attach q1container`, then `git --version`
5. `docker push ZohaibZafar/devops:q1.v1`

## Observations
- The image is tagged with repository ZohaibZafar/devops and tag q1.v1. It is very small because alpine is minimal.
- `docker attach` connects the terminal to the main process (PID 1) of a running container. It is useful for viewing the container's output or interacting with its main process. Exiting with `exit` stops the container, so detach with Ctrl+P, Ctrl+Q. `docker exec -it` is the safer way to open a shell.
