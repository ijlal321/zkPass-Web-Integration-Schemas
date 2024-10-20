### Data Source Name:
Spotify, a music streaming service. Here there are users who listens to song and artists who publishes their song.

### API Endpoint URL:
`GET https://api-partner.spotify.com/pathfinder/v1/query` eturns artist information, specifically checking if the artist is saved in the user's library.

**Sample JSON Response:**
The api requests returns something like this:
```json
{
  "data": {
    "lookup": [
      {
        "__typename": "ArtistResponseWrapper",
        "data": {
          "__typename": "Artist",
          "saved": false
        }
      }
    ]
  }
}

```

### Technical Breakdown:
This schema integrates Spotify's API to check if a user has saved or follows the artist Alan Walker in their library. The key field of interest is lookup[0].data.saved, which determines whether the user has saved the artist.

### Schema Code:
```json
{
  "issuer": "Spotify",
  "desc": "Prove you are following Artist Alan Walker",
  "website": "https://open.spotify.com/artist/7vk5e3vY1uw9plTHJAMwjN",
  "APIs": [
    {
      "host": "api-partner.spotify.com",
      "intercept": {
        "url": "pathfinder/v1/query",
        "method": "GET",
        "query": [
          {
            "operationName": "areEntitiesInLibrary",
            "verify": false
          }
        ]
      },
      "assert": [
        {
          "key": "data|lookup|0|data|saved",
          "value": "true",
          "operation": "="
        }
      ]
    }
  ],
  "HRCondition": [
    "Followed Alan Walker"
  ],
  "tips": {
    "message": "When you successfully log in, please click the 'Start' button to initiate the verification process."
  },
  "category": "Social",
  "id": "0x019e041d70c0488ab2683971c0055970"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/e2ee485b-011f-441d-8a15-a4b89fb0f68b)

