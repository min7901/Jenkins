## Jenkins Project
* In Jenkins the traditional way of creating project/job is called as Free Style
* The Free Style Jenkins Job Contains the following sections
    * General
        * Basic information about project
    * Source Code Management:
        * Section for configuring SCM
    * Build Triggers:
        * Section for configuring when to start the build
    * Build Environment:
        * Has information and options to control workspace and logs
    * Build:
        * This is section used to configure the builds
    * Post Build:
        * Actions to be performed after the build is complete

* Jenkins is a plugin based tool, the Functionality to show UI to the user and converting the interaction into low level commands is done by Plugin.
* Plugins can be developed by using Java Language
* There are lot of community plugins. Plugins generally have the format of hpi (hudson plugin interface) or jpi (jenkins plugin interface)
* Before installing subversion plugin

![Preview](./Images/Jenkins78.png)

* Lets install a plugin for Subversion

![Preview](./Images/Jenkins79.png)

![Preview](./Images/Jenkins80.png)

![Preview](./Images/Jenkins81.png)

![Preview](./Images/Jenkins82.png)

![Preview](./Images/Jenkins83.png)

* Plugins of the jenkins are available at Refer Here
Plugins can be installed in 3 ways
  * Using the Plugins UI
  * Using the Jenkins-cli
  * Direct Upload

## Distributed Builds
* When we work with any CI/CD system, Working with one server is not possible due to various reasons
   * Projects might have different build environments
   * Every build on one server will make this a single point of failure
    ![Preview](./Images/Jenkins84.png)
* So jenkins supports distributed builds, where we can have a jenkins master is the central server to create and configure jobs and then to run the jenkins jobs, we create jenkins nodes.
* Jenkins node is a different machine with jenkins agent in it.
* Jenkins nodes have labels and Jenkins master will try to identify the best fit node for the project based on the labels on the node.
* If the labels on the project/job match node, then jenkins will execute the job on a particular node as mentioned in the below image

![Preview](./Images/Jenkins85.png)

* To establish the communication between jenkins master and nodes, jenkins has by default two ways
  * Controller based
  * SSH Based

* [Refer Here](https://www.jenkins.io/doc/book/using/using-agents/) for the official docs to connect to nodes
* Lets create two more linux servers. On these server lets create a user called as jenkins and give admin permissions (sudo permission without password) 
   * In one server i will be install java 8

    ![Preview](./Images/Jenkins86.png)

   * In other server i will be install java 11

* Now lets configure Node-1 (jdk 8 and mvn) as a node via ssh to the jenkins server
* Manage Jenkins => Manage Nodes

![Preview](./Images/Jenkins87.png)

![Preview](./Images/Jenkins88.png)

![Preview](./Images/Jenkins89.png)

![Preview](./Images/Jenkins90.png)

![Preview](./Images/Jenkins91.png)

* Lets create a project to run on node-1 to build game of life [Refer Here](https://github.com/wakaleo/game-of-life). In this project i will be using the forked verson [Refer Here](https://github.com/devops-easy/game-of-life.git)

![Preview](./Images/Jenkins92.png)

![Preview](./Images/Jenkins93.png)

![Preview](./Images/Jenkins94.png)

![Preview](./Images/Jenkins95.png)

![Preview](./Images/Jenkins96.png)

![Preview](./Images/Jenkins97.png)

![Preview](./Images/Jenkins98.png)

![Preview](./Images/Jenkins99.png)

* Now lets configure the node2 with jdk11 and maven

![Preview](./Images/Jenkins103.png)

![Preview](./Images/Jenkins104.png)

* Jenkins can run multiple projects in parallel, but one project will be assigned to only one executor

![Preview](./Images/Jenkins100.png)

* If you want to change this, we need to configure concurrent builds

![Preview](./Images/Jenkins101.png)

![Preview](./Images/Jenkins102.png)

* When we execute any jenkins project a build id which is by default a running number (Start from 1 ) is assigned.