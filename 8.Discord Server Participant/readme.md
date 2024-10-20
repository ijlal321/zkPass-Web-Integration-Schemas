### Data Source Name:
Discord, a popular communication platform for gamers and communities.

### API Endpoint URL:
`GET https://discord.com/api/v9/channels/1278648011345629232/messages` returns messages in a server which user can access only if he is part of that server.

**Sample JSON Response:**
The api requests returns something like this:
```json
[
    {
        "type": 7,
        "content": "",
        "mentions": [],
        "mention_roles": [],
        "attachments": [],
        "embeds": [],
        "timestamp": "2024-09-27T18:16:27.367000+00:00",
        "edited_timestamp": null,
        "flags": 0,
        "components": [],
        "id": "1289289570155761877",
        "channel_id": "1278648011345629232",
        "author": {
            "id": "878571462586429460",
            "username": "chrisasek",
            "avatar": "50522f7faafa43b874e3b250cf5dda5c",
            "discriminator": "0",
            "public_flags": 0,
            "flags": 0,
            "banner": null,
            "accent_color": null,
            "global_name": "chrisasek",
            "avatar_decoration_data": null,
            "banner_color": null,
            "clan": null
        },
        "pinned": false,
        "mention_everyone": false,
        "tts": false
    },
    ...
]

```

### Technical Breakdown:
A user can only access messages of a discord server if he is part of a server. If user successfully loads all messages from a server, means he is part of that server.

### Schema Code:
```json
{
  "issuer": "Discord",
  "desc": "It is confirmed user is part of a specific discord group",
  "website": "https://discord.com/channels/1278648011345629228/1278648011345629232",
  "APIs": [
    {
      "host": "discord.com",
      "intercept": {
        "url": "api/v9/channels/1278648011345629232/messages",
        "method": "GET"
      },
      "assert": [
        {
          "key": "0",
          "value": "null",
          "operation": "!="
        }
      ]
    }
  ],
  "HRCondition": [
    "Discord Group"
  ],
  "tips": {
    "message": "Wait at least 3 seconds, and give it time to load."
  },
  "category": "Social",
  "id": "0x4dec5bd1c63b4572bf1a3ce48641ec99"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/22c5debf-05f0-4952-a774-d0c5690d0c28)

