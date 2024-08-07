# A Cloud Guru - Docker Deep Dive =
## Installation and Configuration (Centos)
### Remove previous installs  
```dockerfile
yum remove -y docker docker-client docker-client-latest \
              docker-common docke-latest docker-latest-logrotate \
              docker-logrotate docker-engine
```
                             
### Dependencies
  `yum install -y yum-utils device-mapper-persistent-data lvm2`
### Add docker repo
  `yum-config-manager --add-repo https://download.docker.com/linux/centos/docer-ce.repo`
### Install
  `yum install docker-ce`
                           
### Enable and start Docker
  `system-ctl enable --now docker`
                           
### Test Docker installation
  `docker run hello-world`
                           
### Add docker group to user
  `usermod -aG docker {user} (prevents having to sudo)`
  
                           
### Script installation
  `wget -qO- https://get.docker.com | sh`

## Docker Architecture
### Architecture Overview       
#### Client-server architecture                                              
   * The client talks to the Docker daemon                                   
   * The Docker daemon handles:                                              
     * Building                                                              
     * Running                                                               
     * Distributing                                                          
   * Both communicate using a REST API:                                      
     * UNIX sockets                                                          
     * Network interface                                                     
                                                                             
#### The Docker daemon (dockerd)  
   * Listens for Docker API request and manages Docker objects:            
     * Images                                                              
     * Containers                                                          
     * Networks                                                            
     * Volumes                                                             
                                                                             
#### The Docker Client (docker)  
   * Is how users interact with Docker                                     
   * The client sends these commands to dockerd                            
                                                                             
#### Docker registries:                                                        
   * Stores Docker images                                                  
   * Public registry such as DockerHub                                     
   * Run your own private registry                                         
                                                                             
#### Docker objects:                                                           
   * *images*                                                              
     * Read-only template with instructions for creating a Docker container
     * Image is based on another image                                     
     * Create your own images                                              
     * Use a Dockerfile to build images                                    
   * *Containers*                                                          
     * Runnable instance of an image                                       
     * Connect a container to networks                                     
     * Attach storage                                                      
     * Create a new image based on its current state                       
     * Isolated from other containers and the host machine                 
   * *Services*:                                                           
     * Scale containers across multiple Docker daemons                     
     * Docker Swarm                                                        
     * Define the desired state                                            
     * Service is load-balanced                                            
   * *Docker Swarm*:                                                       
     * Multiple Docker daemon (Master and Worker)                          
     * The daemons all communicate using the Docker API                    
     * Supported in Docker 1.2 and higher                                  

### Docker Engine  
#### Under the hood  
   * *Docker Engine*:
     * Modular in design:
       * Batteries included but replaceable                                 
     * Based on an open-standards outline by the *Open Container Initiative*
  
     * The major components:  
       * Docker client  
       * Docker daemon  
       * containerd  
       * runc  
     * All of these together help build images  
  
### A Breif History of the       
#### Docker Enging              
   * *The first release of Docker*:                                                                  
     * *The Docker daemon*                                                                         
       * Docker client                                                                             
       * Docker daemon                                                                             
       * Monolithic binary                                                                         
       * Docker API                                                                                
       * Container runtime                                                                         
       * Image builds                                                                              
       * Much more...                                                                              
     * *LXC*                                                                                       
       * Namespaces                                                                                
       * Control groups (cgroups)                                                                  
       * Linux-specific                                                                            
                                                                                                   
   * *LXC was later replace with libcontainer*:
     * Harder to innovate                                                                          
     * Slow                                                                                        
     * Now what the ecosystem wanted                                                               
                                                                                                   
   * *Docker became more modular*:                                                                   
     * Smaller more specialized tools                                                              
     * Pluggable architecture                                                                      
                                                                                                   
   * *Open Container initiative*:                                                                    
     * Image spec                                                                                  
     * Container runtime spec                                                                      
     * version 1.0 releaseed in 2017                                                               
     * Docker, Inc. heavily contributed                                                            
     * Docker 1.11 (2016) used the specification as                                                
       much as posible                                                                             
   * *runc*                                                                                          
     * Implementation of the OCI container-runtime-spec                                            
     * Lightweight CLI wrapper for libcontainer                                                    
     * Create containers                                                                           
                                                                                                   
   * *containerd*:                                                                                   
     * Manage container lifecycle:                                                                 
       * Start                                                                                     
       * Stop                                                                                      
       * Pause                                                                                     
       * Delete                                                                                    
     * Image management                                                                            
                                                                                                   
     * Part of the 1.11 release                                                                    
                                                                                                   
   * *shim*                                                                                          
     * Implementation of daemonless Containers                                                     
     * *containerd* forks an instance of *runc* for each new container                             
     * *runc* process exits after the container is created                                         
     * *shim* process becomes the container parent                                                 
     * Responsible for:                                                                            
       * STDIN and STDOUT                                
       * Reporting exit status to the Docker daemon                     
### Running Containers
  * `docker container run -it --name <NAME> <IMAGE>:<TAG>`
  
  * Creating a container:
    * Use the CLI to execute a command
    * Docker client uses the appropriate API payload
    * POSTs to the correct API endpoint
    * The Docker daemon receives instructions
    * The Docker daemon calls *containerd* to start a new container
    * the Docker daemon uses *gRPC* (a CRUD style API)
    * *cntainerd* creates an OCI bundle from the Docker image
    * Tells *runc* to create a container using the OCI bundle
    * *runc* interfaces with the OS kernal to get the constructs needed to create a container
    * this include namespaces, *cgroups*, etc
    * The container process is started as a child process
    * Which completes the process and the container is now running

### Docker Images and Containers ==
#### What are Docker Images?  
   * Docker images:                                                              
     * Use images to create an instance of a container                         
     * Comprised of multiple layers                                            
     * Build time constructs                                                   
     * Built from the instructions                                             
                             
### Docker Images and Layers  
  * Images are made of multiple layers                                      
  * Each layer represents an instruction in the image's Dockerfile                                        
  * Each layer, except the very last one, is read-only                                                    
  * Eacy layer is only a set of differences from the layer before it                                      
  * Containers add a new writable layer on top of the underlying layers                                   
  * All changes made to a running container are made to the Container layer                               
                             
