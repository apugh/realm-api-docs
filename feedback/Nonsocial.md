# API Architecture Feedback

## Remove / rework the ``GetDataUsed ()`` Method
It's like the stachu540 [said](https://github.com/apugh/realm-api-proposal/blob/master/feedback/dstaszewski.md#api-architecture-feedback)...
- As it will be removed, return the ``Header`` containing the info about the data used for every method request:

``stachu540`` example:
```yaml
Headers:
  X-Rate-Limit: 7500
  X-Rate-Limit-Remaining: 7499 # after first query will responde one less than X-Rate-Limit
  X-Rate-Limit-Reset: 1529091932 # unix timestamp in UTC (2018-06-15T19:45:32+00:00)
```

- It can be something like too:

This Headers will just be returned when used ``CreateSession ()``
```yaml
Headers:
  Request-Limit-Daily: 7500
  Session-Cap: 500
  Session-Concurrent-Limit: 50
  Session-Time-Limit: 15
```

This Headers will be returned for every method request
```yaml
Headers:
  Request-Requests-Today: 51
  Request-Sessions-Today: 29
  Session-Active: 9
```

- If it be refused, remove the ``GetDataUsed ()`` being counted as Request (Actually, every ``GetDataUsed ()`` request will decrease the requests remaining by one)

## Remove the [ResponseFormat] from the ``/Ping[ResponseFormat]`` Method
- Why we need to Request as JSON, if what will be returned is Text Plain, not JSON? (I know that ``/PingXML`` will return a XML-like, but...)

**Requesting as JSON**: http://api.realmroyale.com/realmapi.svc/PingJSON
```
"RealmAPI (ver 1.0.0.0) [PATCH - 0.3.225.0] - Ping successful. Server Date:6/28/2018 1:26:12 AM"
```

**Requesting as XML**: http://api.realmroyale.com/realmapi.svc/PingXML
```xml
<string>RealmAPI (ver 1.0.0.0) [PATCH - 0.3.225.0] - Ping successful. Server Date:6/30/2018 9:43:32 PM</string>"
```

## Move the Official Documentation API to Github
- One repository for each API endpoint (Smite, Paladins and Realm Royale)
- The repository will contains: The ReadMe.md with contain an intro / short description about the API and a "shortcut" for the Wiki, and code samples.
- All Documentation will be found on the Wiki. (I can help here, if requested / needed!)

## A full list about the ret_msg messages
I've wrote the ret_msg message that I've catched [here](https://github.com/apugh/realm-api-proposal/wiki/Getting-Started#ret_msg), but probably it's not all.

# Realm Royale Endpoint Feedback

## Remove the XML support.
I saw no one using XML, JSON is better...

If it's accepted, rework all methods to:
- ``/CreateSession/{devID}/{signature}/{timestamp}``
- ``/GetDataUsed/{devID}/{signature}/{session_Id}/{timestamp}``
- ``/GetHiRezServerStatus/{devID}/{signature}/{session}/{timestamp}``
- ``/GetPatchInfo/{devID}/{signature}/{session}/{timestamp}``
- ``/Ping``
- ``/TestSession/{devId}/{signature}/{session_id}/{timestamp}``
- ``/GetLeaderboard/{devId}/{signature}/{session_id}/{timestamp}/{queue}/{ranking_criteria}``
- ``/GetMatchDetails/{devId}/{signature}/{session_id}/{timestamp}/{matchId}``
- ``/GetMatchIDsByQueue/{devId}/{signature}/{session_id}/{timestamp}/{queue}/{date}/{hour}``
- ``/GetPlayer/{devId}/{signature}/{session_id}/{timestamp}/{player}/{platform}``
- ``/GetPlayerMatchHistory/{devId}/{signature}/{session_id}/{timestamp}/{player}``
- ``/GetPlayerStats/{devId}/{signature}/{session_id}/{timestamp}/{player}``
- ``/GetPlayerStatus/{devId}/{signature}/{session_id}/{timestamp}/{player}``

## Remove the duplicate / "useless" data:
- Have a lot information that really don't need to be returned (Extra data)... And we can filter it now! (Ofc there more extra data, but we can start here)

```diff
+ { "name": "RealmHero",
+ "id": 123,
+ "matches": [{
+ "match_id": 526153,
+ "match_datetime": "6\/14\/2018 5:14:27 PM",
+ "match_duration_secs": 1243,
+ "map_game": "LIVE Royale Map",
- "match_queue_name": "Duo",
+ "match_queue_id": 475,
- "class_name": "Mage",
+ "class_id": 2285,
+ "team_id": 123828,
+ "region": "Brazil"}]
+ }

##### Full-explaination:
- Remove "queue" / queue name from GetLeaderboard ()
P.S: How it returned as array, maybe it can be removed too: "rank" (The array index / array length can be used to determine who is the rank 1, 2, 3, etc ....)

- Remove "queue" / queue name from GetMatchDetails ()

- Remove "match_queue_name", "class_name" from GetPlayerMatchHistory ()

- Remove "match_queue_name", "class_name" from GetPlayerStats ()

- "status" from GetPlayerStatus ()
```
