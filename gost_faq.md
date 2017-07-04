# GOST FAQ

## Docker

q: How to delete all data and start over?

A: For deleting the all stored data the Docker volumes has to be deleted. 
Warning: this deletes all information stored in GOST, Database and Node-RED.

```
$ docker-compose down -v
$ docker-compose up
```

And a new clean database will be there.


