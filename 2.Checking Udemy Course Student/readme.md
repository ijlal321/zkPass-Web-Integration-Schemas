### Data Source Name:
Udemy, a platform providing online courses for various topics, with verification for specific course purchases.

### API Endpoint URL:
`GET https://www.udemy.com/api-2.0/course-landing-components/4939836/me/` returns a JSON response with details such as IP address information, city, coordinates, and ISP details.

**Sample JSON Response:**
The api requests returns data with alot of keys. What we are intrested in is this **Purchsse** field something like this:
```json
{
  "purchase": {
    "data": {
      "is_valid_student": false,
      "purchase_date": null,
      "is_in_subscription": false,
      "show_discount_info": true
    },
    "course_id": 950390,
    "is_free_for_organization": false,
    "is_in_subscription": false,
    "is_organization_only": false,
    "is_valid_student": false
  }
  ... {more data, not important here}
}

```

### Technical Breakdown:
This purchase date is only not null when someone has bought the course. Hence this will prove if a user is a valid student or not.

### Schema Code:
```json
{
  "issuer": "Udemy",
  "desc": "This will prove if you are a student of this sample Udemy course. i.e. you have bought it.",
  "website": "https://www.udemy.com/course/unity-multiplayer-blockchain-game-course/?couponCode=24T1MT101824",  // coupon code is optional, because when loading some courses, udemy automatically applies some coupons. But this will also work without it
  "APIs": [
    {
      "host": "www.udemy.com",
      "intercept": {
        "url": "api-2.0/course-landing-components/4939836/me/",
        "method": "GET",
        "query": [
          { // coupon code is optional, because when loading some courses, udemy automatically applies some coupons. But this will also work without it
            "couponCode": "24T1MT101824",     
            "components": "purchase,add_to_cart,buy_button,discount_expiration,price_text,lifetime_access_context",
            "verify": true
          }
        ]
      },
      "assert": [
        {
          "key": "purchase|data|purchase_date",
          "value": "null",
          "operation": "!="
        }
      ],
      "nullifier": "purchase|data|pricing_result"
    }
  ],
  "HRCondition": [
    "Udemy Course Student"
  ],
  "tips": {
    "message": "Just wait for website to load"
  },
  "category": "Educational",
  "id": "0x14b6c11171a6424ea1da58ff2489262c"
}

```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/4978b8bb-0187-4001-949e-e97d58f70e52)

