### Data Source Name:
UET Lahore Learning portal, a prestigious educational institution in Pakistan. Here user can log in and see all his details from CGPA to Fee structure.

### API Endpoint URL:
`POST https://lms.uet.edu.pk/web/dataset/call_kw/obe.grade.book.detail/read`  retrieves the GPA details for students.

**Sample JSON Response:**
The api requests returns something like this:
```json
{
    "jsonrpc": "2.0",
    "id": 2857345,
    "result": [
        {
            "semester": "FALL 2022",
            "semester_ch": 18.0,
            "cgpa": "3.867",
            "id": 328474,
            "gpa": "3.867"
        },
        ...
    ]
}
```

### Technical Breakdown:
To verify if the student's GPA in the first semester is greater than 3, the API response is checked for the following condition:

  **The cgpa field for the first semester (identified as result[0].cgpa) must be greater than 3.**


### Schema Code:
```json
{
  "issuer": "UET Lahore",
  "desc": "In first semester your gpa was more than 3",
  "website": "https://lms.uet.edu.pk/web?#view_type=form&model=obe.grade.book&menu_id=572",
  "APIs": [
    {
      "host": "lms.uet.edu.pk",
      "intercept": {
        "url": "web/dataset/call_kw/obe.grade.book.detail/read",
        "method": "POST"
      },
      "assert": [
        {
          "key": "result|0|gpa",
          "value": "3",
          "operation": ">"
        }
      ],
      "nullifier": "id"
    }
  ],
  "HRCondition": [
    "Student of UET with Gpa in 1st semester > 3"
  ],
  "tips": {
    "message": "When you successfully log in, please click the show semester summary button to initiate the verification process."
  },
  "category": "Legal Identity",
  "id": "0x091cdb3853014d8e9ea142c39180ea79"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/8e2a2197-6965-4eff-87e6-c56593e5c856)

