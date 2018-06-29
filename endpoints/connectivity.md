# Create Session
**/createsession**[ResponseFormat]/{developerId}/{signature}/{timestamp}

A required step to Authenticate the developerId/signature for further API use.  
- [ResponseFormat] = "json" or "xml"
- {timestamp} is UTC time

```js
{ 
    "session_id": "96AD8C1A916E461686240EE30D4E67EF",
    "timestamp": "6\/29\/2018 2:17:34 PM",
    "ret_msg": "Approved"
}
```


# Test Session
**/testsession**[ResponseFormat]/{developerId}/{signature}/{session}/{timestamp}

A means of validating that a session is established.

```js
 returns a string ...
 Example: "This was a successful Test Session, blah, blah, blah ..."
```


# Ping
**/testsession**[ResponseFormat]/{developerId}

A quick way of validating availabiltiy of the Hi-Rez API.

```js
 returns a string ...
 Example: "RealmAPI (ver 1.0.0.0) [PATCH - 0.3.225.0] - Ping successful. Server Date:6\/29\/2018 3:10:25 PM"
```


# Get Data Used
**/getdataused**[ResponseFormat]/{developerId}/{signature}/{session}/{timestamp}

Returns API Developer daily usage limits and the current status against those limits.

```js
{ 
    "active_sessions": 3,
    "concurrent_sessions": 500,
    "request_daily_limit": 7500,
	"session_cap": 2000,
	"session_time_limit": 30,
	"total_requests_today": 1032,
	"total_sessions_today": 49,
	"ret_msg": null
}
```


# Get Hi-Rez Server Status
**/gethirezserverstatus**[ResponseFormat]/{developerId}/{signature}/{session}/{timestamp}

Returns UP/DOWN status for the primary game/platform environments.  Data is cached once a minute.

```js
{    
	"entry_datetime": "2018-06-29 14:31:35.315",
	"status": "UP",
	"version": "0.3.225.0",
	"ret_msg": null
}
```


# Get Patch Info
**/getpatchinfo**[ResponseFormat]/{developerId}/{signature}/{session}/{timestamp}

Returns information about current deployed patch. Currently, this information only includes patch version.

```js
{    	
	"version": "0.3.225.0",
	"version_id": 196833,
	"version_code":  "OB3",
	"ret_msg": null
}
```
