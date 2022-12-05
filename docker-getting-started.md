# Docker tutorial

A Docker image is a private file system just for your container. It provides all the files and code your container needs to run.

`docker build -t docker101tutorial .`

After you build your image, you can start a container. Running a container launches the application with its private resources, isolated from the rest of your machine.

`docker run -d -p 80:80 --name docker-tutorial docker101tutorial`

You can save your image to Docker Hub and then share it with other people to be used on any other machine.

`docker tag docker101tutorial [hub repo]`


# Running the container: flags in the command

`docker run -d -p 80:80 --name docker-tutorial docker101tutorial`

`-d` runs the container in detached mode (in the background)
`-p 80:80` maps port 80 of the host to port 80 in the container
`docker101tutorial` the image to use

The purpose of a container is to run a thing that does one single thing

If a thing has no reason to keep going, it kills itself. This is why you might see a container fuckin run and then exit right away

`docker run -it node:18 bash`

`docker run -it debian`
runs an interactive debian container

Containers are ephemeral -- if you save a file into your container and then you exit that container, you're not meant to get back to that saved state. If you run that container again, all you will have is the configuration to run some shit, not the actual stuff you 'did' on that mini computer. A container is not designed to persist state over time.

Setting a volume means allocating space on your computer ouside of docker to work as a file system so you can persist data outside of teh container's normal lifecycle

`docker-compose up -d`
brings up all of the docker containers define in the docker-compose.yml file
-d says to do it detached, in the background

`docker-compose ps`
lists the running containers

`docker logs --follow`
gets the logs from a running container

`docker exec -it [container name] bash`
exec executes a command in a container that already exists (different from run which launches a container)

docker-compose.yml lets you compose multiple containers on your local machine that can all communicate with each other. it's not a production tool, just for local dev.

If you ever need to run a container that's crashing, you can do a hacky thing where you run it with command sleep and 100000 or something, and then bash into it from another container to read logs and diagnose