# Buiding the Latest Docker Image 

Pick the latest deb package from Bitbucket download page (https://bitbucket.org/jsuto/piler/downloads/) and use it as the PACKAGE build argument. As of writing  this guide the latest version is `piler_1.3.7-bionic-94c54a0_amd64.deb`.

Run the following command to download it.

```
wget https://bitbucket.org/jsuto/piler/downloads/piler_1.3.7-bionic-94c54a0_amd64.deb
```
Run the following comand to build the docker image. 

```
docker build --build-arg PACKAGE=${PACKAGE} --build-arg MYSQL_PILER_PASSWORD=${MYSQL_PILER_PASSWORD} --buid-arg MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD} -t cghub/mailpiler .
```

# How to Run the Image

Set the PILER_HOST env variable to match your hostname, 

```
docker run -d --name mpiler -p 25:25 -p 80:80 -e PILER_HOST=mpiler.yourdomain.com cghub/mailpiler
```
# Running with docker-compose

## Clone the Repository

First clone the repository:

```
git clone https://github.com/enterpriselinux/mailpiler.git /opt/mpiler
```

Change the PILER_HOST=mpiler.yourdomain.com to match with your hostname. Run the command:

```
cd /opt/mpiler
docker-compose up -d
```
# Observing Mailpiler SMTP Logs

Run the following command:

```
docker-compose exec mpiler tail -f /var/log/syslog
```



