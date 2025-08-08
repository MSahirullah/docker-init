# Docker

#### General Commands

##### 1.Create an docker image using the Dockerfile
    docker build -t image_name

##### 2.To see all the images
    docker images

##### 3.To create a container from that image
    docker run –name container_name image_name
    docker run –name container_name -d image_name (to run in detached mode)


##### 4.To see all the running services(containers)
    docker ps

##### 5.To see all the containers (running ones or not)
    docker ps -a

##### 6.To stop a running container
    docker stop container_name
    //or
    docker stop container_id

##### 7.To restart a docker container
    Docker start container_name
    //(here we don't need to re configure the port mappings as we did that earlier)

##### 8.Remove a docker container
    docker ps -a
    docker container rm CONTAINER_ID_OR_NAME

    Remove multiple containers
    docker container rm CONTAINER_ID_OR_NAME CONTAINER_ID_OR_NAME

##### 9.Remove a docker image
    docker images
    docker image rm IMAGE_ID_OR_TAG

##### 10.Remove all containers all images and all volumes
    docker system prune -a


### Docker Volumes
1. **Anonymous Volumes:** Created and managed by Docker but not given a specific name. These volumes are typically used for temporary data that doesn't need to be persisted beyond the container's lifecycle.
    ```
    docker run -d --name my_container -v /app/data my_image
    ```

2. Named Volumes: Created with a specific name and can be referenced by multiple containers. Named volumes are useful for persisting data that needs to be shared between containers or across container restarts.
    ```
    docker run -d --name my_container -v my_volume:/app/data my_image
    ```

3. Host Volumes (Bind Mounts): Directly map a directory or file on the host to a directory or file in the container. Unlike managed volumes, the host determines where the data is stored. Bind mounts provide more control but less isolation from the host system.
    ```
    docker run -d --name my_container -v /path/on/host:/path/in/container my_image
    ```

#### Docker Commands
##### 1.Create a docker volume
    docker volume create my_volume

##### 2.Run a docker container with a volume
    docker run -d --name my_container -v my_volume:/app/data my_image

    //docker run --name container_name --rm -v /app/node_modules -v ${PWD}:/app  image_name
    //--rm - when you stop the container, container will removed

###### 3.List all docker volumes
    docker volume ls

##### 4.Inspect docker volumes
    docker volume inspect my_volume

##### 5.Remove
    docker volume rm my_volume
