# Preparing the Build Envioronment

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
