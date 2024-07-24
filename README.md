# Mosler Lock APIs (Version 1)

### 1. Create Booking

```
curl --location
'https://api.mosler.in/api/v1/hooks/booking/create' \
--header 'apikey: qcfVu6h3UBwAO3w5' \
--header 'Content-Type: application/json' \
--data-raw '{
"bookingStartDate": "2023-03-03T13:06:42.982Z",
"bookingEndDate": "2023-03-03T13:08:42.982Z",
"roomNumber": "11",
"customerPhone": "+91999999999",
"customerEmail": "mosler_dev@mosler.in",
"siteId": "123",
"referenceId": "xyzabcd123"
}'
```

#### Payload

- bookingStartDate ISODate(mandatory)

- bookingEnddate ISODate(mandatory)

- roomNumber String(mandatory)

- customerEmail or/and customerPhone String(one is mandatory)

- siteId String(mandatory)

- referenceId String(mandatory) [Unique for each booking]

### 2. Update Booking

```
curl --location
'https://api.mosler.in/api/v1/hooks/booking/update/{referenceId} \
--header 'apikey: qcfVu6h3UBwAO3w5' \
--header 'Content-Type: application/json' \
--data '{
"bookingStartDate": "2023-03-01T11:06:42.982Z",
"bookingEndDate": "2023-03-03T13:06:42.982Z"
}'
```

#### Payload

- bookingStartDate - ISODate(mandatory)

- bookingEnddate - ISODate(mandatory)

### 3. Cancel Booking

```
curl –location --request POST
'https://api.mosler.in/api/v1/hooks/booking/cancel/{referenceId} \
--header 'apikey: qcfVu6h3UBwAO3w5' \
--header 'Content-Type: application/json' \
--data ''
```

#### Payload

- Nothing needs to be passed

---

# APIs For Mobile Apps (Version 2)

# Lock APIs

## 1. Fetch ekeys for mobile users (beta)

- Method Type: GET
- Params: Unique Booking Id
- Headers: api key

Response Object would be as follows

```
{
        "total": 1,
        "pages": 1,
        "pageNo": 1,
        "pageSize": 2000,
        "list": [{
        "date": 1686810869000,
        "specialValue": 1967976951,
        "lockAlias": "M302_f1d545",
        "keyStatus": "110401",
        "endDate": 1686873600000,
        "keyName": "Ekey for Mosler",
        "keyId": 103471522,
        "lockMac": "25:10:88:45:D5:F1",
        "timezoneRawOffset": 19800000,
        "featureValue": "C2F44754CF1F7",
        "lockId": 7711494,
        "electricQuantity": 100,
        "lockData": "2x5vlPpVb7b1nZGEmSOhqVfdVYCB+hktr/S2a3hY67hLFAAPnw1CRbvK1q9k96iNd0wiEkLtmit5Lb2PGbu6rCXJjZKCwicLg4c0tGhvOsIdU+y7xRiPA3AsQKNcrsrpIAe3R0WzM1Z0V4hcs7g6GehJdDWZiEzhHcgekE91H9NJbDoHkIH5fiZbnEp5cvCS3gvfFFTm8w6YULf8YishS/L3DWXUZVZIjFULS0FpS3LHSXiXoip60/FYPAQJZv2KMlpiCiWAAmVocvoSSPu8piu5DhKXNLjhYeWO00DY4/Fx2fvawk8xMXS76EhG9MMDPQbirnQqvbCPQ8gJMIB7QyVw+Oy4N9Demj6XcwXn9y5oIY6fJ54c+NntDNnHzE16EhyyujKsPvKfN50F+AqdDhdCR596bAFcjdf6JU0R5l3lznD2A7q29tXcBaAkj3XZvmCjaUK4SuZVvGKjJOrurcwYWY3zytGc/q+G/Zarg82jWuYcmKBXHRWw1Em5fVca4KgFlMAHiImjQY+wNOApWTuELiP1uoCE6tIUHC5semqPPpejNXg5LB5VUKeGKrrhSTXIHpAtLxDpUsDwzRJV+2011JbDzfSmj8fbVe8x3baI19OFfQ9rtkdm5MazevopbQyEvC80GIZzzeFARYL1/SUQiEXV8Q==",
        "hasGateway": 0,
        "keyboardPwdVersion": 4,
        "remoteEnable": 2,
        "lockVersion": {
        "showAdminKbpwdFlag": true,
        "groupId": 1,
        "protocolVersion": 3,
        "protocolType": 5,
        "orgId": 1,
        "logoUrl": "",
        "scene": 2
        },
        "userType": "110302",
        "lockName": "M302_f1d545",
        "startDate": 1686810819956,
        "remarks": "For testing purpose.",
        "keyRight": 0
        }]
}

```

## 2. Fetch lockData Version 2

```
{{url}}/api/v2/booking/getLockData/:referenceId
```

- Method Type: GET
- Params: Unique Booking Id
- Headers: api key

Response Object would be as follows

