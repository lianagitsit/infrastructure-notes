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