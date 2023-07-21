### Artifactory Installation
* Prerequisites for JFrog
   * small or medium instance t2 type
   * 2cpus
   * 8081 and 8082 and ssh ports (22)
   * openjdk 11

==> $ sudo apt update
* First of all add the GPG key by entering the following command.
==> sudo apt install openjdk-11-jdk -y

==> $ wget -qO - https://releases.jfrog.io/artifactory/api/gpg/key/public | sudo apt-key add -;
* Add jfrog repository in your apt list. Just copy and paste the following command in your terminal.

==> $ echo "deb https://releases.jfrog.io/artifactory/artifactory-pro-debs xenial main" | sudo tee -a /etc/apt/sources.list;
* Let’s then update apt index,

==> $ sudo apt update
* Now, you can install using jfrog service by entering the following command.

==> $ sudo apt install jfrog-artifactory-oss
* Start the service,

==> $ sudo systemctl start artifactory.service
* Enable the service,


==> $ sudo systemctl enable artifactory.service
* Check the status of service

==> $ sudo systemctl status artifactory.service

## Access Jfrog UI
* Open your browser and enter http://IP_or DOMAIN-NAME:8081/artifactory

* Use default username and password to loging.
   * admin
   * password

* You need to reset the admin password.

* Setup the base URL, like your domain name to access the JFrog artifactory web UI. You can skip if you don’t have any.

* Now, the next step is to configure the default proxy. If your enterprise has a proxy gateway for accessing the server, use it otherwise skip it.

* Now your installation and basic configuration is finished. You can start creating a repository based on your project.