## GOST and security

The SensorThings API does not define specific security capabilities, security aspects should be handled
in a different application layer (see http://docs.opengeospatial.org/is/15-078r6/15-078r6.html#21).

## Limit write access
One common usecase is to limit write access to the SensorThings API. By configuring a proxy server like Apache2 or 
NGINX this can be achieved.

Example configuration for Apache2:

```
<Location /gost/v1.0/>
		<Limit POST PUT DELETE PATCH>
			AuthType Basic
			AuthName "GOST Writer"
			AuthUserFile "/etc/apache2/thepwfile"
			Require user gost
		</Limit>
	</Location>
```

And for Dashboard:

```
<Location "/gost/Dashboard/">
		AuthType Basic
		AuthName "GOST Writer"
		AuthUserFile "/etc/apache2/thepwfile"
		Require user gost
	</Location>
  ```
  
## CORS

Another common usecase is to support CORS requests. See https://github.com/gost/dashboard/blob/master/default.conf for an example of configuring CORS in NGINX.

CORS functionality can be tested from within Chrome using the following script on a different domain:

```
var http = new XMLHttpRequest();
var url = "http://localhost:8080/v1.0/Things";
var params = JSON.stringify({
   "description": "my thermometer",
   "name":"BertThermometer",
   "properties": {
       "organisation": "Geodan",
       "owner": "Bert"
   }
});
http.open("POST", url, true);

//Send the proper header information along with the request
http.setRequestHeader("Content-type", "application/json");

http.onreadystatechange = function() {//Call a function when the state changes.
   if(http.readyState == 4 && http.status == 201) {
       alert(http.responseText);
   }
}
http.send(params);
```

