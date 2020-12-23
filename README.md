# docker-wordpress
Running a **WordPress** instance inside **Docker** container with Persistent storage. The setup can be run on our local machine as well as on cloud VM.

Docker is a CMS running on **LAMP stack** (Linux, Apache, MySQL, PHP). We will be running the full stack using docker-compose.

![alt text](https://github.com/samteck/docker-wordpress/blob/main/wordpress-docker.png)

We will use 3 docker images

### Wordpress
This image has Linux (alpine) as its base image and Apache and PHP are already installed.

Link: https://hub.docker.com/_/wordpress

### MySQL
This image will host our SQL server and store all of our posts, comments, configurations, etc.

Link: https://hub.docker.com/_/mysql

### phpMyAdmin
This is a tool used to access our MySQL database from web browser.

Link: https://hub.docker.com/r/phpmyadmin/phpmyadmin


We will use docker-compose to bring up these Docker containers. In addition to the 2 required docker images (Wordpress and MySQL) we will also be running phpMyAdmin to access our MySQL Database from the Browser.


#### Docker Volumes
Here we are using volume instead of bind mounts. Volumes are completely managed by docker. Volumes will be storing persistent and our data will be safe from container stop or restart. Plus Volumes can be shared among different Docker containers via volume drivers.

### Commands Used

#### Setting up docker (download from docker repo instead of linux repo)
- sudo apt update
- sudo apt install apt-transport-https ca-certificates curl software-properties-common
- curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
- sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
- sudo apt update
- apt-cache policy docker-ce
- sudo apt install docker-ce
- sudo systemctl status docker


#### Give use root permission (not have to use sudo every time )
- sudo usermod -aG docker ${USER}
- after this restart the machine or type 

#### Docker Compose

docker-compose up -d
docker-compose down

To Tear Down (all delete persistent volumes)
docker-compose down --volumes


##### Other useful docker commands

- docker container ls -a
- docker ps
- docker attach ID
To detach Ctrl+P CTRL+Q, if not able to detach run the below command and CTRL+C
- docker attach --sig-proxy=false ID
- docker exec -it ID /bin/bash

- docker volume ls
- docker volume inspect [volume]