# assignment1


Write a Dockerfile that:
• uses "ubuntu:18.04" as base image
• starts a Nagios Remote Plugin Executor (NRPE) daemon
• provides a NRPE command "check_mysql" (see check_mysql of monitoring-plugins) to
check the status of a database
• uses environment variables to modify the NRPE configuration & commands

Write a docker-compose.yaml that:
• starts a container of your image and a MariaDB image
• exposes the NRPE port






docker pull mariadb




![image](https://user-images.githubusercontent.com/33985509/60667167-215cdf00-9e69-11e9-8b14-df36a4a30131.png)


![image](https://user-images.githubusercontent.com/33985509/60667209-42253480-9e69-11e9-9bf7-408dbb175539.png)

