### Data Source Name:
Discord, a popular communication platform for gamers and communities.

### API Endpoint URL:
`GET https://discord.com/api/v9/users/@me` returns a JSON response with details about current logged in user.

**Sample JSON Response:**
The api requests returns something like this:
```json
{
    "id": "something",
    "username": "something",
    "avatar": null,
    "discriminator": "0",
    "public_flags": 0,
    "flags": 0,
    "banner": null,
    "accent_color": null,
    "global_name": "ijlal",
    "avatar_decoration_data": null,
    "banner_color": null,
    "clan": null,
    "mfa_enabled": false,
    "locale": "en-US",
    "premium_type": 0,
    "email": "something hidden",
    "verified": true,  // here it checks if user verified
    "phone": "hidden",
    "nsfw_allowed": true,
    "linked_users": [],
    "bio": "",
    "authenticator_types": []
}
```

### Technical Breakdown:
To verify if the user has a proper and verified account, the API response is checked for the following conditions:

**The verified field must be true.**
### Schema Code:
```json
{
  "issuer": "Discord",
  "desc": "It is confirmed user has a proper account, which has been verified from Discord",
  "website": "https://discord.com",
  "APIs": [
    {
      "host": "discord.com",
      "intercept": {
        "url": "api/v9/users/@me",
        "method": "GET"
      },
      "assert": [
        {
          "key": "verified",
          "value": "true",
          "operation": "="
        }
      ],
      "nullifier": "id"
    }
  ],
  "HRCondition": [
    "Discord verified Account Owner"
  ],
  "tips": {
    "message": "When you successfully log in, please click your account on the bottom left corner and wait."
  },
  "category": "Social",
  "id": "0xb74ada84a6f44b5f969309df6697bfb0"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/6731d409-79a3-47fb-a768-bb9dbaf405d9)
