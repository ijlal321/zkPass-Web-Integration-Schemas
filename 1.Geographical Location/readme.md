### Data Source Name:
IP2Location, a platform providing geolocation data based on IP addresses.

### API Endpoint URL:
`POST https://api.ip2location.io/query/` returns a JSON response with details such as IP address information, city, coordinates, and ISP details.

**Sample JSON Response:**
```json
{
  "addressType": "(U) Unicast",
  "areaCode": "(92) 042",
  "asName": "Cyber Internet Services Pvt Ltd.",
  "asNumber": "9541",
  "category": "(IAB19-18) Internet Technology",
  "cityName": "Lahore",
  "coordinates": "31.549677, 74.343556",
  "countryCode": "PK",
  "countryName": "Pakistan",
  "district": "Lahore District",
  "domain": "cyber.net.pk",
  "elevation": "218m",
  "isProxy": "No",
  "isp": "Cyber Internet Services Pakistan",
  "lastSeen": "-",
  "localTime": "2024-10-20 19:16:04",
  "mcc": "-",
  "mnc": "-",
  "mobileBrand": "-",
  "netSpeed": "DSL",
  "proxyAsName": "-",
  "proxyAsNumber": "-",
  "proxyProvider": "-",
  "proxyType": "-",
  "regionName": "Punjab",
  "threat": "-",
  "timeZone": "UTC +05:00",
  "usageType": "(ISP) Fixed Line ISP",
  "weather": "Lahore (PKXX0011)",
  "zipCode": "55110"
}
```

### Technical Breakdown:
The schema integrates IP2Location API with the zkPass framework to verify users based on geographic location, using cityName and coordinates for validation.

### Schema Code:
```json
{
  "issuer": "ip2location",
  "desc": "The platform to ask questions and connect with people who contribute unique insights and quality answers.",
  "website": "https://www.ip2location.com/",
  "APIs": [
    {
      "host": "api.ip2location.io",
      "intercept": {
        "url": "query/",
        "method": "POST"
      },
      "assert": [
        {
          "key": "cityName",
          "value": "Lahore",
          "operation": "="
        }
      ],
      "nullifier": "coordinates"
    }
  ],
  "HRCondition": [
    "Quora Account Owner"
  ],
  "tips": {
    "message": "When you successfully log in, please click the 'Start' button to initiate the verification process."
  },
  "category": "Legal Identity",
  "id": "0xbe025484b1c646048ca9d763905c82e2"
}
```

### Optional - Demo/Test Case:
A test case simulating the verification of a user based in Lahore, showing how the schema processes the data and validates against IP2Location.