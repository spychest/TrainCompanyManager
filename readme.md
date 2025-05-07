# Train Company Manager
## Introduction
From 2016 to 2019 I worked in a company which repair, service and upgrade freight cars.
Now I'm a web developper and I want to create an enterprise resource planning (E.R.P.) web application.
## Goals
The web application will have to cover these departments:
- Human resources
- Work planing
- Stock management
- Client management
- Data analysis
- Billing service
- Internal maintenance
- Quality service
## Installation
### Pre-require
To run this project you'll need a linux server. You'll also need to install some software
#### Git
```shell
sudo apt install git-all
```
#### Docker
```shell
# Add Docker's official GPG key:
sudo apt-get update 
&& apt-get install ca-certificates curl
&& install -m 0755 -d /etc/apt/keyrings
&& curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
&& chmod a+r /etc/apt/keyrings/docker.asc
&& echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
&& tee /etc/apt/sources.list.d/docker.list > /dev/null
&& apt-get update
```
```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
#### Docker-compose
```shell
sudo apt-get update
&& apt-get install docker-compose-plugin
```
Then you're ready to continue.
### Clone the project
```shell
cd /var/www &&
sudo git clone git@github.com:spychest/TrainCompanyManager.git
```
### Setting the project
Go to the cloned project
```shell
cd TrainCompanyManager
```
Then edit the `.env` file to use your own password, names, and value for variables.
```shell
sudo nano .env
```
### Launch the project
Then launch the project and install the dependencies
```shell
sudo docker-compose up -d
&& docker-compose exec train-company-manager-php-fpm composer install
&& docker-compose exec train-company-manager-php-fpm php bin/console d:d:c
&& docker-compose exec train-company-manager-php-fpm php bin/console d:m:m --no-interaction
&& docker-compose exec train-company-manager-php-fpm php bin/console ca:cl
```
Then go on http://localhost:80
