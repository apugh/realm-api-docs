
# Realm Royale API Feedback (multiple contributors)
**Eric SmiteGuru**

- get player stats call - break out by Profile (MaleTank, FemaleDamage,..) since it's what makes the game unique from other BRs and more classes are planned and it would be a shame to lose that granularity of data when it can just be combined to get the summary per queue by the developer like it is on Smite and Paladins atm. <i>[AP: 2018-06-15]: Yes, getPlayerStats() will return aggregate and (match_queue, class) detailed breakdowns of stats.</i>

- Match Details call - would deaths not increment for the times someone gets downed or turned into a chicken? And do you know what this field is for: dropped_out_flag?  <i>[AP: 2018-06-15]: Good questions ... will check w/Dev</i>

- Would it be possible to add the region that the match took place into the top level match object where the match_id and queue stuff is?  <i>[AP: 2018-06-15]:  Yes.</i>

**CSpraggs**

- Leaderboards:  Add average kill count? If I understand correctly the highest ranks are based on kill count too.  <i>[AP: 2018-06-15]: Yes, will add it.</i>

- Players: As granular as possible so splitting up average_placement is preferred over grouping them.  <i>[AP: 2018-06-15]: Yes, getPlayerStats() will return aggregate and (match_queue, class) detailed breakdowns of stats.</i>

**Negativitet**
- Could getPlayerMatchHistory() be built to handle up to some level of multiple playerId inputs? To simplify for us that want to work with multiple players at the same time? Getting the result for 25 playerIds at once will be less intense on databases than fetching one result x 25 times.
- getPlayerMatchHistory() could benefit from **optional** input parameter, something like "last fetch timestamp" so that you don't re-fetch results you've already gathered. Like so: getPlayerMatchHistory(12345,'2018-07-10 11:38:00') and then you get results for 12345 that are saved later than 2018-07-10 11:38:00
