[[Docker.wiki|Back]]
--------------------------------------------------------------------------------
Creating custom Docker images
--------------------------------------------------------------------------------
                             |
--------------------------------------------------------------------------------
Docker Compose
--------------------------------------------------------------------------------
Benefits of using Docker Compose
  - Separate CLI that gets installed along with Docker
  - Used to start up multiple Docker containers at the same time.
  - Automates some of the long-winded arguments we were passing to 'docker run'
                             |
docker-compose.yml
  preview                    | Here are the containers I want to create
                             |   redis-server
                             |     - Make it using the 'redis' image
                             |   node-app
                             |     - Make it using the Dockerfile in the current directory
                             |     - Map port 8081 to 8081
--------------------------------------------------------------------------------
Docker-compose restart policy
  "no"                       | never attempt to restart this container if it
                             | stops or crashes
                             |
  always                     | If this container stops *for any reason*
                             | always attempt to restart it
                             |
  on-failure                 | Only restart if the container stops with an
                             | error code
                             |
  unless-stopped             | Always restart unless we (the developers)
                             | forcibly stop it
                             |
                             |
                             |
--------------------------------------------------------------------------------
Continuous Intergration With docker
--------------------------------------------------------------------------------
Example workflow
  `Dev-------------------------------------+`
  `| - Create/change features              |`
  `| - Make changes on a non-master branch |`
  `+---------------------------------------+`
  `                  | `
  `            Push to github`
  `                  | `
  `            Create Pull request`
  `            to merge with master`
  `                  | `
  `Test-------------------------+`
  `| - Code pushed to Travis CI |`
  `| - Tests run                |`
  `+----------------------------+`
  `                  | `
  `          Merge PR with master`
  `                  | `
  `Prod-------------------------------+`
  `| - Code pushed to Travis CI       |`
  `| - Test run                       |`
  `| - Deply to AWS Elastic Beanstalk |`
  `+----------------------------------+`
[[Docker.wiki|Back]]
