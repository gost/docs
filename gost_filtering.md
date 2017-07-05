# GOST filtering

Samples of supported filtering requests

## Logical Operators

- Equals

```
$ curl http://localhost:8080/v1.0/Datastream?$filter=name eq 'test1'
```

- Not Equals

```
$ curl http://localhost:8080/v1.0/Datastream?$filter=name ne 'test1'
```

- Lower than

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result lt 5
```

- Lower or equals than

```
$ http://localhost:8080/v1.0/Observations?$filter=result le 5
```

- Greater than

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result gt 5
```

- Greater or equals than

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result ge 5
```

- And

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result ge 5 and result le 15
```

- Or

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result lt 5 or result gt 15
```

- Not

```
$ curl http://localhost:8080/v1.0/Datastream?$filter=not endswith(Description,'milk')
```

## Arithmetic Operators

- Add

select observations where result equals 10 + 5 = 15

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result eq 10 add 5
```

- Sub

select observations where result equals 10 - 3 = 7

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result eq 10 sub 3
```

- Mul

select observations where result equals 10 * 3 = 30

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result eq 10 mul 3
```

- Div

select observations where result equals 21 / 3 = 7

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result eq 21 div 3
```

- Mod

select observations where result modulo 2 == 0

```
$ curl http://localhost:8080/v1.0/Observations?$filter=result mod 2 eq 0
```

## grouping Operators

```
$ curl http://localhost:8080/v1.0/Observations?$filter=(result sub 5) eq 45
```

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
$ curl http://localhost:8080/v1.0/Sensors?$filter=substringof(name, 'sensor') eq true
```

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
$ curl http://localhost:8080/v1.0/Sensors?$filter=tolower(name) eq 'sensor name 1'
```

- concat

```
$ curl http://localhost:8080/v1.0/Sensors?$filter=concat(name,'!') eq 'sensor name 1!'
```

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

- day 

```
$ curl http://localhost:8080/v1.0/Observations?$filter=day(phenomenonTime) eq 4
```

- hour

```
$ curl http://localhost:8080/v1.0/Observations?$filter=hour(phenomenonTime) eq 8
```

- minute

```
$ curl http://localhost:8080/v1.0/Observations?$filter=minute(phenomenonTime) eq 8
```

- second

```
$ curl http://localhost:8080/v1.0/Observations?$filter=second(phenomenonTime) eq 8.234
```

- month

```
$ curl http://localhost:8080/v1.0/Observations?$filter=month(phenomenonTime) eq 8
```

- month

```
$ curl http://localhost:8080/v1.0/Observations?$filter=year(phenomenonTime) eq 2017
```

- fractional seconds

```
$ curl http://localhost:8080/v1.0/Observations?$filter=fractionalseconds(phenomenonTime) eq 733
```

- now 

```
$ curl http://localhost:8080/v1.0/Observations?$filter=phenomenonTime gt now()
```

- mindatetime

```
$ curl http://localhost:8080/v1.0/Observations?$filter=phenomenonTime gt mindatetime()
```

- maxdatetime

```
$ curl http://localhost:8080/v1.0/Observations?$filter=phenomenonTime lt maxdatetime()
```

- totaloffsetminutes

```
$ curl http://localhost:8080/v1.0/Observations?$filter=totaloffsetminutes(phenomenonTime) eq 0
```

- date

```
$ curl http://localhost:8080/v1.0/Observations?$filter=date(phenomenonTime) eq 0
```

- time

```
$ curl http://localhost:8080/v1.0/Observations?$filter=time(phenomenonTime) eq 0
```

## Math functions

- round

```
$ curl http://localhost:8080/v1.0/Observations?$filter=round(result) eq 10
```

- floor

```
$ curl http://localhost:8080/v1.0/Observations?$filter=floor(result) eq 10
```

- floor

```
$ curl http://localhost:8080/v1.0/Observations?$filter=ceiling(result) eq 10
```

## Type functions

isOf

status: not implemented