```
[
    {
        "date": 1694770062000,
        "specialValue": 1967976951,
        "lockAlias": "M302_f1d545",
        "keyStatus": "110401",
        "endDate": 1695061800000,
        "keyName": "Mosler Key",
        "keyId": 120307616,
        "lockMac": "25:10:88:45:D5:F1",
        "passageMode": 2,
        "timezoneRawOffset": 19800000,
        "featureValue": "C2F44754CF1F7",
        "lockId": 7711494,
        "electricQuantity": 100,
        "lockData": "2x5vlPpVb7b1nZGEmSOhqVfdVYCB+hktr/S2a3hY67iuQTc1Lyh9ZzJlmYDsvr4rufejgM7/uKmchXqmhp9Zs593sQFXerRsMdu/uOzF5AjUbOUnodVL0F1NXdZU4SqxU/EVi90G08ALBuLKf1X9w3JChxBrxS33xFoWFvYQL0HBcLtTjsY7w8tIa3f6Ky5FI9E5n+Xyt8XUvfj3h9zRTrsAlMigxi5VYseec27GIeessuMEEWpSoODiy0KevbXvV0OALuNY5QDK0ai62QtWIt9V0xVnI1pCY719QGDg3MAIuLrhURwWcgJneUEerzCxg/S2mRgJasVY5sAyUHJ1aX2ITDDtUCxn0DM6FyxeRfkX/QjNvCjAIwdPfJs5SdvNGmsxXEfO/003EpcaH3+omt0Ha5FhtXnFEozgNaGlLx8ths4co5oq4+ZrCXrxccJJLMQuhkjduekcBfOoR5yNXC5NYqqYULSXzamVgLLSIQUcZQbH3WRFtMzUC6o2HiJD5GlPSQu6XHB3qzHp1R9qEI1lXzUVHx8UkeVvK9UFmGwDEaTFTb7oxJKzqTREshW8Qf4Y6M9yjkWLrfw830zWmzHchPAAwkJX6EgtcAifWPSIKlQmzH2hNOb9qNzQdG3Mzo7eWX9nhG3VIzS+h9cS7CUQiEXV8Q==",
        "hasGateway": 0,
        "keyboardPwdVersion": 4,
        "remoteEnable": 2,
        "lockVersion": {
            "showAdminKbpwdFlag": true,
            "groupId": 1,
            "protocolVersion": 3,
            "protocolType": 5,
            "orgId": 1,
            "logoUrl": "",
            "scene": 2
        },
        "userType": "110302",
        "lockName": "M302_f1d545",
        "startDate": 1694975400000,
        "remarks": "Have a nice day.",
        "keyRight": 0
    }
]

```

### 2.1 Create Booking Version 2

```
curl --location
'{{url}}/api/v2/booking/create' \
--header 'apikey: qcfVu6h3UBwAO3w5' \
--header 'Content-Type: application/json' \
--data-raw '{
"bookingStartDate": "2023-03-03T13:06:42.982Z",
"bookingEndDate": "2023-03-03T13:08:42.982Z",
"roomNumber": "11",
"customerPhone": "+91999999999",
"customerEmail": "mosler_dev@mosler.in",
"customerName": "Mosler Dev",
"siteId": "123",
"referenceId": "xyzabcd123"
}'
```

- Method Type: POST
- Headers: api key

#### 2.1.1 Payload

- bookingStartDate ISODate(mandatory)

- bookingEnddate ISODate(mandatory)

- roomNumber String(mandatory)

- customerEmail or/and customerPhone String(one is mandatory)

- siteId String(mandatory)

- referenceId String(mandatory) [Unique for each booking]

Response would be as follows

```
[
    {
        "lock_id": "64afdda230cad50f34c8985a",
        "lockId": "7711494",
        "bookingStartDate": "2023-08-18T13:06:42.982Z",
        "bookingEndDate": "2023-08-20T13:08:42.982Z",
        "roomNumber": "Room 3",
        "customerEmail": "testCustomer170823@yopmail.com",
        "customerPhone": "9988774455",
        "siteId": "64abbb19cf23c3235e39b968",
        "companyId": "64abba90cf23c3235e39b94e",
        "keyId": 115316608,
        "isDeleted": false,
        "referenceId": "TestRef170823",
        "moslerEmail": "booking_pxacil@mosler.in",
        "moslerPassword": "ac1fee1cf875a4c32441d895f27b5c39",
        "plainTextPassword": "ler.in",
        "_id": "64ddce851b108de61b4c4c22",
        "createdAt": "2023-08-17T07:38:45.795Z",
        "updatedAt": "2023-08-17T07:38:45.795Z"
    }
]

```

### 2.2 Update Booking Version 2

```
curl --location
'{{url}}/api/v2/booking/update/{referenceId} \
--header 'apikey: qcfVu6h3UBwAO3w5' \
--header 'Content-Type: application/json' \
--data '{
"bookingStartDate": "2023-03-01T11:06:42.982Z",
"bookingEndDate": "2023-03-03T13:06:42.982Z"
}'
```

- Method Type: PUT
- Headers: api key
- Params: Unique Reference Id

#### 2.2.1 Payload

