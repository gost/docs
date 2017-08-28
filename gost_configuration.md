## GOST server configuration using yaml

GOST server uses a default config.yaml configuration file, you can edit this file or specify your own file by running gost with the -config flag. 

```sh
./gost -config myconfig.yaml
```

**default config.yaml**  
server: <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: GOST Server (name of the webserver)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;host: (host of webserver, set to 0.0.0.0 if hosting on external machine)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port: 8080 (port of webserver)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;externalUri: http://localhost:8080/ (change to the uri where users can reach the service)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxEntityResponse: 50 (max entities to return if no $top and $skip is given)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;indentedJson: true (return indented JSON)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;https: false (ron GOST on HTTPS true/false)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;httpsCert: (location of https cert file)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;httpsKey: (location of https key file)<br />
database:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;host: localhost (location of PostGIS server)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port: 5432 (port of PostGIS database)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;user: postgres (PostGIS user)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;password: postgres (PostGIS password)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;database: gost (PostGIS database to use)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;schema: v1 (schema to use)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ssl: false (SSL enabled, not implemented yet)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxIdleConns: 30 (maximum idle connections)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxOpenConns: 100 (maximum open connections)<br />
mqtt:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;enabled: true (true/false to enable/disable MQTT)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;host: localhost (host of the MQTT broker)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port: 1883 (port of the MQTT broker)<br />
logger:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fileName: gost (filename to log to, leave blank to log to stdout)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;verbose: true (true for logging debug and up, false to log from warn and up)<br />

##  GOST server configuration using environment variables
The config.yaml parameters can be overruled with the following environment variables, check default config.yaml above for the variable descriptions.

**Gost server configuration**  
GOST_SERVER_NAME  
GOST_SERVER_HOST  
GOST_SERVER_PORT  
GOST_SERVER_EXTERNAL_URI  
GOST_SERVER_MAX_ENTITIES  
GOST_SERVER_INDENT_JSON  
GOST_SERVER_HTTPS  
GOST_SERVER_HTTPS_KEY  
GOST_SERVER_HTTPS_CERT  

**Gost server database connection**  
GOST_DB_HOST  
GOST_DB_SCHEMA  
GOST_DB_DATABASE  
GOST_DB_PORT  
GOST_DB_USER  
GOST_DB_PASSWORD  
GOST_DB_MAX_IDLE_CONS  
GOST_DB_MAX_OPEN_CONS  

**Gost server mqtt connection**  
GOST_MQTT_ENABLED  
GOST_MQTT_HOST  
GOST_MQTT_PORT
GOST_MQTT_SSL_ENABLED  

**Gost logging**  
GOST_LOG_FILENAME  
GOST_LOG_VERBOSE_FLAG   

**Example setting GOST environment variable on Windows**

```sh
set GOST_DB_HOST=192.168.40.10
```

**Example setting GOST environment variable on Mac/Linux**

```sh
export GOST_DB_HOST=192.168.40.10
```

**Example setting GOST environment variable in docker-compose.yml**

```
    gost:
        image: geodan/gost
        depends_on:
            - mosquitto
            - gost-db
        environment:
            GOST_DB_HOST: gost-db
            GOST_MQTT_HOST: mosquitto
            GOST_SERVER_EXTERNAL_URI: http://fancy_server:8181
```

**Example setting GOST environment variable in docker run**

```
    $ docker run -d -p 8080:8080 -t -e GOST_DB_HOST=192.168.40.10 -e GOST_DB_DATABASE=gost
```
