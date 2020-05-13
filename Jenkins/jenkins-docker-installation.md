# TO INSTALL JENKINS DOCKER ON UBUNTU INSTANCE/VM

To install jenkins docker on ubuntu VM

## Install docker

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install -y docker-ce
sudo usermod -aG docker ubuntu
sudo systemctl restart docker
docker --version
```

## create a new directory
This is necessary to store all jenkins files and resources in the host machine
```
mkdir -p /var/jenkins_home
```
## change ownership of the dir
chown -R 1000:1000 /var/jenkins_home/

## RUN JENKINS CONTAINER

To run jenkins container, you should pull the jenkins image
_The image used here is an image I prepared with the Dockerfile below_
https://github.com/Ariseaz/devops-pro/blob/master/Docker/jenkins.Dockerfile

Pull the docker hub image below to your Ubuntu environment
```
docker pull adenijiazeez/jenkins-docker:latest
```
The command below would run a jenkins docker container while mapping the container jenkins_home directory to the host directory, at the same time the docker sock running in the container will sync with the docker engine on the host

```
sudo docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d adenijiazeez/jenkins-docker
```

## DOCKER COMMANDS

check list of docker images
```
docker images
```
To list running docker instance/container
```
docker ps
```
To list all docker instance

```
docker ps -a
```

## Another way to deploy jenkins docker container using bash script

```
wget https://raw.githubusercontent.com/Ariseaz/devops-pro/master/script/jenkins_docker_install.sh
chmod +x jenkins_docker_install.sh
```
