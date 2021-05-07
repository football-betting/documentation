# Microservice documentation 


## MatchApi

It should provide a Json where all the match are and also the LiveApi where the result where game which just runs


MatchApi for all futuregie spiell should look like this:

```JSON
{
    event: match.api
    data: {
      "matchId": "2020-06-16-21:00-FR-DE",
      "team1" : "FR",
      "team2" : "DE",
      "matchDatetime": "2020-06-16 21:00",
      "scoreTeam1": null,
      "scoreTeam2": null,
    }
}
```

When a game is loud, the goals must be sent along. The json should look like this:

```JSON
{
    event: match.api
    data: {
      "matchId": "2020-06-16-21:00-FR-DE",
      "team1" : "FR",
      "team2" : "DE",
      "matchDatetime": "2020-06-16 21:00",
      "scoreTeam1": 1,
      "scoreTeam2": 4,
    }
}
```

Please send one event per game