### Container and Layers      
  * Top writable layer                                          
  * All changes are stored n the writable layer                                               
  * The writable layer is deleted when the container is deleted                               
  * the image remains unchanged                                                               
                             
### Docker Commands  
#### Docker Commands  
  **Management Commands**  
  * ***builder***: Manage Builds                                             
  * ***config***: Manage Docker configs                                     
  * ***container***: Manage containers                                      
  * ***engine***: Manage the docker engine                                  
  * ***image***: Manage images                                              
  * ***network***: Manage networks                                          
  * ***node***: Manage Swarm nodes                                          
  * ***plugin***: Manages plugins                                           
  * ***secret***: Manage Docker secrets                                     
  * ***service***: Manage services                                          
  * ***stack***: Manage Docker stacks                                       
  * ***swarm***: Manage Swarm                                               
  * ***system***: Manage Docker                                             
  * ***trust***: Manage trust on Docker images                              
  * ***volume***: Manages volumes                                           
                             
#### docker image
  **docker image commands** 
  * ***ls***: List images
  * ***pull***: Pull an image or a repo from a registry
  * ***push***: Push an image or a repo to a registry
  * ***inspect***: return low-level information on Docker object
  * ***import***: import the contents from a tarboo to create a filesystem image
                             
#### docker container**
  * **ls**: list containers  
  * ***run***: Run a command in a new container
  * ***inspect***: Display detailed information on one or
    more containers
  * ***top***: Display the running processes of a container
  * ***restart***: Restart one or more containers
  * ***Attch***: Attach local standard input, output, and
    error streams to a running container
                             
#### run a command within a docker container
  * `docker container exec -it <contaner id> <command>`
  * `docker container exec -it f8d9c /bin/bash`
                             
## Creating Containers  
### Creating Containers        
#### Command: docker container commands
                                                                                                    
   * *run*: Run a command in a new container  
          Example: `docker container run busybox`
                                                                                                     
   **Flags**  
   * **--help**: Print usage  
   * **--rm**: Automatically remove the container when it exists  
   * **-d, --detach**: Run container in the backgroud and print container ID  
   * **-i, --interactive**: Keep STDIN open even if not attached  
   * **--name string**: Assign a name to the container  
   * **-p, --publish list**: Publish a container's port(s) to the host  
   * **-t, --tty**: Allocate a pseudo-TTY  
   * **-v, --volume list**: Bind mount  a volume  
   * **--mount, mount**: Attach a filesystem mount to the container  
   * **--network string**: Connect a container to a network (default "default")  
                                                                                                     
   * **Examples**                                                                                        
       `docker container run --rm busybox`  
       `docker container run -it busybox`  
       `docker container run -d busybox`  
       `docker container run -d --name myContainer busybox`  

## Explosing and Publishing Container Ports  
### Exposing and Publishing Ports   
#### Expose:                                                                                           
   * Expose a port or a range of porst                                                             
   * This does not publish the port                                                                                           
   * Use `--expose <PORT>`
   * Example                                                                                                                    
     `*docker container run --expose 1234 <IMAGE>*`
                                                                                                                               
