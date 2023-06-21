[[../Docker.wiki|Back]]
[[--------------------------------------------------------------------------------]]
Docker in practice  stoped at page 18 (docker layering)
--------------------------------------------------------------------------------
== Key Docker Commands ==
  docker build               | Build a Docker image
  docker run                 | Run a Docker image as a container
  docker commit              | Commit a Docker container as an image
  docker tag                 | Tag a Docker imager
                             |
== Options for create Docker images ==
  Docker commands / "by hand"| Fire up a container with docker run and input the
   (proofs of concepts)      | commands to create your image on the command
                             | line. Create a new image with docker commit
                             |
  Dockerfile                 | Build from a known base image, and specify the
                             | build with a limited set of simple commands
                             |
  Dockerfile and             | Same as Dockerfile, but you hand over control of
  configuration management   | the build to a more sophisticated CM tool
  (CM) tool                  |
                             |
  Scratch image and import a | From an empty image, import a TAR file with the
  set of files               | required files
                             |
== Writing a Dockerfile ==
  * Define a base image      | FROM node
  * Declare the maintainer   |  LABLE maintainer ian.miell@gmail.com
  * Clones the todo code     |  RUN git clone -q https://github.com/docker-in-practice/todo.git
  * Creats a namespace for   |  WORKDIR todo
    working files            |
  * Runs the npm install cmd |  RUN npm install > /dev/null
  * Specifies that containers|  EXPOSE 8000
    from the built image     |
   should listen on port     |
  * Specifies which command  |  CMD ["npm","start"]
    will be run on startup   |
                             |
== Building a Docker image ==
  docker build .             | docker build <path to Dokerfile file>
                             |
== Tagging the docker image from image ID ==
  docker tag 66c7eikd todoapp| docker tag <image id> <tag>
                             |
== Running a Docker container ==
  docker run -i -t -p 8000:8000 --name example1 todoapp
                             |
                             | The Docker run subcommand starts the
                             | container, -p maps the contaier's port
                             | 8000 to the port 8000 on the host machine,
                             | --name gives the container a unique name,
                             | and the last argument is the image
                             |
  terminate the process and  | Ctrl-c
  the container              |
                             |
  Command to see containers  | docker ps -a
  that have been started     |
  and removed, with ID/status|
                             |
  docker diff shows you what | docker diff <unique name>
  files have been affected   |
  since the image was        |
  instantiated as a container|
                             |
