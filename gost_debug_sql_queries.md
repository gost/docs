# GOST Debug SQL Queries

In this document a method to quickly debug GOST sql queries is described. 

## Enable GOST verbose logging

Add the environment variable 'GOST_LOG_VERBOSE_FLAG' with value '1' to the GOST section in docker-compose.yml:

```
environment:
    GOST_LOG_VERBOSE_FLAG: 1
```

## Get SQL database access

Edit docker-compose.yml and open the database port by adding to the GOST-DB section:

```
ports:
    - "5432:5432"
```

And start GOST

```
$ docker-compose up
```

Now open SQL client of choice (PGAdmin/PSQL/DBeaver) and make a database connection on port 5432.

```
$ psql -U postgres
```

Connect to GOST database:

```
postgres=# \connect gost
```

Sample test query (to get the number of things in the database):

```
gost=# select count(*) from v1.thing;
 count
---------
    1
(1 row)
```

## Debugging

Start GOST without detached mode

```
$ docker-compose up
```

Execute queries in a browser, for example go to 'http://localhost:8080/v1.0/Things'

In the console you'll see SQL queries and timings:

```
gost_1       | time="2020-01-20T10:13:49Z" level=debug msg="GET start: /v1.0/Things" package=gost.server.http
gost_1       | time="2020-01-20T10:13:49Z" level=debug msg="constructing select query" elapsed="29.2µs" package=gost.server.database.postgis
gost_1       | time="2020-01-20T10:13:49Z" level=debug msg="execute select query: SELECT A_thing.thing_id AS A_thing_id, A_thing.thing_name AS A_thing_name, A_thing.thing_description AS A_thing_description, A_thing.thing_properties AS A_thing_properties FROM (SELECT thing.id AS thing_id, thing.name AS thing_name, thing.description AS thing_description, thing.properties AS thing_properties FROM v1.thing  ORDER BY thing_id DESC LIMIT 21 OFFSET 0) AS A_thing " elapsed=9.783ms package=gost.server.database.postgis
gost_1       | time="2020-01-20T10:13:49Z" level=debug msg="GET done: /v1.0/Things" elapsed=10.1285ms package=gost.server.http
```

Or use the 'docker logs' statement on the running GOST container to see the same information.

Next the query can be analyzed in SQL client by using 'explain analyze':

```
gost=# explain analyze SELECT A_thing.thing_id AS A_thing_id, A_thing.thing_name AS A_thing_name, A_thing.thing_description AS A_thing_description, A_thing.thing_properties AS A_thing_properties FROM (SELECT thing.id AS thing_id, thing.name AS thing_name, thing.description AS thing_description, thing.properties AS thing_properties FROM v1.thing  ORDER BY thing_id DESC LIMIT 21 OFFSET 0) AS A_thing;
                                                   QUERY PLAN
----------------------------------------------------------------------------------------------------------------
 Limit  (cost=12.59..12.64 rows=21 width=1072) (actual time=0.022..0.024 rows=1 loops=1)
   ->  Sort  (cost=12.59..12.76 rows=70 width=1072) (actual time=0.020..0.021 rows=1 loops=1)
         Sort Key: thing.id DESC
         Sort Method: quicksort  Memory: 25kB
         ->  Seq Scan on thing  (cost=0.00..10.70 rows=70 width=1072) (actual time=0.004..0.005 rows=1 loops=1)
 Planning time: 0.223 ms
 Execution time: 0.057 ms
(7 rows)
```


