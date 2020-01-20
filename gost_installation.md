
### GOST installation 

GOST can be installed in several ways, but the recommended method is using Docker tooling.

### Install with Docker

Sample script for complete installation (Docker + Docker-compose + GOST) on Ubuntu 16.04:

```
// Step 1] Install Docker

// docker repository
$ sudo apt-get update
$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

// install docker
$ sudo apt-get update
$ sudo apt-get install docker-ce

// install docker-compose
$ sudo apt install docker-compose

Test:
$ sudo docker run hello-world

Step 2]  GOST installatie

$ mkdir /gost/docker-compose/latest
$ cd gost/docker-compose/latest
$ wget https://raw.githubusercontent.com/gost/docker-compose/master/docker-compose.yml 
$ sudo docker-compose up -d

test:
$ curl http://localhost:8080/v1.0
```

## GOST testcase after installation: 

In browser open http://localhost:8080/v1.0 to test if the server is running

In browser op http://localhost:8080 to test if the dashboard is working
