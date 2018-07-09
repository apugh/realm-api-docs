# Get Player 
**getPlayer** [{playerId}|{playerName}]/{"hirez"}]  | [{steamId}/{"steam"}]

Returns basic player information

```js
{
    "name": "RealmHero",
    "id": 123,
    "created_datetime": "3\/18\/2018 5:14:27 PM",
    "last_login_datetime": "6\/12\/2018 7:51:11 PM",      
    "level": 22,
    "steam_id": 76561198199559770,
    "region": "Europe"
}
```

# Get Player Stats
**getPlayerStats** {playerId}

Returns player stats for each [match_queue_id (solo 474, duo 475, quad 476), class (Warrior, Hunter, Mage, Engineer, Assassin)] combination. 
<b>average_placement and placements</b> are TBD based on query performance and will likely be that for only the past 30 days due to purging of the source table.

```js
{      
  "id": 123,
  "aggregate_stats": {         
      "games_played": 2521,
      "kills_player": 1371,
      "kills_bot": 46,
      "killing_spree_max": 25,
      "deaths": 2479,
      "assists": 1214,
      "duration_secs": 5210000,
      "damage_player": 220190,
      "damage_done_in_hand": 210932,
      "damage_taken": 43790,
      "damage_mitigated": 5942,
      "healing_player": 249.999985,
      "healing_player_self": 6635,
      "wins": 8,
      "losses": 1519,
      "wards_mines_placed": 11098,
      "earned_xp": 1575850,
      "earned_tokens": 1442,
      "average_placement": 23,
      "placements": {"1": 8, "2": 7, "3": 13, "4": 12, "... 28": 0, "29": 3}
  },
  "queue_class_stats": [{
      "match_queue_name": "Solo",
      "match_queue_id": 474,
      "class_name": "Warrior",
      "class_id": 2594,
      "stats": {
           "games_played": 521,
           "kills_player": 371,
           "kills_bot": 6,
           "killing_spree_max": 5,
           "deaths": 479,
           "assists": 214,
           "duration_secs": 52100,
           "damage_player": 22019,
           "damage_done_in_hand": 21832,
           "damage_taken": 4379,
           "damage_mitigated": 942,
           "healing_player": 249.999985,
           "healing_player_self": 663,
           "wins": 2,
           "losses": 519,
           "wards_mines_placed": 1098,
           "earned_xp": 157850,
           "earned_tokens": 442,
           "average_placement": 17,
           "placements": {"1": 2, "2": 4, "3": 3, "4": 3, "... 26": 0, "27": 1}
     }
  },
  {
      "match_queue_name": "Duo",
      "match_queue_id": 475,
      "class_name": "Warrior",
      "class_id": 2594,
      "stats": {
           "games_played": 521,
           "kills_player": 371,
           "kills_bot": 6,
           "killing_spree_max": 5,
           "deaths": 479,
           "assists": 214,
           "duration_secs": 52100,
           "damage_player": 22019,
           "damage_done_in_hand": 21423,
           "damage_taken": 4379,
           "damage_mitigated": 942,
           "healing_player": 249.999985,
           "healing_player_self": 663,
           "wins": 2,
           "losses": 519,
           "wards_mines_placed": 1098,
           "earned_xp": 157850,
           "earned_tokens": 442,
           "average_placement": 17,
           "placements": {"1": 2, "2": 4, "3": 3, "4": 3, "... 26": 0, "27": 1}
     }
  }]        
}
```

# Get Player Match History
**getPlayerMatchHistory** {playerId}

Returns high level data regarding matches played in the past 30 days.  Limited to the 50 most recent matches.

```js
{
  "name": "RealmHero",
  "id": 123,
  "matches": [{
      "match_id": 526153,
      "match_datetime": "6\/14\/2018 5:14:27 PM",
      "match_duration_secs": 1243,
      "map_game": "LIVE Royale Map",
      "match_queue_name": "Duo",
      "match_queue_id": 475,
      "class_name": "Mage",
      "class_id": 2285,
      "team_id": 123828,
      "region": "Brazil",
      "gold": 0,
      "kills": 1,
      "creeps": 1,
      "assists": 0,
      "deaths": 1,
      "minutes": 8,
      "time_in_match_seconds": 513,
      "placement": 17,
      "damage": 2295,
      "damage_taken": 1949,
      "healing_player": 325
      "healing_player_self": 308,
      "healing_bot": 0,          
      "killing_spree_max": 1,
      "damage_mitigated": 1500,
      "damage_done_in_hand": 300,          
      "wards_mines_placed": 94          
  }]     
}
```

# Get Player Status
**getPlayerStatus** {playerId}

Returns player online/offline status.

```js
{
    "match_id": 1181882,
    "personal_status_message": null,
    "status_id": 3,
    "status": "In Game",          
    "ret_msg": null
}
```

# Search Players
**searchPlayers** {playerName}

Returns up to 500 players with playerName <i>starting with</i> parameter provided.

```js
[
    {"id":53198,
     "name":"EonicBoom",
     "ret_msg":null,
     "steam_id":76561198132255826
    },
    {"id":1741198,
     "name":"Eonic",
      "ret_msg":null,
      "steam_id":76561198117389412
    }
 ]
```

