### Data Source Name:
Spotify, a music streaming service. Here there are users who listens to song and artists who publishes their song.

### API Endpoint URL:
`GET https://api-partner.spotify.com/pathfinder/v1/query` returns track information, with key fields we are interested in being trackUnion.saved.

**Sample JSON Response:**
The api requests returns something like this:
```json
{
  "data": {
    "trackUnion": {
      "id": "1jLsirPDkUS2g4gnkYua58",
      "name": "Ignite",
      "saved": false,
      "playcount": "355297545",
      "playability": {
        "playable": true,
        "reason": "PLAYABLE"
      },
      "firstArtist": {
        "items": [
          {
            "profile": { "name": "Alan Walker" }
          }
        ]
      },
      "uri": "spotify:track:1jLsirPDkUS2g4gnkYua58"
    }
  }
}

```

### Technical Breakdown:
This schema integrates Spotify's API to check if a user has saved or followed the track "Ignite" by Alan Walker in their library. The key field of interest is trackUnion.saved, which determines whether the user has the track in their saved list.

### Schema Code:
```json
{
  "issuer": "Spotify",
  "desc": "Prove you are following Ignite Song by Alan Walker",
  "website": "https://open.spotify.com/track/1jLsirPDkUS2g4gnkYua58",
  "APIs": [
    {
      "host": "api-partner.spotify.com",
      "intercept": {
        "url": "pathfinder/v1/query",
        "method": "GET",
        "query": [
          {
            "operationName": "getTrack",
            "verify": false
          },
          {
            "variables": "%7B%22uri%22%3A%22spotify%3Atrack%3A1jLsirPDkUS2g4gnkYua58%22%7D",
            "verify": true
          },
          {
            "extensions": "%7B%22persistedQuery%22%3A%7B%22version%22%3A1%2C%22sha256Hash%22%3A%22ae85b52abb74d20a4c331d4143d4772c95f34757bfa8c625474b912b9055b5c0%22%7D%7D",
            "verify": true
          }
        ]
      },
      "assert": [
        {
          "key": "data|trackUnion|saved",
          "value": "true",
          "operation": "="
        }
      ]
    }
  ],
  "HRCondition": [
    "Spotify Account Owner"
  ],
  "tips": {
    "message": "When you successfully log in, please click the 'Start' button to initiate the verification process."
  },
  "category": "Social",
  "id": "0xe1f704dd4c6943299c675b28221855ee"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator (extension) screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/07d00c58-cf9e-4f87-8622-5867968d4ea4)

