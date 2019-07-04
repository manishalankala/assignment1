# Assignment1


Write a Dockerfile that:

• uses "ubuntu:18.04" as base image

• starts a Nagios Remote Plugin Executor (NRPE) daemon

• provides a NRPE command "check_mysql" (see check_mysql of monitoring-plugins) to
check the status of a database

• uses environment variables to modify the NRPE configuration & commands

Write a docker-compose.yaml that:

• starts a container of your image and a MariaDB image

• exposes the NRPE port






Instance name : jm

Instance ip : 10.128.0.7

Instance type : Centos



Start by updating your system packages and install the required dependencies:

sudo yum update




Now that the Docker repository is enabled, install the latest version of Docker CE (Community Edition) 

sudo yum install docker-ce



Once the Docker package is installed, start the Docker daemon and enable it to automatically start at boot time

sudo systemctl start docker

sudo systemctl enable docker

sudo systemctl status docker



![image](https://user-images.githubusercontent.com/33985509/60667167-215cdf00-9e69-11e9-8b14-df36a4a30131.png)


![image](https://user-images.githubusercontent.com/33985509/60667209-42253480-9e69-11e9-9bf7-408dbb175539.png)





Executing the Docker Command Without Sudo

sudo usermod -aG docker $USER





we can list the images with

docker image ls



Created folder

mkdir nrpe

in nrpe created a Dockerfile

vi Dockerfile

Below mentioned command 

# Docker File

```bash
FROM ubuntu:18.04

# Environment Variable
ENV NRPE_SERVER '192.181.1.0'
ENV NRPE_COMMAND ''

## Installing NRPE services
RUN apt-get update && apt-get install -y \

nagios-nrpe-server \

nagios-plugins \

# Install the plugin of mysql_check

## Adding allowed host entry for NRPE server/configuration
#RUN sed -i "/allowed_hosts/s/[^=]*\(.*\)$/allowed_hosts=\1, ${NRPE_SERVER}/"

## Restarting NRPE 
#RUN sudo /etc/init.d/nagios-nrpe-server restart


## Run the mysql_check
RUN /usr/lib/nagios/plugins/check_mysql -H 10.128.0.7 -p my-secret-pw

```


![image](https://user-images.githubusercontent.com/33985509/60676039-24ae9580-9e7e-11e9-9da1-5dda8377ea56.png)
