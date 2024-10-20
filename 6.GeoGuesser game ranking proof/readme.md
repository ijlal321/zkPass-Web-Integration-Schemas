### Data Source Name:
GeoGuesser, a popular game that allows players to guess locations from Google Street View images.

### API Endpoint URL:
`GET https://www.geoguessr.com/api/v3/profiles/` returns all information about logged in user.

**Sample JSON Response:**
The api requests returns something like this:
```json
{
    "user": {
        "isProUser": false,
        ... // other fields
        },
        ... // other fields 
    "playingRestriction": {
        ...
    },
    "email": "logegot648@abaot.com",
    "isEmailChangeable": true,
    "isEmailVerified": false,
    "emailNotificationSettings": {
       ...
    },
    "isBanned": false,
    "chatBan": false,
    ...
}
```

### Technical Breakdown:
To verify if the player is a pro and not banned, the API response is checked for the following conditions:

 1. The **isProUser** field must be **true**.
2. The **isBanned** field must be **false**.

The api returns all information about user, like his scores etc, making verification very simple and opens alot of different ways to handle it.

### Schema Code:
```json
{
  "issuer": "GeoGuesser",
  "desc": "Check if a gamer on popular geoguesser game is a pro player. Also check if he is not banned so he can enter secret society of pro players.",
  "website": "https://www.geoguessr.com/me/achievements",
  "APIs": [
    {
      "host": "www.geoguessr.com",
      "intercept": {
        "url": "/api/v3/profiles/",
        "method": "GET"
      },
      "assert": [
        {
          "key": "user|isProUser",
          "value": "true",
          "operation": "="
        },
        {
          "key": "isBanned",
          "value": "false",
          "operation": "="
        }
      ],
      "nullifier": "user"
    }
  ],
  "HRCondition": [
    "Check pro level and must not be banned"
  ],
  "tips": {
    "message": "When you successfully log in, please click the 'Start' button to initiate the verification process."
  },
  "category": "Game",
  "id": "0xdd03b8e31c14400d88b4ec9a77639c5d"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/66a4ca0d-7916-4d9f-883f-531e7a1e53bb)

