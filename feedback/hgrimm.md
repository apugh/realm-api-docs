
# Realm Royale Endpoint Feedback
**specifically related to Realm Royale**

* I'd suggest adding an endpoint for a players' match history similar to getMatchHistory (params: playerName) in SMITE/Paladins API. In case the calls for average_placement and placements in getPlayerStats are too performance heavy, you could relocate the single placements into the matches returned by the suggested getMatchHistory endpoint so the developer can estimate the averages by himself.

* A little neat, but yet unfundamental stat to be pulled would be the death position of a player, in case this data is available. =)

* Additionally, to reduce the transfer of unneccessary data (and with that, higher bandwidth), a players endpoint for his teams' performance in a particular match would be extremely helpful (e.g. getPlayerTeamDetails, params: matchID). This endpoint will return the data block for the players' team only, excluding the stats for potential 49 other Duos or 24+ Squads.

Why this would help: (estimations chosen freely)
- 90% of people are interested in players performance only (getMatchHistory)
- Assuming a user would also be interested in the players' team performance, the current endpoints would require me pulling the whole match block and excluding all other teams from my end evaluation. To prevent this, a new endpoint of getPlayerTeamDetails by a matchID would drastically reduce the unused output (unimportant for a single situation, but influential on 1000+ daily pulls by each dev).
- Developers that would want to analyze all teams will still have the getMatchDetails endpoint as an easy solution.


UPDATE 15. June:

- An endpoint or option for a users class performance would be awesome for the early release of the API (like getPlayerStats desc. states: "If desired, that data can be broken out separately.")

- I agree with MichaelNay that a field for the players STEAM_ID would be beneficial and would love to see that implemented (if possible). =)
