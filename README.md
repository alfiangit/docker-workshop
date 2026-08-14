# docker-workshop
workshop code spaces

## Docker 101 - Realization [Resource](https://github.com/DataTalksClub/data-engineering-zoomcamp/blob/main/01-docker-terraform/docker-sql/01-introduction.md)
- `docker run {image}` ALWAYS creates a brand new container. If it's your first time using that image, Docker will automatically download (fetch) it first.
- `docker ps` shows currently running containers. `docker ps -a` shows ALL containers (both running and stopped).
- To clean up unused containers, use `docker rm {container_id}`. (Note: The container must be stopped first, or you can force it with `docker rm -f {container_id}`).
- The `-it` flags start the container in **interactive mode**, which brings you inside the container's command line. To exit and stop the container, press `Ctrl + D` (or type `exit`). 
- **The magic of official images:** You don't need to download a full OS like Ubuntu, run updates, and install Python manually. Images like `python:3.13.11-slim` already have a minimal OS (Debian Linux) and Python pre-installed. It skips the redundant setup steps and gives you exactly what you need out of the box.
