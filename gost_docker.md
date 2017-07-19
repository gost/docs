# GOST Docker support

For getting GOST to work in Docker there are three images available on Docker Hub

[Server](https://hub.docker.com/r/geodan/gost/) containing the GOST server  
[gost-db](https://hub.docker.com/r/geodan/gost-db/) containing an already configured postgis database  
[gost-dashboard](https://hub.docker.com/r/geodan/gost-dashboard/) containing nginx and the GOST dashboard  

For more information about the containers check the projects on github: [server](https://github.com/gost/server) - [gost-db](https://github.com/gost/gost-db) - [gost-dashboard](https://github.com/gost/dashboard)

The docker images can run separately, or running in a combined way using the Dockercompose file.

## Running GOST with Docker-compose
Our default docker-compose file comes with a MQTT server (Mosquitto) and Node-RED, a handy tool that can be used with GOST.  
Use the tag latest for the latest development version, otherwise use a tag like '0.5' for more stable versions.   

Running (unstable) latest build of GOST:
```
$ wget https://raw.githubusercontent.com/gost/docker-compose/master/docker-compose.yml 
$ docker-compose up
```
Running (stable) 0.5 build of GOST
```
$ wget https://raw.githubusercontent.com/gost/docker-compose/master/docker-compose-0.5.yml 
$ docker-compose -f docker-compose-0.5.yml up
```

## Running GOST with docker run
- Start geodan/gost-db which creates an user postgres with password postgres and initialises a database named gost</br>
- Start geodan/gost and set info to connect to gost-db, gost will be available at http://localhost:8080/v1.0</br>
- Start geodan/gost-dashboard and link gost to use GOST trough nginx, gost + dashboard available at http://localhost:8081

```
$ docker run -d -p 5432:5432 -e POSTGRES_DB=gost -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres --name gost-db geodan/gost-db</br>
$ docker run -d -p 8080:8080 --link gost-db:gost-db -e gost_db_host=gost-db -e gost_db_user=postgres -e gost_db_password=postgres --name gost geodan/gost</br>
$ docker run -d -p 8081:8080 --link gost:gost --name gost-dashboard geodan/gost-dashboard		
```

For making connection to external database use environmental variables gost_db_host, gost_db_port, gost_db_user, gost_db_password
```
$ docker run -d -p 8080:8080 -t -e gost_db_host=192.168.40.10 -e gost_db_database=gost --name gost geodan/gost
```

## Building GOST service

```
$ git clone https://github.com/Geodan/gost.git

$ cd src/github.com/geodan/gost/src

$ docker build -t geodan/gost:latest .

$ docker push geodan/gost

```
## Building GOST service Raspberrypi

note: building the Raspberry Pi image must be done on a Raspberry Pi :-(, otherwise errors will occur.

```
pi@raspberrypi:~/dev/go/src/github.com/Geodan/gost $ sudo docker build -f Dockerfile-rpi -t geodan/rpi-gost .

pi@raspberrypi:~/dev/go/src/github.com/Geodan/gost $ sudo docker push geodan/rpi-gost
```

## Removing database

The data of the Postgis is stored on a Docker volume. If you want to remove the data use commands like:

```
$ docker volume rm dockercompose_postgis

Error response from daemon: unable to remove volume: remove dockercompose_postgis: volume is in use - [e31cec73654b8c19381bb1fa3b3f9f2f3dd710af3464d3321c19c54564e94e5f]

$ docker rm e31

$ docker volume rm dockercompose_postgis
```
