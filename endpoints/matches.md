# Get Match IDs by Queue 
**getMatchIDsByQueue** {queue}/{date}/{hour}

Returns all matchID values for a queue for a particular timeframe.  Similar to SMITE/Paladins

```js
[
  {
      "active_flag": "n",
      "match": 1793874     
  }
]
```

# Get Match Details
**getMatchDetails** {matchId}

Returns <b>end of match</b> stats for a particular match.  Intra-match stats are not available.
  - teams/id is only relevant for grouping within this match
  - deaths would be "1" or "0"
  - goal is to group by teams (not meaningful for the Solo queue), then players within the team
  - people have asked for listing a.) weapon owned at death (or end-of-match), and b.) weapon used to cause player's death ... this data isn't clearly available but I'm asking around about how to obtain it if possible.

```js
[
  {   
      "match_id": 1793874,
      "region": "Europe",
      "queue_id": 476,
      "queue": "Quad",
      "duration_secs": 1805,
      "teams": [{
        "id": 383773,
        "placement": 1,
        "players": [{
            "name": "1stPlayer",
            "id": 3987123,
            "level": 22,
            "kills_player": 2,
            "kills_bot": 1,
            "assists": 1,
            "deaths", 1,
            "damage_player": 3361,
            "healing_player": 249.999985,            
            "duration_secs": 1422,
            "damage_taken": 344,
            "killing_spree_max": 11,
            "dropped_out_flag": 0,
            "healing_player_self": 284,
            "damage_mitigated": 450,
            "profile": "MaleTank",
            "damage_done_in_hand", 1231,
            "mines_wards_placed", 96,
            "earned_xp", 27100,
            "earned_tokens", 177
         }],  
      }],     
  }
]
```

# Get Match History
**getMatchHistory** {playerId}

Returns high level data regarding matches played in the past 30 days.  Limited to the 50 most recent matches.

```js
[
  {
      "name": "RealmHero",
      "id": 123,
      "matches": [{
          "match_id": 526153,
          "match_datetime": "6\/14\/2018 5:14:27 PM",
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
          "healing_player_self": 308,
          "killing_spree_max": 1,
          "wards_mines_placed": 94          
      }]     
  }
]
```
