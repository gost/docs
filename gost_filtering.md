# GOST filtering

Samples of supported filtering requests

## Non-spatial

- contains: Sensors?$filter=contains(name, 'y s')

- startswith: Sensors?$filter=startswith(name, 'my')

- endswith: Sensors?$filter=endswith(name, 'sensor 3')

- length: Sensors?$filter=length(name) eq 13

- indexof: Sensors$filter=indexof(name, 'y sensor') eq 1

- substring: substringof('sensor', name) eq false

- trim

- toupper

- tolower

- concat

## Spatial

geo.within 

st_within 

geo.intersects 

st_intersects
