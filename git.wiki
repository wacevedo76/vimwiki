--------------------------------------------------------------------------------
Git
--------------------------------------------------------------------------------
** Most useful git commands
Config                       |
  Alows you to set:          |
    Default user name        | git config --global user.name "John Doe"
    Default email            | git config --global user.email johndoe@example.com
    default editor           |
    and others               |
                             |
Remote                       |
  Used to work with remote   |
  repositories               |
  list all remotes           | git remote -v
  Add remote                 | git remote add <name> <url>
                             |
  start a new repository     | git init
                             |
  Push all branches to       | git push <git alias> --all
  remote repository          |
                             |
  Clone a repository         | git clone <repo> <directory>
                             | git clone http://example.com/gitproject.git
                             |
  remove untracked file      | git rm --cached [filename]
  without deleting file      |
  --------------------------------------------------------------------------------
  ** YAML: "Yaml Ain't Markup Language"
    YAML: Features:
    - Used to format & represent Data
    - Superset of JSON
    - Easy to read / designed wit hhuman readability in mind
    - Convert between JSON and Yaml
    YAML: Use Cases:
    - Most DevOps tools such as Ansible, Kubernetes, Gitlab, Openstack & more..
    - Transmit data from 2 application components
    - Import / Export data
    YAML: Indentation
    - Uses spaces for indentation
    - No mandatory spaces ( No need for consistency in spacing after "-")
      Example:
        - the
        -   spacing
        -     doesn't
        -   matter
    YAML: Comments
    - Require the "#" hash/number symbol at the end of the line
      # this is a comment
    - NOTE: Multiline comements are not accepted
    YAML: Data Types
    - Nulls
      variable: --> (null | Null | NULL | ~ )
    - Booleans
      Variable: True --> ( True/False, Yes/No, On/Off )
    - Numbers
      variable: 123
    - Strings
      variable: "123"
    YAML: Lists
      - Elements will be added as long as indentation is in place
      - Lists can be defined in block or square brackets syntax:

        Listname:
          - one
          - two
          - three

        listname: [one, two, three]
    YAML: Dictionaries
      - Requires indentation and a key followed by a colon and space
      - Can be defined in block or round bracket syntax

        cat:
          name: mirana
          color: brown
          age: 3 years

        Cat: {name: mirana, color: brown,...}
    YAML: Nesting
      - Can nest dictionaries in lists and vice versa.
--------------------------------------------------------------------------------
** Gitlab CI/CD Pipeline
  - Defined in the ".gitlab-ci.yml" file in the root directory of your Gitlab project
    - Job:
      A block of YAML code used to perform an action in a pipeline. Requres the "script:" key
    - Stages:
      Contains 1 or more jobs. It defines when to run a job. The stages are defined by
      the "stages:" key.
    - Script:
      Specifies the commands that the runner will execute in the job. Defined with
      the "script:" key
    - Image:
      Specify docker image to be used for a job or the whole pipeline. Defined with
      "image:" key:

      stages:
        - build
        - test

      Jobname1:
        stage: build
        image: node:latest
        script:
          - npm install

      Jobname2:
        stage: test
        script:
          - echo "This job is for testing"
--------------------------------------------------------------------------------
** Utilizing Artifacts
  Artifacts
    - Collection of data such as fiels, code, dependencies and more
    - Output by one job and can be consumed by the follwoing jobs
    - Gitlag jobs generate 2 types of artifacts:
      - Job Artifacts:
        - Archive of files and directories
        - Can be downloaded through API/UI
        - Requires the "artifacts:" keyword
        - Automatically downloaded in the jobs in following stages
          job_name:
            script: echo "hello world" > helloworld.txt
            artifacts:
              paths:
                - helloworld.txt
      - Pipeline Artifacts:
        - Mainly reports from testing tools and vulnerability scans
        - Viewed in Pipeline views, Merge Requests and in security and
          compliance section
        - Requires the "artifacts: reports" keyword
          artifacts:
            paths:
              - target/surefire-reports/TEST-*.xml
            reports:
              junit:
                - target/surefire-reports/TEST-*.xml
--  Ended on video 25  ---------------------------------------------------------
                             |
