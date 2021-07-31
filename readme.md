# **Ubuntu Basic Docker Setup**

Several web pages were used as resources to get this to work:
- https://docs.docker.com/install/linux/docker-ce/ubuntu/
- https://docs.docker.com/develop/develop-images/baseimages/
- https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04

These steps have worked with both Ubuntu 18.04 and 20.04.  Comments are in parenthesis.

------------


apt-get update

apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -

apt-key fingerprint 0EBFCD88

add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

apt-get install docker-ce docker-ce-cli containerd.io

docker run hello-world (ensures you can reach the Docker Hub)

<br><br>


## Create CentOs Docker Container on your Ubuntu System

------------

This will create a CentOS container and install nodejs within the container.

docker search centos

docker pull centos (get latest Centos image from Docker Hub)

docker images (see available images you downloaded)

docker run -it centos (run container, you will be inside the container once it starts and prompt has container id)

yum clean all
yum install nodejs
node -v

<br><br>

## Open Another Terminal on your System/Desktop

------------

node -v (your desktop will show nodejs is not installed, unless you actually installed it previously on your desktop, because the above steps installed it within the container)

docker ps -a (see all containers id and name, e.g. my CentOS container is called laughing_volhard)
(laughing_volhard is the default container name, I did not create that name)
docker ps -l
docker start 3d09efb1f56f (the number is the container id from docker ps command) or
docker start laughing_volhard
docker attach laughing_volhard (attach to a running container if you have mulitple running containers)
docker stop laughing_volhard
docker rm laughing_volhard (delete container)

<br><br>

## Allow User to run Docker

------------

usermod -aG docker default (allow user named default to run docker)

<br><br>

## Remove Docker

------------

apt-get purge docker-ce; rm -rf /var/lib/docker (remove docker)
