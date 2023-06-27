### Building Java
* To make it simple to build java code , Apache foundation has created a tool called as Ant
* In Ant we configure the build using build.xml [Refer Here](https://ant.apache.org/manual/using.html)
* Then a tool called as Maven was released which can perform
    * build
    * packaging
    * dependency management
    * documenation
* Maven goes with ``` Convention over Configuration ``` and all of them are around a file which is referred as ``` pom.xml ``` (project object model)
* Maven has a lifecycle
   * validate
   * compile
   * test
   * package
   * install
   * deploy
   * clean

   ![Preview](./Images/maven.png)

### Dependencies
* All the development projects depend on external libraries
       * Java: maven packages
       * node js: npm packages
       * python: pip packages
       * dotnet: nuget packages
* There is a need for managing dependencies

![Preview](./Images/Jenkins8.png)

![Preview](./Images/Jenkins9.png)

![Preview](./Images/Jenkins10.png)

### Jenkins (Contd)
* Installing Jenkins [Refer Here](https://www.jenkins.io/download/)
* Software and Hardware requirements for jenkins [Refer Here](https://www.jenkins.io/doc/book/installing/linux/#prerequisites)
* Basic Requirements
![Preview](./Images/Jenkins-Install.png)

* Initially lets take a free tier eligible machine 
   * AWS: t2.micro

   ![Preview](./Images/ec2.png)

   * Azure: Standard_B1s 

* Login to the ubuntu VM
* Now install java 11 on ubuntu [Refer Here](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-20-04)

![Preview](./Images/Jenkins11.png)

![Preview](./Images/Jenkins12.png)

![Preview](./Images/Jenkins13.png)

![Preview](./Images/Jenkins14.png)

* Commands used

```
sudo apt update
sudo apt-cache search openjdk
sudo apt install openjdk-11-jdk -y
java -version
```
* Now lets try to install jenkins on ubuntu [Refer Here](https://pkg.jenkins.io/debian-stable/)

![Preview](./Images/Jenkins15.png)

* Commands used

```
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee     /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]     https://pkg.jenkins.io/debian-stable binary/ | sudo tee     /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install fontconfig jenkins -y
sudo systemctl status jenkins.service
```
* Now Navigate to ``` http://<publicip>:8080 ```

![Preview](./Images/Jenkins16.png)


* Continue the installation

![Preview](./Images/Jenkins17.png)

![Preview](./Images/Jenkins18.png)

![Preview](./Images/Jenkins19.png)

![Preview](./Images/Jenkins20.png)

![Preview](./Images/Jenkins21.png)

![Preview](./Images/Jenkins22.png)

## Now lets see what has happened on the ubuntu vm to make jenkins work

*  Lets see the users in the linux system
    * command: ``` sudo cat /etc/passwd ```. A new user called as ``` jenkins ``` is created and the group name is ``` Jenkins ``` with the home directory of ``` /var/lib/jenkins ```
 
 ![Preview](./Images/Jenkins23.png)

 ![Preview](./Images/Jenkins24.png)


* In Jenkins we create jobs, Lets create one now

![Preview](./Images/Jenkins25.png)

![Preview](./Images/Jenkins26.png)

![Preview](./Images/Jenkins27.png)

![Preview](./Images/Jenkins28.png)

![Preview](./Images/Jenkins29.png)

![Preview](./Images/Jenkins30.png)

![Preview](./Images/Jenkins31.png)

![Preview](./Images/Jenkins32.png)

* From the jenkins UI, no matter what user you are logged in as, the low level commands are executed as a ``` jenkins ``` user
Now lets try to do ``` sudo apt update ``` from the jenkins ui

![Preview](./Images/Jenkins33.png)

![Preview](./Images/Jenkins34.png)

![Preview](./Images/Jenkins35.png)

* Now build the job/project

![Preview](./Images/Jenkins36.png)

![Preview](./Images/Jenkins37.png)

* From Jenkins UI we can do anything that the linux user ``` jenkins ``` can do.
From Jenkins UI if we need to do installations etc, we need sudo permissions without password.
* So Lets configure linux ``` jenkins ``` user to have sudo permissions without password prompts

![Preview](./Images/Jenkins38.png)

* Now lets explore the home directory of jenkins

![Preview](./Images/Jenkins39.png)

* We have create a project called as ```Day1 ```
* Lets explore the jobs folder

* Now lets create a job which leads to creation of some files

![Preview](./Images/Jenkins40.png)

![Preview](./Images/Jenkins41.png)

![Preview](./Images/Jenkins42.png)

![Preview](./Images/Jenkins43.png)

![Preview](./Images/Jenkins44.png)

![Preview](./Images/Jenkins45.png)

![Preview](./Images/Jenkins46.png)

## Exercise: Try to Create Jenkins on the Centos 7 Server

* Installation steps for centos/redhat

```
sudo yum search openjdk
sudo yum install java-11-openjdk-devel -y
sudo wget -O /etc/yum.repos.d/jenkins.repo   https://pkg.jenkins.io/redhat-stable/jenkins.repo --no-check-certificate
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum upgrade
sudo yum install epel-release -y
sudo yum install jenkins -y
sudo systemctl daemon-reload
sudo systemctl status jenkins.service
sudo systemctl enable jenkins.service
sudo systemctl start jenkins.service
```
* If i want to run some commands periodically on a server or laptop,
       * Windows => Scheduler
       * Linux => Cron Job
* Jenkins is a Cron/Scheduler on Steriods fine tuned for Continuous Integration and Continuous Deployment
* Plugin is an addon to jenkins, which provides functionality on the jenkins ui



