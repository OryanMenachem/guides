# Docker CLI Commands

## Containers

-   **docker run IMAGE** --- Run a container from an image\
-   **docker run -d IMAGE** --- Run in background\
-   **docker run -p HOST:CONTAINER IMAGE** --- Map ports\
-   **docker run --name NAME IMAGE** --- Run with custom name\
-   **docker start CONTAINER** --- Start a stopped container\
-   **docker stop CONTAINER** --- Stop a running container\
-   **docker restart CONTAINER** --- Restart container\
-   **docker kill CONTAINER** --- Force-stop container\
-   **docker pause CONTAINER** --- Pause all processes\
-   **docker unpause CONTAINER** --- Resume\
-   **docker logs CONTAINER** --- View logs\
-   **docker logs -f CONTAINER** --- Follow logs\
-   **docker exec -it CONTAINER bash** --- Enter container shell\
-   **docker cp SRC CONTAINER:DEST** --- Copy into container\
-   **docker cp CONTAINER:SRC DEST** --- Copy out\
-   **docker ps** --- List running containers\
-   **docker ps -a** --- List all containers\
-   **docker rm CONTAINER** --- Remove container\
-   **docker rm -f CONTAINER** --- Force remove\
-   **docker container prune** --- Remove stopped containers

## Images

-   **docker pull IMAGE** --- Download image\
-   **docker build -t NAME .** --- Build from Dockerfile\
-   **docker build -f FILE -t NAME .** --- Build with custom file\
-   **docker images** --- List images\
-   **docker rmi IMAGE** --- Remove image\
-   **docker rmi -f IMAGE** --- Force remove\
-   **docker image prune** --- Remove unused images\
-   **docker save IMAGE -o FILE.tar** --- Export image\
-   **docker load -i FILE.tar** --- Import image

## Volumes

-   **docker volume create NAME** --- Create volume\
-   **docker volume ls** --- List volumes\
-   **docker volume inspect NAME** --- View details\
-   **docker volume rm NAME** --- Remove\
-   **docker volume prune** --- Delete unused volumes

## Networks

-   **docker network ls** --- List networks\
-   **docker network create NAME** --- Create network\
-   **docker network rm NAME** --- Remove\
-   **docker network inspect NAME** --- Inspect\
-   **docker network prune** --- Remove unused networks

## System

-   **docker info** --- System info\
-   **docker version** --- Versions\
-   **docker stats** --- Resource usage live\
-   **docker top CONTAINER** --- Processes in container\
-   **docker history IMAGE** --- Image layer history\
-   **docker system df** --- Docker disk usage\
-   **docker system prune** --- Cleanup unused resources\
-   **docker system prune -a** --- Cleanup ALL unused

## Compose (Bonus)

-   **docker compose up** --- Start services\
-   **docker compose up -d** --- Start in background\
-   **docker compose down** --- Stop and remove\
-   **docker compose logs** --- Show logs\
-   **docker compose logs -f** --- Follow logs\
-   **docker compose ps** --- List services\
-   **docker compose build** --- Build images