#### Publish:                                                                                                                     
   * Maps a container's port to a host's port                                                                                 
   * **-p, --publish**: Used ot list a published container's port(s) to the host                                                
   * **-P, --publish-all**: Used to publish all exposed ports to random ports                                                   
   * Example                                                                                                                    
     * `docker container run -d --expose 3000 -p 80:3000 nginx` <br>
         (runs detached, exposes 3000 and binds internal container port (80) with host port (3000)  
     * `docker container run -d --expose 3000 -p 8081:80/tcp -p 8081:80/udp nginx`
                             
## Executing Container Commands  
### Executing Container commands 
  * Dockerfile               
  * During a Docker run                                   
  * Using the *exec* command                            
### Commands can be:
  * One and done commands
  * Long-running Commands
                             
    #### Starting a container with:
       `docker container run <IMAGE> <CMD>`
                             
    #### Executing a command on a running container
       `docker container exec -it <NAME> <CMD>`
                             
## Container Logging  
### Container Logging          
  * Show information logged by a running container:    
    `docker service logs <NAME>`
                                                     
  * Show information logged by all containers participating in a service:                                                   
    `docker services logs <SERVICE>`
                                                                                
  * Logs need to be output to *STDOUT* and *STDERR*                               
                                                                                
  * Nginx Example:                                                                
    RUN: `ln -sf /dev/stdout /var/log/nginx/access.log && ln -sf /dev/stderr /var/log/nginx/error.log`

## Networking Overview  
### Docker Networking 101      
  * Docker Networking                                 
    * Container Network Model (CNM)                 
    * The libnetwork implements CNM                 
    * Driver extend the model by network topologies  
  * Network Drivers:                                                             
    * bridge                                                                   
    * host                                                                     
    * overlay                                                                  
    * macvlan                                                                  
    * none                                                                     
    * Network plugins                                                          
                             
### Container Network Model
#### Defines three building blocks:  
   * Sandboxes
   * Endpoints
                             
## Networking Commands  
| purpose                            | Command                                           |
| --------------------------         | -------------------------------                   |
| List Networks                      | `docker network ls`                               |
| getting detailed info on a network | `docker network inspect <NAME>`                   |
| create a network                   | `docerk network create <NAME>`                    |
| Remove a network                   | `docker network rm <NAME>`                        |
| Remove all unused networks         | `docker network prune`                            |
| Add a container to a network       | `docker network connect <NETWORK> <CONTAINER>`    |
| Remove a container from a network  | `docker network disconnect <NETWORK> <CONTAINER>` |

## Networking Containers  
| Purpose                                    | Command                                                                                               |
| ------------------------------------------ | ------------------------------------------------------------------                                    |
| Create a network with a Subnet and Gateway | `docker network create --subnet <SUBNET> --gateway <GATEWAY> <NAME>`                                  |
|                                            | `docker network create --subnet <SUBNET> --gateway <GATEWAY> --ip-range=<IP_RANGE> --driver=<DRIVER>` |
| Removing a network                         | `docker network rm <NAME>`                                                                            |
                             |
  Removing a network         | docker network rm <NAME>
                             |
  Assigning an IP to a       | docker container run -name <NAME> --it --network <NETWORK> --ip <IP> <IMAGE> <CMD>
  container                  |
                             |
  Adding a container to a    | docker network connect <NETWORK> <CONTAINER>
  network                    |
                             |
--------------------------------------------------------------------------------
== Storage Overview ==
  Categories of data storage | * Non-persistent
                             |   * Data that is ephemeral
                             |   * Every container has it
                             |   * Tied to the lifecycle of the container
                             |
                             | * Persistent
                             |   * Volumes
                             |   * Volumes are decoupled from containers
                             |
  Non-persistent Data        | * By default all containers use local storage
                             | * Storage locations:
                             |   * Linux: /var/lib/docker/<STORAE-DRIVER>/
                             |   * Windows: c:\ProgramData\Docker\windowsfilter\
                             |
                             | * Storage Drivers:
                             |   * RHEL uses overlay2
                             |   * Ubuntu uses overlay2 or aufs
                             |   * Windows uses it's own
                             |
  Persistent Data Using      | Volumes
  Volumes                    |   * user a volume for persistent data
                             |     1. Create the volume
                             |     2. Create your container
                             |
                             |   * Mounted to a directory in the container
                             |   * Data is written to the volume
                             |   * Deleting a container does not delete the volume
                             |   * First-class citizens
                             |   * Uses the local driver
                             |
                             |   * Third party drivers
                             |     * Block storage
                             |     * File storage
                             |     * Object storage
                             |
                             |   * Storage locations
                             |     * Linux: /var/lib/docker/volumes
                             |     * Windows: c:\ProgramData\Docker\volumes
                             |
--------------------------------------------------------------------------------
== Volume Commands ==
  List all Docker volume     | docker volume -h
  commands                   |
                             |
  List all volumes on a host | docker volume ls
                             |
  Creating volumes           | docker volume create <NAME>
                             |
  inspecting a volume        | docker volume inspect <NAME>
                             |
  Deleting a volume          | docker volume prune
                             |
  Removing all unused        | Removing all unused volumes
  volumes                    | docker volume prune
                             |
--------------------------------------------------------------------------------
== Using Bind Mounts ==
  Using Bind Mounts          | Bind mounts have been around since the early days
                             | of Docker.
                             |
                             | They have limited functionality compared to volumes
                             |
                             | With bind mount, a file or directory on the host
                             | machines is mounted into a container.
                             |
                             | Volumes use a new directory that is created witin
                             | Docker's storage directory on the host machine,
                             | and Docker manages that directory's contents
                             |
  Using the mount flag       | docker container run -d --name <NAME> --mount type=bind,source=<SOURCE>,target=<TARGET> <IMAGE>
                             |
  Using the volume flag:     | docker container run -d --name <NAME> -v <SOURCE>:<TARGET> <IMAGE>
                             |
                             | Example
                             |   docker container run -d --name nginx-bind-mount --mount type=bind,source="$(pwd)"/target,target=/app nginx
                             |
--------------------------------------------------------------------------------
== Using Volumes for Persistent Storage ==
                             | Volumes are easier to back up or migratethan bind
                             | mounts.
                             |
                             | You can manage volumes using Docker CLI commands
                             | or the Docker API.
                             |
                             | Volumes work on both Linux and Windows containers.
                             |
                             | Volumes can be more safely shared among multipl
                             | containers.
                             |
                             | Volume drivers let you store volumes on remote
                             | hosts or cloud providers, to encrypt the contents
                             | of volumes, or to add other functionality.
                             |
                             | New volumes can have their content pre-populated
                             | by a container.
                             |
  Create a new volume for a  | docker volume create html-volume
  Nginx contaier:            |
                             |
  Using the mount flag:      | docker container run -d --name <NAME> --mount type=volume,source=<SOURCE>{,readonly}},target=<TARGET> <IMAGE>
  (can also be readonly)     |
                             |
  Creating a volume using    | docker container run -d --name <NAME> -v <VOLUME-NAME>:<TARGET> <IMAGE>
  that volume flag           |
                             |
--------------------------------------------------------------------------------
== Introduction to the Dockerfile ==
  What is a Dockerfile?      | Dockerfiles are instructions on how to build an
                             | image
                             |
                             | The file contains all commands used to start a
                             | Container:
                             |   * Docker image consists of read-only layers
                             |   * Each layer represents a Dockerfile instruction
                             |   * Layers are stacked
                             |   * Each layer is a delta of the changes from the
                             |     previous layer
                             |   * Images are built using the docker image build
                             |     command
                             |
  Dockerfile Layers          | *Dockerfile*
                             | FROM ubuntu:15.04
                             | COPY . /app
                             | RUN make /app
                             | CMD python /app/app.py
                             |
                             | *Layers*:
                             |   * *FROM* creates a layer from the ubuntu:15.04 Docker image
                             |   * *COPY* adds files from your Docker client's current directory
                             |   * *RUN* builds your application with make
                             |   * *CMD* specifies what command to run within the container
                             |
  Best Practices             | General guidelines
                             |   * Keep containers as ephemeral as possible
                             |   * Follow Principle 6 of the 12 Factor App.
                             |   * Avoid including unnecessary files.
                             |   * User *.dockerignore*
                             |   * Use multi-stage builds
                             |   * Don't install unnecessary packages
                             |   * Decouple applications
                             |   * Minimize the number of layers
                             |   * Sort multi-line arguments
                             |   * Leverage the build cache
                             |
