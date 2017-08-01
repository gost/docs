## GOST Configuration

Default configuration file: config.yaml

server: <br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;name: GOST Server (name of the webserver)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;host: localhost (host of webserver, set to 0.0.0.0 if hosting on external machine)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port: 8080 (port of webserver)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;externalUri: http://localhost:8080/ (change to the uri where users can reach the service)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maxEntityResponse: 50 (Max entities to return if no $top and $skip is given, not implemented yet)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;indentedJson: true (return indented JSON, not implemented yet)<br />
database:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;host: localhost (location of PostGIS server)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port: 5432 (port of PostGIS database)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;user: postgres (PostGIS user)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;password: postgres (PostGIS password)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;database: gost (PostGIS database to use)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;schema: v1 (schema to use)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ssl: false (SSL enabled, not implemented yet)<br />
mqtt:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;enabled: true (enable MQTT)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;host: iot.eclipse.org (host of the MQTT broker)<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;port: 1883 (port of the MQTT broker)<br />

The following configuration parameters can be overruled 
from the following environment variables:

db: GOST_DB_HOST, GOST_DB_DATABASE, GOST_DB_PORT, GOST_DB_USER, GOST_DB_PASSWORD. 

mqtt: GOST_MQTT_HOST, GOST_MQTT_PORT

server: GOST_SERVER_HOST, GOST_SERVER_PORT, GOST_SERVER_EXTERNAL_URI

Example setting GOST environment variable on Windows:

```sh
set GOST_DB_HOST=192.168.40.10
```

Example setting GOST environment variable on Mac/Linux:

```sh
export GOST_DB_HOST=192.168.40.10
```

If you are using Docker the environment variables can be set in the docker-compose file. For example, change the external adress
via gost_server_external_uri: 

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



