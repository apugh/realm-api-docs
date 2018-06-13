# Get Player 
**getPlayer** {playerId | playerName}

Returns basic player information

```js
[
  {
      "name": "RealmHero",
      "id": 123,
      "created_datetime": "3\/18\/2018 5:14:27 PM",
      "last_login_datetime": "6\/12\/2018 7:51:11 PM",      
      "level": 22
  }
]
```

# Get Player Stats
**getPlayerStats** {playerId | playerName}

Returns player stats for each match_queue_id (solo 474, duo 475, quad 476).
<b>average_placement and placements </b> are TBD based on query performance and will likely be that for only the past 30 days due to purging of the source table.

```js
[
  {      
      "id": 123,
      "match_queue": [{
          "name": "Solo",
          "id": 474,
          "games_played": 521,
          "kills": 371,
          "deaths": 479,
          "assists": 214,
          "playtime_secs": 52100,
          "wins": 2,
          "average_placement", 17,
          "placements": {1: 2, 2: 4, 3: 3, 4: 3, ... 26: 0, 27: 1}
      }]     
  }
]
```