--------------------------------------------------------------------------------
== Working with Instructions ==
  Common Instructions        |
      FROM                   | *FROM:*     Initializes a new build stage and sets
                             |           the Base Image.
                             |
      RUN                    | *RUN:*      Will execute any commands in a new layer.
                             |
      CMD                    | *CMD:*      Provides a defalt for an executing container.
                             |           There can only be *one* *CMD* instruction in
                             |           a docker file.
                             |
      LABEL                  | *LABEL:*    Adds metadate to an image.
                             |
      EXPOSE                 | *EXPOSE:*   Informs Docker tha tthe container listens
                             |           to the specified network ports at runtime
                             |
      ENV                    | *ENV:*      Sets the environment variable *<key>* to the value *<value>*
                             |
      ADD                    | *ADD:*      Copies new files, directories, or remote
                             |           file URLs from *<src>* and adds them to the
                             |           filesystem of the image at the path *<dest>*
                             |
      WORKDIR                | *WORKDIR:*  Sets the working directory for any
                             |           *RUN* *CMD* *ENTRYPOINT* *COPY* and *ADD* instructions
                             |           that follow it in the Dockerfile.
                             |
      ARG                    | *ARG:*      Defines a variable that users can pass at
                             |           build time to the builder with the docker
                             |           *build* command using the *--build-arg <varname>=<value>*
                             |           flag.
                             |
      ONBUILD                | *ONBUILD:*  Adds a trigger instructions to the image
                             |           that executes when the image is used as
                             |           the base for another build.
                             |
      HEALTHCHECK            | *HEALTHCHECK:* Tells Docker ow to test a container
                             |              to check that it is still working
                             |
      SHELL                  | *SHELL:*    Allows the default shell used for the
                             |           shell form of commands to be overridden
                             |
  Working wit Instructions   | Example Dockerfile:
                             |
                             | FROM node
                             | LABEL org.label-schema.version=v1.1
                             | RUN mkdir -p /var/node
                             | ADD src/ /var/node
                             | Run npm install
                             | Expose 3000
                             | CMD ./bin/www
                             |
  Build the weather-app      | docker image build -t
  image                      | linuxacademy/weather-app:v1
                             |
--------------------------------------------------------------------------------
== Environment Variables ==
  Environment Variables      | use the *--env* flat to pass an environment variable
                             | when building an image
                             |   *--env <KEY><VALUE>*
                             |
                             | Use the *ENV* instruction in the Dockerfile:
                             |   *ENV <KEY>=<VALUE>*
                             |   *ENV <KEY> <VALUE>*
                             |
  Dockerfile example         | *Dockerfile*
                             | FROM node
                             | LABEL org.label-schema.version=v1.1
                             | ENV NODE_ENV="development"
                             | ENV PORT 3000
                             | RUN mkdir -p /var/node
                             | ADD src/ /var/node/
                             | WORKDIR /var/node
                             | RUN npm install
                             | EXPOSE $PORT
                             | CMD ./bin/www
                             |
  Pass in ENV Variables at   | docker container run -d -name \
  command line               | weather-app2 -p 8082:3001 \
                             | --env PORT=<PORT> /
                             | --env NODE_ENV=<NODE_ENV>
                             | \linuxacademy/weather-app:v2
                             |
--------------------------------------------------------------------------------
== Build Arguments ==
  Use the --build-arg flag   | --build-arg <NAME>=<VALUE>
  when building an image:    |
                             |
  Use the *ARG* instructions   | ARG <NAME>=<DEFAULT_VALUE>
  in the Dockerfile          |
                             |
  Example Dockerfile         | Dockerfile:
                             | FROM node
                             | LABEL org.label-schema.verson=v1.1
                             | ARG SRC_DIR=/var/node
                             | RUN /kdir -p $SRC_DIR
                             | ADD src/ $SRC_DIR
                             | WORKDIR $SRC_DIR
                             | RUN npm install
                             | EXPOSE 3000
                             | CMD ./bin/www
                             |
--------------------------------------------------------------------------------
== Working with Non-privileged User ==
  Example Dockerfile using   | Dockerfile:
  non-privilaged user        | FROM centos:latest
                             | RUN useradd -ms /bin/bash cloud_user
                             | USER cloud_user
                             |   -> *NOTE:* this throws an error because *WORKDIR* was never defined
                             |
                             |
                             |
  Build the new image:       | docker image build -t centos7/nonroot:v1
                             |
  Create a container using   | docker container run -it --name test-build centos7/nonroot:v1 /bin bash
  the new image              |
    (will enter and new user)|
                             |
  enter container as root    | docker container exec -u 0 -it test-build /bin/bash
  (while container is up)    |   (user flat *-u* root user *0*)
                             |
--------------------------------------------------------------------------------
== Using the Volume Instructions ==
                             | The VOLUME instruction allows ut to go ang create
                             | a mountpoint for a specified directory. This
                             | means when you create a container using the image,
                             | it's going to automatically have a vlume attached
                             | to it.
                             |
  Example docker file        | FROM nginx:latest
                             | VOLUME ["/usr/share/nginx/html"]
                             |
  Build the new image        | docker image build -t linuxacademy/nginx:vi .
                             |
  Create a continer using    | docker container run -d --name nginx-volume linuxacademy/nginx:v1
  the new image              |
                             |
--------------------------------------------------------------------------------
== Entrypoint vs. Command ==
  *CMD*                        | *CMD* defines a default command for a container
                             |
                             | It's best used for setting a default command
                             |
                             | It can be easily overridden
                             |
                             | The main usage of *CMD* is that you use it to set
                             | a default command with the expectation that it
                             | will be overwritten
                             |
  *ENTRYPOINT*                 | *ENTRYPOINT* defines a container with a specific
                             | executable
                             |
                             | It cannot be overridden when starting the
                             | containers without using the *--entrypoint* flag
                             |
                             | Use *ENTRYPOINT* to specify an executable and *CMD*
                             | to easily set environment variables
                             |
  Example Dockerfile         | # Create an image for the weather-app
                             | FROM node
                             | LABEL org.label-schema.version=v1.1
                             | ENV NODE_ENV="production"
                             | ENV PORT 3001
                             |
                             | RUN mkdir -p /var/node
                             | ADD src/ /var/node/
                             | WORKDIR /var/node
                             | RUN npm install
                             | EXPOSE $PORT
                             | ENTRYPOINT ./bin/www
                             |
--------------------------------------------------------------------------------
== Using .dockerignore ==
                             | Create the *.dockerignore* file:
                             |   vi .dockerignore
                             |
                             | Add the following to *dockerignore*
                             | .dockerignore
                             |
                             |     `*/*.md`
                             |     `*/.git`
                             |     `src/docs/`
                             |     `*/tests/`
                             |
                             | Create and build the image:
                             |   docker image build -t linuxacademy/weather-app:v4 .
                             |
