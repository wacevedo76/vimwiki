[[../Docker.wiki|Back]]
--------------------------------------------------------------------------------
= Docker Notes =
--------------------------------------------------------------------------------
== Basic commmands ==
  list running containers    | docker ps
                             |
  list all containers        | docker ps -a
                             |
Docker Run - User to create and run container
  Start a container          | docker run <image name>
  (runs in attached mode)    |   (if image is not on system, it will be downloaded)
                             |
  Start a container          | docker run --name <given name> <image name>
  assigning name             |
                             |
  Starts a container /       | docker run <image name> command
  override default command   |
                             |
  run a docker tag to run    | docker run:<tag>
  a specific version of a    | docker run redis:4.0
  docker container           |
                             |
  map standared input to     | docker run -i <container>/<app>
  docker container           |
  (interactive mode)         |
                             |
  Allocate (attach) sudo     | docker run -it <container>/<app>
  terminal to container      | docker run -it alpine sh
                             |
  run a docker container     | docker start -ai <container id>
                             | -a   attach stnd i/o and forward signals to the container
                             | -i   attach the containers input
                             |
  stop a container           | docker stop <container name / id>
                             |   Sends a SIGTERM command
                             |
  kill a container           | docker kill <container name / id>
                             |   Sends a SIGKill command
                             |
  remove a container         | docker rm <name of container>
                             |
  list images on host        | docker images
                             |
  remove an image            | docker rmi <name of image>
                             |   (containers and dependent containers rom this
                             |    image must be stopped)
                             |
  Remove all containers      | docker system prune
                             |   - this will remove:
                             |     * all stopped containers
                             |     * all networks not used by at lease on container
                             |     * all dangling images
                             |     * all build cache
                             |
  pull an img w/o running    | docker pull <name of image>
                             |
  execut a command inside    | docer exec <container name> <command> <arguments>
  a running container        |
                             |
  run a second command on    | docker exec -it <container id> <command>
  an existing container      | example: docker exec -it <id of redis container> redis-cli
                             |
  start a container in the   | docker run -d container
  background (detached mode) |
                             |
  run containers with        | docer run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image id>
  mounted volumes            |   (first -v ensures that /app/node_modules is only referenced from
                             |    inside the container, the second -v then mapps the rest of the cwd
                             |    to the WORKDIR of the container
                             |
  attach to a detached       | docker attach <name or id of running container>
  container                  |
--------------------------------------------------------------------------------
== Creating Docker images / Dockerfile ==
  Basic work flow to create  | * Docker file
  a docker image             | --> Docker client
                             |   --> Docker Server
                             |     --> USABLE IMAGE!
                             |
  Create a Dockerfile        |  `------------------------`
                             | ` | Specify a base image` |
                             |  `------------------------`
                             |  `-------------------------------`
                             |  `|     Run some commands to    |`
                             |  `| install additional programs |`
                             |  `-------------------------------`
                             |  `-------------------------------`
                             |  `| Specify a command to run on |`
                             |  `|   container startup         |`
                             |  `-------------------------------`
                             |
                             |
                             |
  Generic Dockerfile         |  Generic Dockerfile
                             |  ------------------------------------------------
                             | 1 # Use an exiting docker image as a base
    --> add base image       | 2 FROM alpine
                             | 3
                             | 4 # Download and install a dependency
    --> adding packages      | 5 Run apk add --update redis
      (based on image repo)  | 6
                             | 7 # Tell the image what to do when it starts
    --> default command      | 8 CMD ["redis-server"]
                             |  ------------------------------------------------
  Command to build image     | docker build .
                             |
  Tagging an image           | docker build -t <dockerID>/<repo>:<version> <build dir>
  (giving image a name)      | docker build -t wacevedo76/redis:latest .
                             |   - technically, the version number (..:<version>) is the tag
                             |   (when modifying the Dockerfile, if you use the
                             |   same tag - it overrights the previous image
                             |
  Specify a working directory| WORKDIR /usr/app --> all folowing directives
                             | Will be relative to WORKDIR
                             |
  Copying Files from project | COPY (file relative to build context) (path inside container)
  Directory to container     | COPY ./ ./
                             |
  *** NOTE ***               | the order in which your arrange the commands matter.
                             | The build process will only execute changes from
                             | the step where it sees changes
                             | For exmaple
                             | if you COPY comes before a RUN directive,
                             | if the files change in the COPY stage, it will
                             | rerun all commands afterwards... In the context
                             | of a nodejs app, if files change in the COPY stage
                             | then it will rerun the following RUN command
                             | (namely, reinstalling all the dependencies in
                             | RUN npm install)  ... you can mitigate this by
                             | having multiple COPY stages:
                             |   COPY ./package.json .  <-- npm needs this to install dependencies
                             |   RUN npm install <--- will only run in new dependencies are added
                             |   COPY . . now it will only update the files that have changed
                             |        and not reinstall dependencies
                             |
  Create an image from a     | docker commit -c <default_Command> <container id>
  container                  | docker commit -c 'CMD ["redis-server"]' 8a3855
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
== Port Mapping ==
  * the docker host in given an Ip address
  * the docker container may have been given and internal Ip address relative to
    it's host container (Internal IP)
  ` -------------------------------------------`
  ` |              | 80 |                     |`
  ` |              ------                     |`
  ` |                 |                       |`
  ` |        _________|                       |`
  ` |        |                                |`
  ` ||--------------------|                   |`
  ` ||  | 5000 |          |  Docker Host      |`
  ` ||  --------          |  IP: 192.168.1.5  |`
  ` ||                    |                   |`
  ` ||  IP: 172.17.0.2    |                   |`
  ` ||                    |                   |`
  ` ||  Web APP           |                   |`
  ` || (Docker container) |                   |`
  ` ||--------------------|                   |`
  ` |-----------------------------------------|`

--------------------------------------------------------------------------------
  Port mapping               | docker run -p <host-port:container-port> <contaner/app>
  (forward traffic to a port | docker run -p 80:5000 <container>/<app>
   of from the container to  |   (now the app can be accessed on 192.168.1.5:80
   the Docker Host)          |
                             |
--------------------------------------------------------------------------------

  `----------------------------------------------------------------------|`
  `|              | 80 |                 | 8000 |        | 8001 |        |`
  `|              ------                 --------        --------        |`
  `|                 |       IP: 192.168.1.5   |               |         |`
  `|        _________|                         |               |         |`
  `|        |                                  |               |         |`
  `||--------------------|  |--------------------| |--------------------||`
  `||  | 5000 |          |  |  | 5000 |          | |  | 5000 |          ||`
  `||  --------          |  |  --------          | |  --------          ||`
  `||                    |  |                    | |                    ||`
  `||  IP: 172.17.0.2    |  |  IP: 172.17.0.3    | |  IP: 172.17.0.4    ||`
  `||                    |  |                    | |                    ||`
  `||  Web APP           |  |  Web APP           | |  Web APP           ||`
  `|| (Docker container) |  | (Docker container) | | (Docker container) ||`
  `||--------------------|  |--------------------| |--------------------||`
  `|                                                                     |`
  `||--------------------| |--------------------|                        |`
  `||  | 3306 |          | |  | 3306 |          |                        |`
  `||  --------          | |  --------          |                        |`
  `||                    | |                    |      Docker Host       |`
  `||  IP: 172.17.0.2    | |  IP: 172.17.0.2    |      IP: 192.168.1.5   |`
  `||                    | |                    |                        |`
  `||  MySQL             | |  MySQL             |                        |`
  `|| (Docker container) | | (Docker container) |                        |`
  `||--------------------| |--------------------|                        |`
  `|    |                      |                                         |`
  `| --------               -------                                      |`
  `| | 3306 |               | 8306|                                      |`
  `|---------------------------------------------------------------------|`

--------------------------------------------------------------------------------
  multiple instances of a    | docker run -p 80:5000 <container>/Webapp
  container within a host    | docker run -p 8000:5000 <container>/Webapp
  can be mapped to different | docker run -p 8001:5000 <container>/Webapp
  ports                      | docker run -p 3306:3306 mysql
                             | docker run -p 8306:3306 mysql
--------------------------------------------------------------------------------
== Specify a Working Directory ==
                             |
                             |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
== Volume mapping ==
  Once a container is stopped| `|--------------------|`
  all data changes within    | `|                    |`
  the container are lost     | `|  DATA              |       |--------------|`
  to persist the changes, a  | `|  /var/lib/mysql <--|-------| /opt/datadir` |
  volume can be mapped to the| `|                    |       |--------------|`
  file structur of the       | `|  MySQL             |`
  container from outside the | `| (Docker container) |`
  container                  | `|--------------------|`
                             |
  volume mapping             | docker run -v /opt/datadir:/var/lib/mysql mysql
                             |
  inspect a container        | docker inspect blissful_hopper
  (returns all the details   |
  of a container in json)    |
                             |
  view the logs of a detached| docker logs <container id>
  container                  |
--------------------------------------------------------------------------------
== Docker compose ==
  What is Docker Compose     | * Separate CLI that gets installed along with docker
                             | * used to start up multile Docker containers
                             |   at the same time
                             | * Automates some of the long-winded argumets we
                             |   were passing to 'docker run'
                             |
  docker-compose file        | docker-compose.yml
                             |
          Docker compose file abstraction

                Docker-compose.yml
          -----------------------------------------------
          `| Here are the containers I want to create:   |`
          `----------------------------------------------|`
          `|      |redis-server                          |`
          `|       --------------------------------------|`
          `|           | Make it using the 'redis' image |`
          `|      ---------------------------------------|`
          `|      |node-app                              |`
          `|      ---------------------------------------|`
          `|           |Make it using the Dockerfile in  |`
          `|           |the current directory            |`
          `|           ----------------------------------|`
          `|           |Map port 8081 to 8081            |`
          `-----------------------------------------------`

                    Example file

            `|  version: '3'              |`
            `|  services:                 |`
            `|    redis-server:           |`
            `|      image: 'redis'        |`
            `|    node-app:               |`
            `|      restart: on-failure   |`
            `|      build: .              |`
            `|      ports:                |`
            `|        - "4001:8081"       |`

  Syntax keywords            |
    version                  | the version of docker-compose which is being used
    services                 | the type of container being used
    restart                  | within each service, you can specify a restart policy
                             | there are 4 options
                             |  * "no" (yaml files recognize no as a boolean value and "no" as a string value)
                             |  * always
                             |  * on-failure
                             |  * unless-stopped
                             |
  **NOTE**                   | when multiple containers are spun up with docker
                             | compose, these containers are able to communitcte
                             | amongst one another freely; no explicit network
                             | connection need to be established between them
                             |
                             | the names of the containers which are defined
                             | in the docker-compose.yml file are automatically
                             | set as the container's host name, which facilitates
                             | the network connections between containers; Containers
                             | are referenced by their hostnames
                             |
                             | a port number may also be assigned
                             |
  Create an instance of all  | * docker-compose up
  the containers defined in  |   (synonymous with docker run)
  a docker-compose file      |
                             |
  rebuild and docker-compose | * docker-compose up --build
                             |   (synonymous with docker build, then docker run)
                             |
  Launch docker compose      | docker-compose up -d
  in background              |
                             |
  Stop containers            | docker-compose down
                             |
Docker Volumes
                             |
[[../Docker.wiki|Back]]
