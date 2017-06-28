# GOST filtering

Samples of supported filtering requests

## Non-spatial

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
$ curl http://localhost:8080/v1.0/Sensors?$indexof(name, 'sensor') eq 0
```

- substring

```
$ curl http://localhost:8080/v1.0/Sensors?$substringof('sensor', name) eq false
```

- trim

- toupper

- tolower

- concat

## Spatial

geo.within 

st_within 

geo.intersects 

st_intersects
