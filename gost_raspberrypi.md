# How to run GOST on Raspberry Pi

Warning: Raspberry Pi support for GOST is in experimental phase!

## Flash card

For running GOST we need to have a flash card with Docker installed.

One easy option is to use the <a href="https://blog.hypriot.com/">Hypriot</a> images, it comes with Docker tools installed.

Installation instructions:

- For Mac: https://blog.hypriot.com/getting-started-with-docker-and-mac-on-the-raspberry-pi/

- For Windows: https://blog.hypriot.com/getting-started-with-docker-and-windows-on-the-raspberry-pi/

- For Linux: https://blog.hypriot.com/getting-started-with-docker-and-linux-on-the-raspberry-pi/

Use the latest Hypriot image: https://github.com/hypriot/image-builder-rpi/releases/download/v1.5.0/hypriotos-rpi-v1.5.0.img.zip (29.06.2017)

After installation, you should be able to login on machine 'black-pearl' with 'pirate' as username, password 'hypriot'

```
$ ssh pirate@black-pearl
```

Now update the installation:

```
$ sudo apt-get update
$ sudo apt-get upgrade docker-hypriot docker-compose
```

## Install GOST

Execute the following commands to install GOST on the Raspberry Pi.

Note: downloading new images can take some time... So grab a coffee and relax while GOST is installing... 

```
$ curl https://raw.githubusercontent.com/gost/docker-compose/master/docker-compose-rpi.yml > docker-compose.yml
$ docker-compose up
```

System is ready when these kind of messages appear:

```
gost-db_1    | LOG:  MultiXact member wraparound protections are now enabled
gost-db_1    | LOG:  autovacuum launcher started
gost-db_1    | LOG:  database system is ready to accept connections
node-red_1   | 1 Sep 10:42:03 - [info] Dashboard version 2.2.1 started at /ui
node-red_1   | 1 Sep 10:42:04 - [info] Settings file  : /root/.node-red/settings.js
node-red_1   | 1 Sep 10:42:04 - [info] User directory : /root/.node-red
node-red_1   | 1 Sep 10:42:04 - [info] Flows file     : /root/.node-red/flows_d25030c9374a.json
node-red_1   | 1 Sep 10:42:04 - [info] Creating new flow file
node-red_1   | 1 Sep 10:42:04 - [info] Starting flows
node-red_1   | 1 Sep 10:42:04 - [info] Started flows
node-red_1   | 1 Sep 10:42:04 - [info] Server now running at http://127.0.0.1:1880/
```

## Check installation

- Dashboard: In browser go to http://black-pearl:8080

- Node-RED: In browser go to http://black-pearl:1880

If the dashboard is working, you can continue with the <a href="https://github.com/gost/workshops/blob/master/2017_foss4g_boston/3_configuration.md">Workshop exercises</a> to configure GOST. Make sure to replace 'localhost' with 'black-pearl' in the exercises. 
