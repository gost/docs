# GOST filtering

Samples of supported filtering requests

## String functions

- contains

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=contains(name,'temperature')
```

- startswith

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=startswith(name,'temp')
```

- endswith

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=endswith(name,'sensor')
```

- length

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=length(name) eq 18
```

- indexof

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=indexof(name, 'sensor') eq 0
```

- substringof

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=substringof('sensor', name) eq true
```

nb: gives http 500 now

- trim

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=trim(name) eq 'My Sensor'
```

- toupper

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=toupper(name) eq 'SENSOR NAME 1'
```

- tolower

```
$ http://localhost:8080/v1.0/Sensors?$filter=tolower(name) eq 'sensor name 1'
```

- concat

```
$ http://localhost:8080/v1.0/Sensors?$filter=concat(name,'!') eq 'sensor name 1!'
```

## Spatial

geo.within 

st_within 

geo.intersects 

st_intersects

## Date functions

not implemented

## Math functions

not implemented

## Type functions

not implemented

