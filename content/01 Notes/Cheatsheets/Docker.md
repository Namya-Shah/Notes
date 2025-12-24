# What is container?

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.
![[CleanShot_2024-11-17_at_18.49.442x.png]]
![[CleanShot_2024-11-17_at_18.49.592x.png]]
> [!important]
> Virtual machines virtualize *hardware*, they emulate what a physical computer does at a very low level. Containers virtualize at the *operating system* level.

# Docker Commands
## Basic command to run docker image
```Docker
docker run hello-world
```
- `run` -> Run an image to create a container
- `hello-world` -> Image name
## Removing docker image from the id of the image
```Docker
docker rm image-id
```
- `rm` -> To remove image
- `image-id` -> Assigned after pulling from server
## Removing docker image from the name of the image
```Docker
docker rmi image-name
```
- `rmi` -> Same as rm but we need to include image name we want to remove
- `image-name` -> Write the name of the image file
## Containers activity
```Docker
docker ps -a
```
- `ps` -> Active containers
- `-a` -> Shows all containers that are running or have been stopped
## Forwarding calls to another port
```Docker
docker run -d -p 8080:80 nginx
```
- `8080:80` -> Forwarding all the calls from 80 to 8080
- Port 80 is default for nginx
## Commit docker images to make it shareable
```Docker
docker commit -m "commit message" container-number image-name
```
- Committing docker images to make it shareable
- `image-name` -> it should be the one that you want to name it for sharing
- `container-number` -> it should be the one that you want to commit
## Returning only image id from docker images
```Docker
docker images -q
```
- Returns only the `image-id`
## Removing all docker images at once
```Docker
docker rmi $(docker images -q)
```
- Removing all the images at once
- It will not remove images that are running
## Giving container names
```Docker
docker run -d -p 6001:6379 --name redis-older redis:4.0
```
- The above code will name the container `redis-older` which is written after the parameter `--name`
## Returning docker network lists
```Docker
docker network ls
```
# DOCKERFILE Structure
```Docker
FROM node 
ENV MONGO_DB_USERNAME=admin \ 
MONGO_DB_PASSWORD=password 
RUN mkdir -p /home/app 
COPY . /home/app 
CMD ["node", "server.js"]
```
- `ENV` part is optional. It is better if we write it externally in a Docker Compose file rather than in the Dockerfile.
	- Set `MONGO_DB_USERNAME=admin` and `MONGO_DB_PASSWORD=password`
- `RUN` command runs the command in a terminal
	- Creates /home/app folder
- `COPY` command copies the files from host machine to container
	- Copy current folder files to /home/app
- `CMD` command runs the parameters in the terminal
	- Start the app with: `node server.js`
