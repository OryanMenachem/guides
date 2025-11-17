# Docker CLI Cheat Sheet  🐳

## Containers
| Command                                  | Description                                      | Example / Note                          |
|------------------------------------------|--------------------------------------------------|-----------------------------------------|
| `docker run IMAGE`                       | Run a container from an image                    |                                         |
| `docker run -d IMAGE`                    | Run in background (detached)                     |                                         |
| `docker run -p HOST:CONTAINER IMAGE`     | Map ports (host → container)                     | `docker run -p 8080:80 nginx`           |
| `docker run --name NAME IMAGE`           | Give the container a custom name                 |                                         |
| `docker start CONTAINER`                 | Start a stopped container                        |                                         |
| `docker stop CONTAINER`                  | Stop a running container                         |                                         |
| `docker restart CONTAINER`               | Restart container                                |                                         |
| `docker kill CONTAINER`                  | Force-stop container                             |                                         |
| `docker pause CONTAINER`                 | Pause all processes                              |                                         |
| `docker unpause CONTAINER`               | Resume paused container                          |                                         |
| `docker logs CONTAINER`                  | Show container logs                              |                                         |
| `docker logs -f CONTAINER`               | Follow logs in real-time                         |                                         |
| `docker exec -it CONTAINER bash`         | Open interactive shell inside container          | Use `sh` if no bash                     |
| `docker cp HOST_PATH CONTAINER:DEST`     | Copy file/dir from host → container              |                                         |
| `docker cp CONTAINER:SRC HOST_DEST`      | Copy file/dir from container → host              |                                         |
| `docker ps`                              | List running containers                          |                                         |
| `docker ps -a`                           | List all containers (including stopped)          |                                         |
| `docker rm CONTAINER`                    | Remove stopped container                         |                                         |
| `docker rm -f CONTAINER`                 | Force remove running container                   |                                         |
| `docker container prune`                 | Remove all stopped containers                    |                                         |

## Images
| Command                                  | Description                                      | Example / Note                          |
|------------------------------------------|--------------------------------------------------|-----------------------------------------|
| `docker pull IMAGE`                      | Download image from registry                     |                                         |
| `docker build -t NAME .`                 | Build image from Dockerfile in current dir       |                                         |
| `docker build -f FILE -t NAME .`         | Build using custom Dockerfile                    |                                         |
| `docker images`                          | List local images                                |                                         |
| `docker rmi IMAGE`                       | Remove image                                     |                                         |
| `docker rmi -f IMAGE`                    | Force remove image                               |                                         |
| `docker image prune`                     | Remove dangling (unused) images                  |                                         |
| `docker image prune -a`                  | Remove all unused images                         |                                         |
| `docker save IMAGE -o file.tar`          | Export image to tar file                         |                                         |
| `docker load -i file.tar`                | Import image from tar file                       |                                         |

## Volumes
| Command                                  | Description                                      |
|------------------------------------------|--------------------------------------------------|
| `docker volume create NAME`              | Create a named volume                            |
| `docker volume ls`                       | List volumes                                     |
| `docker volume inspect NAME`             | Show detailed info                               |
| `docker volume rm NAME`                  | Remove volume                                    |
| `docker volume prune`                    | Remove all unused volumes                        |

## Networks
| Command                                  | Description                                      |
|------------------------------------------|--------------------------------------------------|
| `docker network ls`                      | List networks                                    |
| `docker network create NAME`             | Create a custom network                          |
| `docker network inspect NAME`            | Show network details                             |
| `docker network rm NAME`                 | Remove network                                   |
| `docker network prune`                   | Remove all unused networks                       |

## System
| Command                                  | Description                                      |
|------------------------------------------|--------------------------------------------------|
| `docker info`                            | System-wide information                          |
| `docker version`                         | Show Docker version                              |
| `docker stats`                           | Live resource usage of containers                |
| `docker top CONTAINER`                   | Show running processes in container              |
| `docker history IMAGE`                   | Show image layer history                         |
| `docker system df`                       | Disk usage                                       |
| `docker system prune`                    | Remove unused objects (networks, images, etc.)  |
| `docker system prune -a`                 | Remove ALL unused objects (be careful!)          |

## Docker Compose (Bonus)
| Command                                  | Description                                      |
|------------------------------------------|--------------------------------------------------|
| `docker compose up`                      | Build (if needed) and start services             |
| `docker compose up -d`                   | Start in background                              |
| `docker compose down`                    | Stop and remove containers + networks            |
| `docker compose logs`                    | Show logs                                        |
| `docker compose logs -f`                 | Follow logs                                      |
| `docker compose ps`                      | List running services                            |
| `docker compose build`                   | Build or rebuild images                          |
| `docker compose pull`                    | Pull latest images                               |
| `docker compose restart`                 | Restart all services                             |

Happy Dockering! 🚀