--------------------------------------------------------------------------------
== Building Images ==
  Building an image          | docker image build -t <NAME>:<TAG>
                             |
  Useful flags               | *-f, --file string*: Name of the Dockerfile
                             |
                             | *--force-rm*: Awayls remove intermediate containers
                             |
                             | *--label*: Sets metadate for an image
                             |
                             | *--rm*: Removes intermediate containers after a
                             |       successful build
                             |
                             | *--ulimit*: Ulimit options
                             |
  Building and image by      |
  piping the Dockerfile      |
  through *stdin*:             | docker image build -t <NAME>:<TAG> -<<EOF
                             | Build instructions
                             | EOF
                             |
  Three ways to build an     | * docer image build -t <NAME>:<TAG> <GIT_URL>#<REF>
  image using URL:           |
                             | * docker image build -t <NAME>:<TAG> <GIT_URL>#:<DIRECTORY>
                             |
                             | * docker image build -t <NAME>:<TAG> <GIT_URL>#<REF>:<DIRECTORY>
                             |
  Building an image from a   | docker image build -t <NAME>:<TAG> - < <FILE>.tar.gz
  zip file                   |
                             |
--------------------------------------------------------------------------------
== Using Multi-Stage Builds ==
                             | * By Default, the stages are not named
                             | * Stages are interger numbers
                             | * Starting with 0 for the first *FROM* instruction
                             | * Name the stage by adding *AS <NAME>* to the *FROM* instruction
                             | * Reference the stage name in the *COPY* instruction
                             |
  Example Dockerfile         | Dockerfile:
                             | FROM node AS build
                             | RUN mkdir -p /var/node
                             | ADD src/ /var/node/
                             | WORKDIR /var/node
                             | RUN npm install
                             |
                             | FROM node:alpine
                             | ARG VERSION=V1.1
                             | LABEL org.label-schema.version=$VERSION
                             | ENV NODE_ENV="production"
                             | COPY --from=build /var/node /var/node
                             | WORKDIR /var/node
                             | EXPOSE 3000
                             | ENTRYPOINT ["./bin/www"]
                             |
--------------------------------------------------------------------------------
== Tagging ==
                             | *-t, --tag* adds a name and an optional tag in
                             | the *name:tag* format:
                             |
                             | docker image build -t <name>:<tag>
                             | docker image build --tag <name>:<tag>
                             |
  Use the commit hash Git as | git log -1 --pretty=%H
  the image tag              |
                             |
  Use *docker image tag* to    | docker image tag <SOURCE_IMAGE><:TAG> <TARGET_IMAGE>:<TAG>
  create a new tagged image  |
                             |
--------------------------------------------------------------------------------
== Distributing Images on Docker Hub ==
  Docker Push                | docker image push <USERNAME>/<IMAGE_NAME>:<TAG>
                             |
  Creating an image for      | docker image tag <IMAGE_NAME>:<TAG> <USERNAME>/<IMAGE_NAME>:<TAG>
  Docker Hub:                |
                             |
--------------------------------------------------------------------------------
== Image History ==
  Show the history of an     | docker image history <IMAGE>
  image                      | docker image history --no-trunc <IMAGE>
                             | docker image history --quiet <IMAGE>
                             | docker image history --quiet --no-trunc <IMAGE>
                             |
--------------------------------------------------------------------------------
== Saving and Loading Images ==
  Save one or mor images to  | docker image save <IMAGE> > <FILE>.tar
  a tar archive:             | docker image save <IMAGE> -o <FILE>.tar
                             | docker image save <IMAGE> --output <FILE>.tar
                             |
  Load an image from a tar   | docker image load < <FILE>.tar
  archive                    | docker image load -i <FILE>.tar
                             | docker image load --input <FILE>.tar
                             |
--------------------------------------------------------------------------------
== Inspecting Container Processes ==
  Docker top:                | Display the running processes of a container
                             |   docker container top <NAME>
                             |
  Docker stats:              | Display a live stream of container(s) resource
                             | usage statistics
                             |   docker container stats <NAME>
                             |
--------------------------------------------------------------------------------
== Having Containers Start Automatically ==
  Auto-restarting            | To configure the restart policy for a container,
                             | use the *--restart* flag:
                             |
                             | * *no*: The default. Do not automatically restart
                             |       the container
                             |
                             | * *on-failuer*: Restart the container if it exits
                             |       due to an error, which manifests as a
                             |       non-zero exit code
                             |
                             | * *always*: Aways restart the container if it stops
                             |
                             | * *unless-stopped*: Similar to always, except that
                             |       when the container is stopped, it is not
                             |       restated even after the Docker daemon restarts
                             |
  Automatically restarting a | docker container run -d --name <NAME> --restart <RESTART> <IMAGE>
  container (example)        |
                             |
                             |
                             |
--------------------------------------------------------------------------------
== Docker Events ==
  Get real-time events from  | docker system events
  the server                 | docker system events --since '<TIME_PERIOD>'
                             |
  Filter events              | docker system events --filter <FILTER_NAME>=<FILTER>
                             |
--------------------------------------------------------------------------------
== Managing Stopped Containers ==
  Remove one or more         | docker container rm <NAME>
  Containers                 |
                             |
  List the rm flags          | docker container rm -h
                             |
  Start one or more stopped  | docker container start <NAME>
  containers                 |
                             |
  Remove all stopped         | docker container prune
  containers                 |
