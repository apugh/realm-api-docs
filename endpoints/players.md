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
      "level": 22,
      "steam_id": "abc123"
  }
]
```

# Get Player Stats
**getPlayerStats** {playerId | playerName}

Returns player stats for each match_queue_id (solo 474, duo 475, quad 476).
<b>average_placement and placements </b> are TBD based on query performance and will likely be that for only the past 30 days due to purging of the source table.
This would aggregate the player/queue data (combining the different Profiles such as MaleTank, FemaleDamage, FemaleSupport, MaleUtility, MaleFlank, etc.).  If desired, that data can be broken out separately.

```js
[
  {      
      "id": 123,
      "match_queue": [{
          "name": "Solo",
          "id": 474,
          "profiles": [
              "MaleTank": {
                  "games_played": 521,
                  "kills_player": 371,
                  "kills_bot": 6,
                  "killing_spree_max": 5,
                  "deaths": 479,
                  "assists": 214,
                  "duration_secs": 52100,
                  "damage_player": 22019,
                  "damage_taken": 4379,
                  "damage_mitigated": 942,
                  "healing_player": 249.999985,
                  "healing_player_self": 663,
                  "wins": 2,
                  "losses": 519,
                  "wards_mines_placed": 1098,
                  "earned_xp": 157850,
                  "earned_tokens": 442,
                  },
              "FemaleSupport": {
                  "games_played": 231,
                  ...
              }
          ],
        "average_placement", 17,
        "placements": {1: 2, 2: 4, 3: 3, 4: 3, ... 26: 0, 27: 1}
        }]     
  }
]
```
