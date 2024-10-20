### Data Source Name:
Gmail. A email serice provider where users can send and receive emails.

### API Endpoint URL:
`POST https://mail.google.com/sync/u/0/i/fd` returns data about current opened email from inbox.
**Sample JSON Response:**
The api repose is very complicated, but ofcouse the structure is always same. We can also get the subject, header etc. For simplicity, we are just taking senders email.
```json
[
  [
    [
      "thread-f:1808125701848709714",
      [
        ...
      ],
      [
        [
          "msg-f:1808125701848709714",
          [1, "noreply@discord.com", "Discord"]
        ],
        ...
      ],
      null,
      863169
    ]
  ],
  ...
]

```

### Technical Breakdown:
So the user can get access to email if he received it. And if he had reeceived he, then he can open it and he gets api response with above data. In this way we can verify if someone got email like a invitation or verification etc without revealing their true identity. Imaginge getting into a party without giving away any identity just because you got an email in your inbox.

### Schema Code:
```json
{
  "issuer": "Gmail",
  "desc": "Email manager, this checks if someone received an email from discord",
  "website": "https://mail.google.com/mail/u/0/#inbox",
  "APIs": [
    {
      "host": "mail.google.com",
      "intercept": {
        "url": "/sync/u/0/i/fd",
        "method": "POST",
        "query": [
          {
            "hl": "en",
            "verify": true
          },
          {
            "c": "0",
            "verify": true
          },
          {
            "rt": "r",
            "verify": true
          },
          {
            "pt": "ji",
            "verify": true
          }
        ]
      },
      "assert": [
        {
          "key": "1|0|1|1|0|1|1",
          "value": "noreply@discord.com",
          "operation": "="
        }
      ]
    }
  ],
  "HRCondition": [
    "Must receive an email from discord."
  ],
  "tips": {
    "message": "When you successfully log in, please click the discord email you want to verify to initiate the verification process."
  },
  "category": "Social",
  "id": "0x21f75b60262047c0a2d7fe9e5941b2db"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/580b2174-b85d-4cd7-a390-896a7b147e4f)

