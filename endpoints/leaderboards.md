# Get Leaderboard Details
**getLeaderboards** {queue}/{ranking_criteria}

Returns leaderboard information for a particular queue.
  - for duo and quad queues/modes the individual's placement results reflect their team/grouping; solo is self-explanatory
  - will limit results to the top 500 players; we never like to expose weak/beginner players
  - players that select to be "private" will have their player_name and player_id values hidden
  - {ranking_criteria} can be: 1: team_wins, 2: team_average_placement (shown below), 3: individual_average_kills, 4. win_rate, possibly/probably others as desired
  - expect this data to be cached on an hourly basis because the query to acquire the data will be expensive; don't spam the calls
 
```js
[
  {         
      "queue_id": 476,
      "queue": "Quad",      
      "last_updated": "3\/18\/2018 5:14:27 PM",
      "leaderboard": [{
        "rank": 1,
        "player_name": "BestPlayer",
        "player_id": 1242243,
        "matches": 234
        "team_wins": 15,
        "team_average_placement": 5        
      },
      {
        "rank": 2,
        "player_name": "2ndBestPlayer",
        "player_id": 1242244,
        "matches": 423
        "team_wins": 16,        
        "team_average_placement": 5.1
      }],     
  }
]
```
