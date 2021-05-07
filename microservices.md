# Microservice documentation 


### Match-Id

MatchId is a date and start time of the game and ISO code of lander

Format: `<Date>:<Time>:<CountryIso-CountryIso>`



## MatchApi

It should provide a Json where all the match are and also the LiveApi where the result where game which just runs


MatchApi for all futuregie spiell should look like this:



```JSON
{
   "event":"match.api",
   "data":{
      "matchId":"2020-06-16:2100:FR-DE",
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
      "matchId":"2020-06-16:2100:FR-DE",
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
         "matchId":"2020-06-16:2100:FR-DE",
         "team1":"FR",
         "team2":"DE",
         "matchDatetime":"2020-06-16 21:00",
         "scoreTeam1":1,
         "scoreTeam2":4
      },
      {
         "matchId":"2020-06-20:1800-PT-DE",
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


## Tip

Tip service gets from application where user can enter his tip the info what result the user has entered.

The json was made to look like this:

> Field User is Unique und is a string 

```JSON
{
   "event":"tip.user",
   "data":{
       "matchId": "2020-06-16:2100-FR-DE",
       "user" : "ninja",
       "tipDatetime": "2020-06-12 14:36",
       "tipTeam1": 2,
       "tipTeam2": 3
   }
}
```

When the tip service gets a data it should send a tip list.


The tip list is per user related, so if a user changes his tip the service has to send a json with all tips from one user.

```JSON
{
   "event":"tip.userlist",
   "data":[
      {
       "matchId": "2020-06-16:2100-FR-DE",
       "user" : "ninja",
       "tipDatetime": "2020-06-12 14:36",
       "tipTeam1": 2,
       "tipTeam2": 3
      },
      {
       "matchId": "2020-06-16:2100-PL-IT",
       "user" : "ninja",
       "tipDatetime": "2020-06-12 14:38",
       "tipTeam1": 0,
       "tipTeam2": 4
      }
   ]
}
```





