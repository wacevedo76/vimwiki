[[../Docker.wiki|Back]]
--------------------------------------------------------------------------------
* Docker and Kubernetes
--------------------------------------------------------------------------------
Detach from within a container
  cntr+p cntr+q
** Manipulating Containers with Docker Client
Creating and Running a       | Syntax: Reference the - Try to create and - Name of image to use
Container from an immage     |         Docker Client   run a container     for this container
                             |
                             |         docker run <image name>
                             |
Create / Start Container     | Syntax: Reference the - Try to create and - Name of image to use - Default Command
overriding /running command  |         Docker Client   run a container     for this container     override
                             |
                             |         docker run <image name> command!
                             | i.e.:   docker run busybox echo hi there <-- echo (command) argument list (hi there)
                             |         docker run busybox ls
                             |
List running windows         |         docker ps
                             |
List all containers          |         docker ps --all
                             |
create container             |         docker create hello-world   # will display its docker id
                             |
start a container            |         docker start -a <docker id> # "-a" means to attach container and return output
                             |           NOTE: when you start a container, as apposed to running, it alwasy starts with the
                             |                 default command, you can not issue a second default command
                             |
remove containers            |         docker system prune
  - all stopped containers   |
  - networs not being used   |
  - dangling images          |
  - all build cache          |
                             |
Get system logs from container         docker logs <container id>
                             |
Stop a container             |
  Stop a container           | docker stop <container ID> # sends sig term to running process
  kill a container           | docker kill <container ID> # sends killtermk to
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
[[../Docker.wiki|Back]]

