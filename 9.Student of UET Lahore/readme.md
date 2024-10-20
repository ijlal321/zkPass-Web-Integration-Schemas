### Data Source Name:
UET Lahore Learning portal, a prestigious educational institution in Pakistan. Here user can log in and see all his details from CGPA to Fee structure.

### API Endpoint URL:
`POST https://lms.uet.edu.pk/web/session/get_session_info` returns a JSON response with student details.

**Sample JSON Response:**
The api requests returns something like this:
```json
{
    "jsonrpc": "2.0",
    "id": 122394,
    "result": {
        "username": "2022cs00@student.uet.edu.pk",
        "user_context": {
            "lang": "en_US",
            "tz": "Asia/Karachi",
            "uid": 55420
        },
        "uid": 55420,
        "db": "OBE",
        "company_id": 1,
        "session_id": "e2ea0edd9d9dbe170cccff1692a4f8d0d686ad75"
    }
}
```

### Technical Breakdown:
To verify if the user is a student of UET Lahore, the API response is checked for the following condition:

  **The username field within the result object must not be null, indicating the user is logged in as a student.**

### Schema Code:
```json
{
  "issuer": "UET Lahore",
  "desc": "Verify I am a student of UET Lahore",
  "website": "https://lms.uet.edu.pk/web?#view_type=form&model=obe.convocation&menu_id=1250",
  "APIs": [
    {
      "host": "lms.uet.edu.pk",
      "intercept": {
        "url": "web/session/get_session_info",
        "method": "POST"
      },
      "assert": [
        {
          "key": "result|username",
          "value": "null",
          "operation": "!="
        }
      ],
      "nullifier": "result"
    }
  ],
  "HRCondition": [
    "Student of UET"
  ],
  "tips": {
    "message": "When you successfully log in, please click the 'Start' button to initiate the verification process."
  },
  "category": "Legal Identity",
  "id": "0xd72f4d2133c8438eab0ab76bf93fb1f9"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source.

![image](https://github.com/user-attachments/assets/df22b93d-c3dd-4d4d-aa0a-31d474e44f14)

