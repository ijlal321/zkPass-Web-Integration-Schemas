### Data Source Name:
IP2Location, a platform providing geolocation data. Like city , country, postal code etc.

### API Endpoint URL:
`POST https://api.ip2location.io/query/` returns a JSON response with details such as IP address information, city, coordinates, and ISP details.

**Sample JSON Response:**
The api requests returns something like this:
```json
{
  "addressType": "(U) Unicast",
  "areaCode": "(92) 042",
  "asName": "Cyber Internet Services Pvt Ltd.",
  "asNumber": "954124",
  "category": "(IAB19-18) Internet Technology",
  "cityName": "Lahore",
  "coordinates": "94.549677, 27.343556",
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
  "zipCode": "24550"
}
```

### Technical Breakdown:
This will allow anyone to prove they are currently in a certain area. If we have our coordinates (provided by browser) or Ip address, we can get our current location by services like the one used in this case. Hence we can prove our location. This can be used in situation when hey, are you currently is US ? then you may enter... scenerio.

### Schema Code:
```json
{
  "issuer": "ip2location",
  "desc": "Allows users to prove their Geographical Location. In this example, checking if user Lives in Lahore. For simplicity, we are just checking city for now.",
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
    "Person must live in Lahore"
  ],
  "tips": {
    "message": "Just wait for website to load"
  },
  "category": "Legal Identity",
  "id": "0xbe025484b1c646048ca9d763905c82e2"
}
```

### Optional - Demo/Test Case:
This has numerous usecases in real world. I have attested a schema validator screenshot to prove this schema is valid and it works and adheres to guidelines and protocols set by zkPass. It works fully well with provided data source,

![image](https://github.com/user-attachments/assets/959bad0e-51e2-4412-ae20-618d4828ea4f)
