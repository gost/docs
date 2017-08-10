# GOST FAQ

## SensorThings

Q: What are possible values for Sensor - EncodingType ?

A: 'application/pdf' and 'http://www.opengis.net/doc/IS/SensorML/2.0'

Q: What are possible values for Datastream - ObservationType

A: 

| O&M 2.0                | Value Code Value (observationType names)                                     | Content of result |
|------------------------|------------------------------------------------------------------------------|-------------------|
| OM_CategoryObservation | http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_CategoryObservation | URI               |
| OM_CountObservation    | http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_CountObservation    | integer           |
| OM_Measurement         | http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement         | double            |
| OM_Observation         | http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Observation         | Any               |
| OM_TruthObservation    | http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_TruthObservation    | boolean           |

Q: Whats the difference between Observation.ResultTime and Observation.PhenomenonTime?

A: 

Observation.ResultTime: The time of the Observation's result was generated.

Observation.PhenomenonTime: The time instant or period of when the Observation happen

## Docker

q: How to delete all data and start over?

A: For deleting the all stored data the Docker volumes has to be deleted. 
Warning: this deletes all information stored in GOST, Database and Node-RED.

```
$ docker-compose down -v
$ docker-compose up
```

And a new clean database will be there.


