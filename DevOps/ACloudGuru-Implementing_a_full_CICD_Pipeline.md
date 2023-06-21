--------------------------------------------------------------------------------
= A Cloud Guru - Implementing a Full CI/CD Pipeline =
--------------------------------------------------------------------------------
== ch-2.2 Installing Git ==
  *Common configuration*       | git config --global user.name "<your name>"
  *Options*                    | git config --global user.email <your email>
                             |
  *Generate an ssh keypair*    | ssh-keygen -t rsa -b 4096
                             |
--------------------------------------------------------------------------------
== Gradle ==
  *Installing Gradle Wrapper*  | If you already have a normal Gradle install on
                             | your system, you can use it to easily install the
                             | wrapper:
                             |   * cd to the project root directory
                             |   * gradle wrapper
                             |
                             | You should also add the line *.gradle* to your *.gitignore* file
                             |
                             | Run Gradle commands against your project like this:
                             |   * cd to the project root directory
                             |   * ./gradelw build
                             |
--------------------------------------------------------------------------------
== Gradle Builds ==
  *Gradle Basics*              | A gradle build is defined in a groovy script called
                             | *build.gradle*, located in the root directory of
                             | your project.
                             |
                             | Use *gradle init* to initialize a new project.
                             | This also sets up the gradle wrapper for you.
                             |
  *Running a gradle Build*     | Gradle builds consist of a set of tasks that you
                             | call from the command line:
                             |   ./gradlew someTask someOtherTask
                             |
                             | This command will run a task named someTask, and
                             | a task named someOtherTask
                             |
  *Defining Tasks*             | The *build.gradle* file controls what tasks are
                             | available for your project
                             |
                             | You can define your own tasks with custom code in
                             | *build.gradle*
                             |   task myTask{
                             |     printlin 'Hello, World!'
                             |   }
                             |
  *example from tutorial*      | task sayHello << {
  *(<< has been depricated*    |   println 'Hello, World!'
   *in current version)*       | }
                             |
                             | task anotherTask << {
                             |   println 'This is another task'
                             | }
                             |
  *Task Dependencies*          | Gradle uses the concept of task dependencies to
                             | determine what tasks need to be run for a particular
                             | build command
                             |   * If you run a task, any other tasks that depend
                             |     on it will also be run
                             |
                             | Task Dependencies also determine the order in
                             | which tasks gets run:
                             |   * A task's dependencies will always run before
                             |     that task
                             |
                             | You can define a dependency relationship between
                             | tasks in *build.gradle* like this:
                             |   * taskA.dependsOn taskB
                             |
  *Plugins*                    | Gradel has a huge variety of plugins available,
                             | many of them contributed by the community.
                             |
                             | Plugins add all kinds of functionality to Gradle.
                             | They usually include pre-built tasks that you can
                             | configure to do what you need.
                             |
                             | You can include plugins in your *build.gradle*
                             | like this:
                             |   plugins{
                             |     id "<plugin id>" version "<plugin version>"
                             |   }
                             |
--------------------------------------------------------------------------------
== Automated Testing ==
  *Types of Automated Tests*   | There are multiple types of automated test:
                             |   * Unit Tests - focus on testing small pieces of
                             |     code in isolation. Usually a single method or
                             |     function
                             |
                             |   * Integration Tests - test larger portions of
                             |     an application that are integrated with each
                             |     other.
                             |
                             |   * Soke Test/Sanity Tests - these are high-level
                             |     integration tests that verify basic, large-scale
                             |     things like whether or not the application runs,
                             |     whether application endpoints return http 500
                             |     erros, etc.
                             |
  *Running Automated Tests*    | How the tests are run depends on what type of
  *in Gradel*                  | tests you have and the technology used to build them.
                             | Generally, automated tests will be run in Gradle
                             | as a task that gets executed as part of the build
                             | process:
                             |   * task build
                             |   * task test
                             |   * build.dependsOn test
                             |
--------------------------------------------------------------------------------
== CI Overview ==
  *Continuous Integration*     | Continuous Integration (CI): the practice of
                             | frequently merging code changes.
                             |
                             | But frequent merges cause difficulties:
                             |   * What if the coe doesn't compile after a merge?
                             |   * What if someone broke something?
                             |   * It would be a lot of work to check these things
                             |     on every merge.
                             |
  *How CI works*               | A CI server executes a build that automatically
                             | prepares/compiles the code and runs automated
                             | tests.
                             |
                             | If something is wrong, the build fails. The team
                             | can get immediate feedback if their change broke
                             | something.
                             |
                             | Merging frequently throughout the day and getting
                             | quick feedback means that if you broke something,
                             | you broke it with your changes within the last
                             | couple of hours. This is much easier to fix than
                             | if you broke something with your changes from a
                             | week ago.
                             |
--------------------------------------------------------------------------------
== Installing Jenkins ==
  Installation documentation | https://jenkins.io/doc/book/installing
                             |
                             | There are several installation options:
                             |   * Docker container
                             |   * WAR file
                             |   * Packages for various OSes
                             |
--------------------------------------------------------------------------------
== Triggering Builds with Git Hooks ==
  *Webhooks*                   | Webhooks are event notifications made from one
                             | application to another over http.
                             |
                             | In Jenkins, we can use webhooks to have GitHub
                             | notify Jenkins whenever the coe in GitHub changes.
                             | Jenkins can respond by automatically running the
                             | build to implement any changes
                             |
                             | We can configure Jenkis to automatically create
                             | and manage webhooks in GitHub as necessary.
                             |
  *Setting up GitHub*          | Configuring webhooks in Jenkis is relatively easy:
  *Webhooks in Jenkins*        |   * Create an access token in GitHub that has
                             |     permissions to read and create webhooks
                             |   * Add a GitHub server in Jenkins for GitHub.com
                             |   * Create a Jenkins credential with the token and
                             |     configure the GitHub server configuration to use it
                             |   * Check "Manage Hooks" for the GitHub server
                             |     configuration
                             |   * In the project configuration, under "Build triggers",
                             |     select "GitHub hook trigger for GITScm polling"
                             |
--------------------------------------------------------------------------------
== Jenkins Pipelines ==
  *What is Jenkins Pipelines?* | Jenkins Pipelines is a set of Jenkis plugins that
                             | support doing continuous delivery in Jenkins
                             |
                             | A Jenkis Pipeline is a na utomated process built
                             | on these tools. It takes source code through a
                             | "pipeline" from the source code creation all the
                             | way to production deployment.
                             |
                             | You can find the Jenkis Pipelines documentation
                             | at https://jenkis.io/doc/book/pipeline
                             |
  *How do you create a*        | Pipelines adheres to the best practice of
  *Jenkis Pipelien?*           | infrastructure as code.
                             |
                             | Therefore, a pipelne is implemented in a file that
                             | is kept in source control along with the rest of
                             | the application code. This file is called a *Jenkinsfile*.
                             |
                             | To create a Pipeline, simply create a file called
                             | Jenkinsfile and add it to your source control repo.
                             |
                             | When creating the Jenkins project, choose the
                             | "Pipeline" or "Multibranch Pipeline" project type
                             |
  *What Goes in a*            | Pipelines has a domain-specific-language (DSL) that
  *Jenkinsfile?*              | is used to define the pipeline logic.
                             |
                             | There are two styles of Pipeline syntax you can use
                             | (you must choose one or the other):
                             |   * *Scripted* - A bit more like procedural code
                             |   * *Declarative* - Syntax describes the Pipeline logic
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
--------------------------------------------------------------------------------
