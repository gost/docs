# SensorThings Deep Insert API

With the Deep Insert functionality of SensorThings API its possible to create multiple entities in one request.

- Create Datastream with ObservedProperty and Sensor for Thing.@iot_id=1

```
$ curl -X POST -H "content-type:application/json" http://localhost:8080/v1.0/Datastreams

body:

{
    "name": "DS3",
    "unitOfMeasurement": {
            "name": "Celsius",
            "symbol": "C",
            "definition": "http://www.qudt.org/qudt/owl/1.0.0/unit/Instances.html#Celsius"
        },
        "description": "Temperature measurement",
        "observationType": "http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement",
        "ObservedProperty": {
            "name": "Temperature",
            "definition": "http://www.qudt.org/qudt/owl/1.0.0/quantity/Instances.html#Temperature",
            "description": "Temperature of the camping site"
        },
        "Sensor": {
            "name": "My Sensor",
            "description": "SensorUp Tempomatic 1000-b",
            "encodingType": "application/pdf",
            "metadata": "Calibration date:  Jan 11, 2015"
        },
         "Thing": {"@iot.id": "1"}
}

```

- Create Observation with FeatureOfInterest

```
$ curl -X POST  -H "content-type:application/json" http://localhost:8080/v1.0/Observations

body:

{
  "phenomenonTime": "2015-04-13T00:00:00+02:00",
  "result" : 38,
  "Datastream":{"@iot.id":"2"},
  "FeatureOfInterest": {
    "name": "Awesome FOI",
    "description": "Underground Air Quality in NYC train tunnels",
    "encodingType": "application/vnd.geo+json",
    "feature": {
        "coordinates": [51.08386,-114.13036],
        "type": "Point"
      }
  }
}
```