# Difference between Image and Container
- **CONTAINER** is a running environment for **IMAGE**
- Container is port binded which talks to application running inside container
- Container has **virtual** file system
# Container Port vs Host Port
- Multiple containers can run on your host machine
- Your laptop has only certain ports available
- Conflict when same port on host machine
# Working of Docker in Real Life
![[snapshot.jpg]]
# Docker Network
- Docker creates its isolated docker network
- When we deploy two containers in the same docker network, they can talk to each other using just the container name without [localhost](http://localhost) or port number etc.
- Application that is running outside Docker is going to connect to them from outside or from the host using [localhost](http://localhost) and the port.
# Steps for creating Docker Network
*This is an example for using mongo db and mongo express*
```Docker
docker network create mongo-network
```
- This create a docker network called `mongo-network`
```Docker
docker run -p 27017:27017 -d -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo
```
- This docker command runs on the default port (which is same as forwarding port).
- `MONGO_INITDB_ROOT_USERNAME` is the username given for the mongo database which is being created and will change the defaults.
- `MONGO_INITIDB_ROOT_PASSWORD` is the password given for the mongo database which is being created and will change the defaults.
- `--name` is passed to name the container
- `--net` is passed to tell docker to run on which network
- `mongo` shows the image name to run
```Docker
docker run -d \\n-p 8081:8081 \\n-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \\n-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \\n--net mongo-network \\n--name mongo-express \\n-e ME_CONFIG_MONGODB_SERVER=mongodb \\nmongo-express
```
- The default port for mongo-express is 8081.
- `ME_CONFIG_MONGODB_ADMINUSERNAME` is the same username that is passed in the before command
- `ME_CONFIG_MONGODB_ADMINPASSWORD` is the same password that is passed in the before command
- `ME_CONFIG_MONGODB_SERVER` is parameter which has value of `--name` from the previous command
# Docker Compose
## Why Docker Compose?
- An application broken down into multiple micro services.
- They must be deployed and run together
- The services need to communicate
## Without Docker Compose
![[CleanShot_2024-11-25_at_12.56.472x.png]]
**Docker Network ->** Allows containers to communicate with each other and with the external world

- Docker compose is a structured document to contain very normal common documents.
- It will be easier for us to edit the file at any later part of the stage
- We don’t need to create docker network that we created in terminal. Docker Compose takes care of creating a common network.
## Docker Compose YAML File Structure
- The below yaml code only executes the mongodb and mongo-express image and not the code.
```yaml
version: '3' 
services: 
	mongodb: 
		image: mongo 
		ports: 
			- 27017:27017 
		environment: 
			- MONGO_INITDB_ROOT_USERNAME=admin 
			- MONGO_INITDB_ROOT_PASSWORD=password 
	mongo-express: 
		image: mongo-express 
		ports: 
			- 8081:8081 
		environment: 
			- ME_CONFIG_MONGODB_ADMINUSERNAME=admin
```
- For pulling image from private repository, the code will look like
```yaml
version: '3' 
services: 
	my-app: 
		image: custom-repository/image-name:tag 
		ports: 
			- 3000:3000 
	mongodb: 
		image: mongo
		ports: 
			- 27017:27017 
		environment: 
			- MONGO_INITDB_ROOT_USERNAME=admin 
			- MONGO_INITDB_ROOT_PASSWORD=password 
	mongo-express: 
		image: mongo-express 
		ports: 
			- 8081:8081 
		environment: 
			- ME_CONFIG_MONGODB_ADMINUSERNAME=admin 
			- ME_CONFIG_MONGODB_ADMINPASSWORD=password 
			- ME_CONFIG_MONGODB_SERVER=mongodb
```
## To start the docker compose file
```Docker
docker-compose -f mongo-docker-compose.yaml up
```
## To stop the docker compose file
```Docker
docker-compose -f mongo-docker-compose.yaml down
```
# Docker Volumes
- They are used for data persistence
    - Useful for databases and other stateful applications
- In a container, if we remove or restart the container, **the data is gone!**
- ![[CleanShot_2024-11-29_at_12.29.402x.png]]
- Data gets automatically replicated in the host machine from the container
- Changes made in the host file system automatically gets synchronized to the container file system
## Volume Types
### Host Volumes
```Docker
docker run -v /home/mount/data:/var/lib/mysql/data
```
- We decide where on the host file system the reference is made.
### Anonymous Volumes
```Docker
docker run -v /var/lib/mysql/data
```
- We just reference the container directory and not the host directory
- For each container a folder is generated that gets mounted
- **It is automatically created by Docker!!!**
### Named Volumes
```Docker
docker run -v name:/var/lib/mysql/data
```
- Name is the reference of the directory present in the host machine and then we write container directory path
- ***Should be used in production***
## Docker Volumes in Docker-Compose file
```Docker
version:'3' 
services: 
	mongodb: 
		image: mongo 
		ports: 
			- 27017:27017
		volumes: 
			- db-data:/var/lib/mysql/data 
	mongo-express: 
		image: mongo-express 
		... 
volumes: 
	db-data
```
## Docker Volume Locations
### Windows
`C:\ProgramData\docker\volumnes`
### Linux
`/var/lib/docker/volumes`
### MacOS
`/var/lib/docker/volumes`
# BEST PRACTICES
1. Use official docker images as base image
	- ![[CleanShot_2024-11-24_at_14.20.052x.png]]
2. Use specific docker image versions
	- ![[CleanShot_2024-11-24_at_14.21.182x.png]]
3. Use small-sized official images
	- ![[CleanShot_2024-11-24_at_14.23.022x.png]]
	- ![[CleanShot_2024-11-24_at_14.26.05.png]]
	- ![[CleanShot_2024-11-24_at_14.26.42.png]]
	- Use **alpine linux** wherever you don't require **full blown OS**.
		- Lightweight Linux distro
		- Security oriented
		- Popular base image
	- **If you don't require any specific utilities, choose leaner and small image**
4. Optimize caching image layers
	- In dockerfile, each command creates an image layer
	```Docker
	FROM node:17.0.1-alpine
	WORKDIR /app
	COPY myapp /app
	RUN npm install --production
	CMD ["node", "src/index.js"]
	```
	- **ADVANTAGES**
		- Faster image building
		- Downloading only added layers and doesn't download already downloaded layers
	- Once you make some changes in any project file. Everything including that commands gets re-executed.
	- Other Dockerfile commands from least to most frequently changing
	- ![[CleanShot_2024-11-24_at_14.36.56.png]]

5. Use `.dockerignore` file
	- **Advantages**
		- Reduce image size
		- Prevent unintended secrets exposure
	- **Steps**
		- Create `.dockerignore` file in the root directory
		- List files and folders you want to ignore
		- Matching is done using Go's *filepath*. Match rules
6. Make use of multi-stage builds
	- ![[CleanShot_2024-11-24_at_14.42.47.png]]
	- You can name your stages with `AS <name>`
	- Each `FROM` instruction starts a new build stage
	- You can selectively copy artifacts from one stage to another
> [!important]
> **Only the last Dockerfile commands are the image layers.**
8. Use the least privileged user
	- **Disadvantages if you use root user**
		- If the dockerfile is not provided with user, it uses root user by default
	    - Container could potentially have root access on the Docker host
	    - Easier privilege escalation for an attacker
    - **Solution**
	    - Create a dedicated user and group
	    - ![[CleanShot_2024-11-24_at_14.50.39.png]]
	    - Don’t forget to set required permissions
	    - Change to non-root user with `USER` directive.
> [!important]
> Some base images have a generic user bundled in
8. Scan your images for security vulnerabilities
	- Use this command in **CLI**
    - `docker scan myapp:1.0`
	- Docker uses Snyk service for the vulnerability scan
	- Scan using **Docker Hub**
	- **Integrate in CI/CD**
# Using Docker in unusual ways
1. As a time machine
    - It can be used to revert back to older version if needed
2. Running Legacy Code
    - We can run code that has programming language version which is old by hosting it on docker and making it available to other users.
3. Hosting a Local Stack
    - We can host a stack we want to use and then rebuild the image
    - If we don’t want to manually rebuild the image, we can use docker `watch` command for auto-rebuild
4. Integration Testing
    - We can use [testcontainers.com](http://testcontainers.com) to create containers to test our stack
    - It will start the container and run the stack and check for flaws. If no flaws found, it will just end the container and remove it
5. Improving Application Security
    - `docker scout` is useful for scanning the local images created or downloaded. It also scan local file systems.
    - It is useful for optimizing images.
    - We can know the vulnerabilities in our code stack and fix them accordingly.