- bookingStartDate - ISODate(mandatory)

- bookingEnddate - ISODate(mandatory)

Response object would be as follows:

```
{
    "data": {
        "_id": "64ddce851b108de61b4c4c22",
        "lock_id": "64afdda230cad50f34c8985a",
        "lockId": "7711494",
        "bookingStartDate": "2023-08-21T13:06:42.982Z",
        "bookingEndDate": "2023-08-23T13:08:42.982Z",
        "roomNumber": "Room 3",
        "customerEmail": "testCustomer170823@yopmail.com",
        "customerPhone": "9988774455",
        "siteId": "64abbb19cf23c3235e39b968",
        "companyId": "64abba90cf23c3235e39b94e",
        "keyId": 115316608,
        "isDeleted": false,
        "referenceId": "TestRef170823",
        "moslerEmail": "booking_pxacil@mosler.in",
        "moslerPassword": "ac1fee1cf875a4c32441d895f27b5c39",
        "plainTextPassword": "ler.in",
        "createdAt": "2023-08-17T07:38:45.795Z",
        "updatedAt": "2023-08-17T07:39:44.523Z"
    },
    "message": "Booking Updated Successfully.",
    "status": 200
}



```

### 2.3 Get Upcoming Bookings Version 2

```
curl --location 'http://localhost:6700/api/v2/booking/upcoming' \
--header 'apikey: 0a7fb8f5-14ba-4d70-a322-5cbeb2dc5667' \
--data ''
```

- Method Type: GET
- Headers: api key

Response object would be as follows:

```
[
    {
        "_id": "64cc8b88368aad134a191d16",
        "lock_id": "64afdda230cad50f34c8985a",
        "lockId": "7711494",
        "bookingStartDate": "2023-08-04T04:30:00.000Z",
        "bookingEndDate": "2023-09-05T05:30:00.000Z",
        "roomNumber": "Room 3",
        "customerEmail": "mosler_testing1@yopmail.com",
        "siteId": {
            "_id": "64abbb19cf23c3235e39b968",
            "siteName": "Site B"
        },
        "companyId": {
            "_id": "64abba90cf23c3235e39b94e",
            "name": "Testing Local KV"
        },
        "keyId": 113140584,
        "isDeleted": false,
        "referenceId": "ferferreferferfvvr",
        "buildingId": {
            "_id": "64abbb2ecf23c3235e39b991",
            "name": "Building 3"
        },
        "roomId": {
            "_id": "64bfc66de96ea2c9eec62bac",
            "roomNumber": "Room 3"
        },
        "moslerEmail": "booking_rxsxaw@mosler.in",
        "moslerPassword": "ac1fee1cf875a4c32441d895f27b5c39",
        "plainTextPassword": "ler.in",
        "createdAt": "2023-08-04T05:24:24.706Z",
        "updatedAt": "2023-08-04T05:24:24.706Z"
    }
]



```

# Gateway APIs (Beta)

## 1. Unlock via network (Gateway)

```
{{url}}/api/v2/room/unlock/:roomId
```

- Method Type: GET
- Params: room Id
- Headers: api key
  Response Object would be as follows

```
{
    "data": {
        "room": {
            "_id": "64ddce851b108de61b4c4c22",
            "roomName": "Room 3",
        },
        "siteId": {
            "_id": "64abbb19cf23c3235e39b968",
            "siteName": "Mosler Test Site",
        },
        "companyName": "Mosler Test Company",
        "floorName": "Ground Floor",
        "buildingName": "Mosler Test Building",
        "roomNumber": "123",
        "status": "UnLocked"
    },
    "message": "Room Unlocked Successfully.",
    "status": 200
}

```
## 2. Lock via network (Gateway)

```
{{url}}/api/v2/room/lock/:roomId
```

- Method Type: GET
- Params: room Id
- Headers: api key
  Response Object would be as follows

```
{
    "data": {
        "room": {
            "_id": "64ddce851b108de61b4c4c22",
            "roomName": "Room 3",
        },
        "siteId": {
            "_id": "64abbb19cf23c3235e39b968",
            "siteName": "Mosler Test Site",
        },
        "companyName": "Mosler Test Company",
        "floorName": "Ground Floor",
        "buildingName": "Mosler Test Building",
        "roomNumber": "123",
        "status": "Locked"
    },
    "message": "Room Locked Successfully.",
    "status": 200
}

```
## 3. Get Lock Battery Status via Network (Gateway)


```
{{url}}/api/v2/room/:roomId
```

- Method Type: GET
- Params: room Id
- Headers: api key
  Response Object would be as follows

```
{
    "data": {
        "room": {
            "_id": "64ddce851b108de61b4c4c22",
            "roomName": "Room 3",
        },
        "siteId": {
            "_id": "64abbb19cf23c3235e39b968",
            "siteName": "Mosler Test Site",
        },
        "companyName": "Mosler Test Company",
        "floorName": "Ground Floor",
        "buildingName": "Mosler Test Building",
        "roomNumber": "123",
        "status": "Locked",
        "batteryStatus": 100
    },
    
    "status": 200
}

```