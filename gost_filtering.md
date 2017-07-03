# GOST filtering

Samples of supported filtering requests

## Logical Operators

- Equals

```
$ http://localhost:8080/v1.0/Datastream?$filter=name eq 'test1'
```

todo: Ne, Gt, Lt, Le, Ge, And, Or, Not

## Arithmetic Operators

todo: Add, Sub, Mul, Div, Mod

## grouping Operators

todo: ()


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

status: implemented

## Geospatial functions

geo.distance 

geo.length

geo.intersects

geo.within 

status: Not implemented

## Spatial Relationship Functions

st_within 

st_intersects

st_equals

st_disjoint

st_touches

st_overlaps

st_crosses

st_contains

st_relate

status: not implemented

## Date functions

day, hour, minute, second, month, year

status: not implemented

## Math functions

round, floor, ceiling

status: not implemented

## Type functions

isOf

status: not implemented

