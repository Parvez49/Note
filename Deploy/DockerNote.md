

```
https://dev.to/thedevtimeline/add-mongodb-and-postgresql-in-django-using-docker-55j6
https://dev.to/karanpratapsingh/dockerize-your-react-app-4j2e
https://medium.com/@audretschjames/understanding-docker-as-if-it-were-a-gameboy-96c96392efbf
```

# Docker:
     Docker Image: Like Class.
     
     Docker Container: Like Object of Class.
     
     Docker Daemon: is a persistent background process that manages Docker containers. It listens for Docker API requests and handles container lifecycle management, such as building, running, stopping, and removing containers.  The daemon is responsible for orchestrating the entire containerization process, including pulling container images from registries, creating container instances, managing their execution, and monitoring their resource usage.
     
     Docker Swarm: Manage docker Daemon.

     Dockerfile: allows you to document the steps to set up the environment for application. The Docker Engine will parse Dockerfile, and create a Docker Image from it.
     
     Mount: Mounting the host system into a container allows the container to read and write to the host system. Mounting allows you to modify files on your host machine while running them in the environment of a Docker container.
     
     Docker Volumes: are like Memory Cards. 
     
     Docker-Compose: Docker Compose coordinates containers to run together.
     

```
docker-compose exec <image_name> <command>
docker-compose exec authentication python manage.py migrate

$ docker-compose down                  // stop and remove docker container
$ docker-compose stop [service-name...]   // stop without remove container
$ sudo docker rm <service name>           // remove docker container
$ sudo docker rmi <directory-service_name>   // to remove associated images with that container
```


# Docker Command:
$ docker ps             // List running docker containers
$ docker ps -a  # Lists running and stopped docker containers
$ docker images ls      // to show all images list
$ docker build -t image_name // to build image



$ docker ps                                  // List running docker containers   
$ docker start aa1463167766                  // 'aa1463167766' is container id
$ docker exec -it aa1463167766 /bin/bash 
$ docker stop aa1463167766 
$ docker rm aa1463167766 



$ docker run -d -p 4000:80 --name docker-container-name image_name
$ docker run -it ubuntu:14.04 /bin/bash 
$ docker run -v <HOST_DIRECTORY>:<CONTAINER_DIRECTORY>
$ docker run -it -v $(pwd):/mounted ubuntu:14.04 /bin/bash


# Docker Volume:
$ docker volume ls
$ docker-compose down -v
$ docker volume create <volume_name>
$ docker volume inspect <volume_name_or_id>    // to get detail information
$ docker volume rm <volume_name_or_id> 
$ docker volume prune                          // to remove unused volume




Docker-compose.yml
	version: which version of docker-compose to use
	services: names of containers we want to ru
	build: steps describing the build process
	context: where the Dockerfile is located at to build the image
	ports: map ports from the host machine to the container
	volumes: map the host machine or a docker volume to the container
	environment : pass environment variables to the container
	depends_on : start the listed services before starting the current service

Dockerfile
	FROM image_name — starts build by layering onto an existing image
	COPY host_path container_path — copies file or directory from host to the image
	RUN shell_command — runs a shell command in the image
	WORKDIR path — sets the current path in the image
	ENV variable value — sets the env variable equal to the value
	EXPOSE port — exposes a container port
	ENTRYPOINT ['shell', 'command'] — prefixes to CMD
	CMD ['shell', 'command'] —executes shell command at runtime




----------------------------------------------------------------

	Kubernets: open source container orchestration tool.