--------------------------------------------------------------------------------
== Managing Docker with Portainer ==
  Create a volume for        | docker volume create portainer_data
  Portainer's data           |
                             |
  Create the Portainer       | `docker container run -d --name portainer -p 8080:9000 \`
  container                  | `-v /var/run/docker.sock:/var/run/docker.sock \`
                             | `-v portainer_data:/data portainer/portainer`
                             |
--------------------------------------------------------------------------------
== Updating Containers with Watchtower ==
  Create a Watchtower        | docker run -d --name watchtower --restart always \
  container                  | -v /var/run/docker.sock:/var/run/docker.sock \
                             | v2tech/watchtower -i 15
                             |
                             |    *-i 15* -> Intervale - will perform its
                             |             action every 15 seconds
                             |
--------------------------------------------------------------------------------
== Installing Docker Compose ==
  Download the latest version| sudo curl -L "https://github.com/docker/compose/release/download/1.23.2/docker-compost-$(uname -s)-$(uname -m)" \
  of Docker Compose          | -o /usr/local/bin/docker-compose
                             |
  Apply executable           | sudo chmod +x /usr/local/bin/docker-compose
  permissions:               |
                             |
  Test Docker Compose        | docker-compose --version
                             |
--------------------------------------------------------------------------------
== Compose Commands ==
  Management Commands        | * *up*: Create and start containers
                             | * *ps*: List containers
                             | * *stop*: Stop services
                             | * *start*: Start services
                             | * *restart*: Restart services
                             | * *down*: Stop and remove containers, networks, images,
                             |       and volumes
                             |
  Create a compose service   | docker-compose up -d
                             | docker-compose -f <COMPOSe_FILE_PATH>.yml ps
                             |
  List the containers created| docker-compse ps
  by compose                 |
                             |
  Stop a compose service     | docker-compose stop
                             |
  Start a compose service    | docker-compose start
                             |
  Restart a compose service  | docker-compose restart
                             |
  Get a list of docker       | docker-compose -h
  compose commands           |
                             |
--------------------------------------------------------------------------------
== Creating a Compose File ==
  docker-compose.yml         | version: '3'
                             | services:
                             |   weather-app:
                             |     build:
  where to find the          |       context: .
  Dockerfile                 |       args:
                             |         - VERSION=v2.0
                             |     ports:
                             |       - "8081:3000"
                             |     environment:
                             |       - NODE_ENV=production
                             |
  Rebuilding image before    | docker-compose build
  bringing up app            |
                             |
  Rebuilding image without   | docker-compose build --no-cache
  using cached layers        |
                             |
--------------------------------------------------------------------------------
== Using Volumes and Networking with Compse ==
  Example docker-compose.yml | version: '3'
  file                       | services:
                             |   ghost:
                             |     container_name: ghost
  Define the image           |     image: ghost:latest
  Map the ports              |     ports:
                             |       - "80:2368"
  setting environment        |     environment:
  variables                  |       `- database__client=mysql`
                             |       `- database__connection__host=mysql`
                             |       `- database__connection__user=root`
                             |       `- database__connection__password=P4SSw0rd0!`
                             |       `- database__connection__database=ghost`
  Mapping volumes to the     |     volumes:
    container (service)      |       - ghost-volume:/var/lib/ghost
  Mapping networks to the    |     networks:
    container (service)      |       - ghost_network
                             |       - mysql_network
  relies on mysql to         |     depends_on:
  create service             |       - mysql
                             |
                             |   mysql:
                             |     container_name: mysql
                             |     image: mysql:5.7
                             |     environment:
                             |       - MYSQL_ROOT_PASSWORD=P4SSw0rd0!
                             |     volumes:
                             |       - mysql-volume:/var/lib/mysql
                             |     networks:
                             |       - mysql_network
                             |
  Define (create) volumes    | volumes:
                             |   ghost-volume:
                             |   mysql-volume:
  Define (create) networks   | networks:
                             |   ghost_network:
                             |   mysql_network:
                             |
--------------------------------------------------------------------------------
== Indtroduction to Docker Swarm ==
  Swarm 101                  | Swarm has two major components:
                             |   * an enterprise-grade secure cluster:
                             |     * Manage one or more Docker nodes as a cluster
                             |     * Encrypted distributed cluster store
                             |     * Encrypted networks
                             |     * Secure join tokens
                             |   * An orchestration engine for creating microservics:
                             |     * API for depolying and managng microservices
                             |     * Define apps in a declarative manifest file
                             |     * Perform rolling updates, rollbacks, and scale applications
                             |
                             |   * Swarm was initially a separate product layered on Docker
                             |   * Since Docker 1.12, it became a part of the engine
                             |
  The Cluster                | * A swarm consists of one or more Docker nodes
                             | * Nodes are either a manager or a worker
                             |
                             | * *Managers*:
                             |   * Manage the state of the cluster
                             |   * Dispatches tasks to workers
                             |
                             | * *Workers*:
                             |   * Accepts and executes tasks
                             | * State is held in etcd
                             |
                             | * Swam uses Transport Layer Security (TLS)
                             |   * Encrypted communication
                             |   * Authenticate Nodes
                             |   * Authorize roles
                             |
  Orchestration              | * The atomic unit of scheduling is a swarm service
                             | * The service construct adds the following to a container:
                             |   * scaling
                             |   * rolling updates
                             |   * rollback
                             | * A container wrapped in a service is a task or a replica
                             |
--------------------------------------------------------------------------------
== Running Docker in Swarm Mode ==
  Initialize the manager     | docker swam init --advertise-addr [PRIVATE_IP]
                             |
  Add the worker to the      | docker swarm join --token [TOKEN] [PRIVATE_IP]:2377
  cluster                    |
                             |
  List the nodes in the      | docker node ls
  swarm                      |
                             |
  To add a manager to this   | docker swarm join-token manager
  swarm, run:                |
                             |
--------------------------------------------------------------------------------
== Managing Swarm Nodes ==
  Listing nodes              | docker node ls
                             |
  Inspecting a node          | docker node inspect [NODE_NAME]
                             |
  Promoting a worker to a    | docker node promote [NODE_NAME]
  manager                    |
                             |
  Demoting a manager to a    | docker node demote [NODE_NAME]
  worker                     |
                             |
  Removing a node from the   | docker node -rm -f [NODE_NAME]
  swarm                      |
                             |
  Have a node leave the      | docker swarm leave
  swarm                      |
                             |
  Getting the *join-token*     | docker swarm join-token [worker | manager]
                             |
  Have the node rejoing the  | docker swarm join --token [TOKEN] [PRIVATE_IP]:2377
  swarm                      |
                             |
--------------------------------------------------------------------------------
== Working with Services ==
  Services                   | An application that is deployed out to a Docker
                             | host running in swarm mode is deployed out as a
                             | service. When a service is created, it is accepted
                             | by the swarm manager and the service definition
                             | represents the desired state. Based on the number
                             | of replicas, the swarm will schedule replica tasks,
                             | and each task invokes a single container, and these
                             | containers run in isolation.
                             |
  Creating a service         | docker service create -d --name [NAME] -p [HOST_PORT]:[CONTAINER_PORT] \
                             | --replicas [REPLICAS] [IMAGE] {CMD}
                             |
                             | example:
                             |   docker service create -d --name nginx_service -p 8080:80 --replicase 2 nginx:latest
                             |
                             |
  List services              | docker service ls
                             |
  Inspecting a service       | docker service inspect [NAME]
                             |
  Getting logs for a service | docker service logs [NAME]
                             |
  List all tasks of a        | docker service ps [NAME]
  service                    |
                             |
  Scaling a service up and   | docker service scale [NAME]=[REPLICAS]
  down                       |
                             |
  Updating a service         | docker service update [OPTIONS] [NAME]
                             |
--------------------------------------------------------------------------------
== Using Networks in Swarm Mode ==
  Overlay network driver     | The overlay network drive creates a distributed
                             | network across multiple Docker nodes. It sits on
                             | top of a the host-specific network, and his allows
                             | containers to go and communicate securely. Docker
                             | handles the routing of packets to the correct Docker
                             | host and to the correct container. This allows us
                             | to use the public IP of our swarm manager to go
                             | and access the service. And then, it's going to go
                             | route that traffic to the correct Docker host and
                             | to the correct correct container
                             |
  create an overlay network  | docker network create -d overlay [NAME]
                             |
  Create an encrypted overly | docker network create -d overlay --opt encrypted encrypted_overlay
  network                    |
                             |
  Create a service with an   | docker service create -d --name [NAME] --network [NETWORK] \
  overlay network            | -p [HOSTPORT]:[CONTAINER_PORT] --replicas [REPLICAS] \
                             | [IMAGE] [CMD]
                             |
  Adding a service to a      | docker service update --network-add [NETWORK] [SERVICE]
  network                    |
                             |
  Removing a service from a  | docker service update --network-rm [NETWORK] [SERVICE]
  network:                   |
                             |
--------------------------------------------------------------------------------
== Using Volumes in Swarm Mode ==
                             | When it comes to using volumes in Swarm mode, you
                             | will need to use a volume plugin as the native
                             | driver for volumes is local (if you create a volume
                             | it's only going to be created locally to where
                             | that command was executed.
                             |
  Adding Plugins:            | docker plugin install [PLUGIN] [OPTIONS]
                             |
  Listing plugins            | docker plugin ls
                             |
  Volume Plugins:            | * Hedvig
                             | * Pure Storage
                             | * HPE Nimble Storage
                             | * Nutanix DVP
                             | * Blockbridge
                             | * NexentaStor
                             | * StorageOS
                             | * Rex-Ray
                             |
  Digital Ocean example      | docker plugin install rexray/dobs DOBS_REGION=<DO_REGION> \
                             | DOBS_TOKEN=<DIGITAL_OCEAN_TOKEN> \
                             | DOBS_CONVERTUNDERSCORES=true
                             |
  Createing a volume using a | docker volume create -d [DRIVER] [NAME]
  driver                     | docker service create -d --name [NAME] --mount type=[TYPE],src=[SOURCE],dst=[DESTINATION] \
                             | -p [HOST_PORT]:[CONTAINER_PORT] --replicas [REPLICASE] [IMAGE] [CMD]
                             |
--------------------------------------------------------------------------------
== Deploying Stacks in Docker Swarm ==
  Creating the prometheus    | vi prometheus.yml
  .yml file:                 |
                             |
  Create a compose file      | vi docker-compose.yml
                             |
  Deploy the stack:          | docker stack deploy [NAME]
                             |
  Fix the volume permissions | sudo chown nfsnobody:nfsnobody -R /var/lib/docker/volumes/prometheus_data
                             |
--------------------------------------------------------------------------------
== Introduction to Docker Security ==
  Docker Security 101        |                   `+--------------------------------+`
                             |                   `| ------------------------------ |`
                             |                   `| |     Secrets Management     | |`
                             |                   `| ------------------------------ |`
                             |                   `| ------------------------------ |`
                             |                   `| |    Docker Content Trust    | |`
                             | *Docker Platform*   `| ------------------------------ |`
                             |   *Technologies*    `| ------------------------------ |`
                             |                   `| |     Security Scanning      | |`
                             |                   `| ------------------------------ |`
                             |                   `| ------------------------------ |`
                             |                   `| |         Swam Mode          | |`
                             |                   `| ------------------------------ |`
                             |                   `+--------------------------------+`
                             |
                             |                   `+--------------------------------+`
                             |                   `| ------------------------------ |`
                             |                   `| |          Seccomp           | |`
                             |                   `| ------------------------------ |`
                             |                   `| ------------------------------ |`
                             |                   `| |  Mandatory Access Control  | |`
                             |                   `| ------------------------------ |`
                             |                   `| ------------------------------ |`
                             |                   `| |        Capabilities        | |`
                             |      *OS (Linux)*   `| ------------------------------ |`
                             |     *Technologies*  `| ------------------------------ |`
                             |                   `| |       Control Groups       | |`
                             |                   `| ------------------------------ |`
                             |                   `| ------------------------------ |`
                             |                   `| |     Kernel Namespaces      | |`
                             |                   `| ------------------------------ |`
                             |                   `+--------------------------------+ `
                             |
  Name Spaces                | * Docker on Linux Namspaces:
                             |   * Process ID (pid)
                             |     - The PID ID namespace isolates the process free of each container
                             |       It prevents the container from seeing or accessing the process
                             |       tree of other containers, or the host that it's running on.
                             |   * Network (net)
                             |     - The net namespace provides each container with its own isolated
                             |       network stack. This includes things such as the network interface,
                             |       IP addresses, port ranges, and route tables.
                             |   * Filesystem/mount (mount)
                             |     - The mount namespace give every container its own unique isolated
                             |       file system. This prevents the container from accessing mount
                             |       namespaces of the Linux host or other containers.
                             |   * Inter-process Communication (ipc)
                             |     - The IPC namespace is used for sharing memory access within a
                             |       container and also isolates it from other containers.
                             |   * User (user)
                             |     - The user namespace allow you to go and map a user inside of a
                             |       container to a different uer on the host. a good example of this
                             |       is mapping the root user of a container to a non-root user on
                             |       the host.
                             |   * UTS (uts)
                             |     - The UTS namespace provides each container with its own unique
                             |       hostname
                             |
  Docker Swarm               | * Cryptographic noe ids
                             | * Mutual authentication via TLS
                             | * Secure join tokens
                             | * CA configuration with automatic certificate rotation
                             | * Encrypted cluster store
                             | * Encrypted cluster store
                             | * Enccrypted networks
                             |
  Docker Secrets             | Secrets Workflow:
                             | * A secret is created and posted to the Swarm
                             | * The secret is encrypted and stored
                             | * A service is created and the secret is attached
                             | * Secrets are encrypted in-flight
                             | * The secret is mounted into the container of a service
                             | * Whe the task is complete, the in-memory is torn down
                             |
                             |
                             |
                             |
                             |
-------------------------------------------------------------------------------
== Working with Docker Security ==
  Seccomp Profiles           | Testing Seccomp:
                             |   Docker container run -rm -it alpine sh
                             |   whoami
                             |   mount /dev/sda1 /tmp
                             |   swapoff -a
                             |
  Using a customer Seccomp   | docker container run --security-opt seccomp=[PROFILE] [IMAGE] [CMD]
  profile                    |
                             |
  Capabilities               | Dropping Capabilities:
    Drop a capability        |   docker container run --cap-drop=[CAPABILITY] [IMAGE] [CMD]
    Add a capability         |   docker container run --cap-add=[CAPABILITY] [IMAGE] [CMD]
                             |
                             | Test MKNOD:
                             |   docker container run --rm -it alpine sh
                             |   mknod /dev/random2 c 1 8
                             |
                             | Disable MKNOD:
                             |   docker container run --rm -it --cap-drop=MKNOD alpine sh
                             |   mknod /dev/random2 c 1 8
                             |
  Control Groups             | Limiting CPU and Memory
                             |   docker container runi -it --cpus=[VALUE] --memory=[VALUE] [SIZE] --memory-swap [VALUE][SIZE] [IMAGE] [CMD]
                             |
  Running                    | docker container run --rm -it --network host --pid host --userns host --cap-add audit_control \
    docker-bench-security    | -e DOCKER_CONTENT_TRUST=$DOCKER_CONTENT_TRUST \
                             | -v /var/lib:/var/lib \
                             | -v /var/run/docker.sock:/var/run/docker.sock \
                             | -v /usr/lib/systemd:/usr/lib/systemd \
                             | -v /etc:/etc --label docker_bench_security \
                             | docker/docker-bench-security
                             |
-------------------------------------------------------------------------------
== Docker Content Trust ==
  Creating a Key             | docker trust key generate [NAME]
                             |
  Importing a key            | docker trust key load [PEM] --name [NAME]
                             |
  Add signer                 | docker trust signer add --key [PEM] [NAME] [REPOSITOR]
                             |
  Remove signer              | docker trust signer remove [NAME] [REPOSITORY]
                             |
  Signing an Image           | docker trust sign [IMAGE]:[TAG]
                             |
  Temporaraly enabling DCT   | export DOCKER_CONTENT_TRUST=1
                             |
  Permanently enabling DCT   | vi /etc/docker/daemon.json
                             |
                             |     {
                             |         "content-trust": {
                             |             "mode": "enforced"
                             |         }
                             |     }
                             |
-------------------------------------------------------------------------------
== Working with Secrets ==
  createing a secret using   | STDIN | docker secret create [NAME] -
  STDIN                      | *Example*
                             | > openssl rand -base64 20 | docker secret create my_secret_data -
                             |
  Creating a secret using a  | docker secrete create [NAME] [FILE]
  file                       |
                             |
  List secrets               | docker secret ls
                             |
  inspecting a secret        | docker secret inspect [NAME]
                             |
  Using a secret:            | docker service create --name [NAME] --secret [SECRET] [IMAGE]
                             |
  Deleteing a secret         | docker secret rm [NAME]
                             |
  Secrets location on        | /run/secrets
  container                  |
                             |
                             |
  *Example*                    | version: '3.1'
  docker-compose.yml file    |
                             | services:
                             |   db:
                             |     image: mysql:5.7
                             |     volumes:
                             |       - db_data:/var/lib/mysql
                             |     networks:
                             |       mysql_internal:
                             |         aliases: ["db"]
                             |     environment:
                             |       MYSQL_ROOT_PASSWORD_FILE: /run/secrets/db_root_password
                             |       MYSQL_DATABASE: wordpress
                             |       MYSQL_USER: wordpress
                             |       MYSQL_PASSWORD_FILE: /run/secrets/db_password
                             |     secrets:
                             |       - db_root_password
                             |       - db_password
                             |
                             |   wordpress:
                             |     depends_on:
                             |       - db
                             |     image: wordpress:latest
                             |     networks:
                             |       mysql_internal:
                             |         aliases: ["wordpress"]
                             |       wordpress_public:
                             |     ports:
                             |       - "8001:80"
                             |     environment:
                             |       WORDPRESS_DB_HOST: db:3306
                             |       WORDPRESS_DB_USER: wordpress
                             |       WORDPRESS_DB_PASSWORD_FILE: /run/secrets/db_password
                             |     secrets:
                             |       - db_password
                             |
                             | secrets:
                             |   db_password:
                             |     file: db_password.txt
                             |   db_root_password:
                             |     file: db_root_password.txt
                             |
                             | volumes:
                             |   db_data:
                             | networks:
                             |   mysql_internal:
                             |     driver: "overlay"
                             |     internal: true
                             |   wordpress_public:
                             |     driver: "overlay"
                             |
  Deploy the stack           | docker stack deploy --compose-file docker-compose.yml [NAME]
                             |   *NOTE:* the secrets' files must be in the same
                             |         directory as the docker-compose.yml file
                             |
-------------------------------------------------------------------------------
== Lab notes ==
  first lab                  | FROM node AS source
                             | RUN mkdir -p /node/weather-app
                             | ADD src/ /node/weather-app
                             | WORKDIR /node/weather-app
                             | RUN npm install
                             |
                             | FROM node:alpine
                             | ARG APP_VERSION=V1.1
                             | LABEL org.label-schema.version=$APP_VERSION
                             | ENV NODE_ENV="production"
                             | COPY --from=source /node/weather-app /node/weather-app
                             | WORKDIR /node/weather-app
                             | EXPOSE 3000
                             | ENTRYPOINT ["./bin/www"]
                             |
                             | cd src
                             | git log -1 --pretty=%H
                             | cd ../
                             |
                             | sudo docker container run -d --name weather-app -p 8080:3000 linuxacademy/weather-app:<HASH>
                             |
[[-------------------------------------------------------------------------------]]
