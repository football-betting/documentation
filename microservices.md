# Microservice documentation 


## MatchApi

It should provide a Json where all the match are and also the LiveApi where the result where game which just runs


MatchApi for all futuregie spiell should look like this:

```JSON
{
   "event":"match.api",
   "data":{
      "matchId":"2020-06-16-21:00-FR-DE",
      "team1":"FR",
      "team2":"DE",
      "matchDatetime":"2020-06-16 21:00",
      "scoreTeam1": null,
      "scoreTeam2": null
   }
}
```

When a game is loud, the goals must be sent along. The json should look like this:

```JSON
{
   "event":"match.api",
   "data":{
      "matchId":"2020-06-16-21:00-FR-DE",
      "team1":"FR",
      "team2":"DE",
      "matchDatetime":"2020-06-16 21:00",
      "scoreTeam1":1,
      "scoreTeam2":4
   }
}
```

Please send one event per game


## Match

Match service gets info about individual games from MatchApi service. The games should be saved and if something has changed:

* a new game has been added (e.g. knockout phase)
* a game result has changed (from 0-0 to 1-0)

a match-json with all players should be delivered

```JSON
{
   "event":"match",
   "data":[
      {
         "matchId":"2020-06-16-21:00-FR-DE",
         "team1":"FR",
         "team2":"DE",
         "matchDatetime":"2020-06-16 21:00",
         "scoreTeam1":1,
         "scoreTeam2":4
      },
      {
         "matchId":"2020-06-20-18:00-PT-DE",
         "team1":"PT",
         "team2":"DE",
         "matchDatetime":"2020-06-20 18:00",
         "scoreTeam1":null,
         "scoreTeam2":null
      },
      ...
   ]
}
```

