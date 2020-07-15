# Preparing the Build Envioronment

Run the follwing command to create `.buildrc` file.

```
bash env.sh
```

# Buiding the Latest Docker Image 

Pick the latest deb package from Bitbucket download page (https://bitbucket.org/jsuto/piler/downloads/)
and use it as the PACKAGE build argument, for example.

```
docker build --build-arg PACKAGE=piler_1.3.6~bionic-65cc7eb_amd64.deb -t cghub/mailpiler .
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



