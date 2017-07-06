# How to run SensorThings GOST on Raspberry Pi

## Version

Check version of your Raspberry Pi:

This document is written for Raspian Jessie.

```
pi@raspberrypi:~ $ lsb_release -a
No LSB modules are available.
Distributor ID:	Raspbian
Description:	Raspbian GNU/Linux 8.0 (jessie)
Release:	8.0
Codename:	jessie
pi@raspberrypi:~ $ 
```

## Install Docker

```
pi@raspberrypi:~ $ curl -sSL get.docker.com | sh
```

For safety, reboot the Raspberrypi.

Check installation with:

```
pi@raspberrypi:~ $ sudo docker info
```
Now install docker-compose:

```
pi@raspberrypi:~ $ sudo apt-get install python-pip

pi@raspberrypi:~ $ sudo pip install docker-compose

```

## Install GOST

Note: downloading new images can take some time... 

```
pi@raspberrypi:~ $ wget https://raw.githubusercontent.com/gost/docker-compose/master/docker-compose-rpi.yml
pi@raspberrypi:~ $ sudo docker-compose -f docker-compose-rpi.yml up
```

## Check installation

- Dashboard: In browser go to http://raspberrypi:8080

If dashboard is working, you can continue with the <a href="https://github.com/gost/workshops/blob/master/2_configuration.md">Workshop exercises</a> to configure GOST. Make sure to replace 'localhost' with 'raspberrypi' in the exercises. 
