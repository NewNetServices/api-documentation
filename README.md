# NNS SFO CSIMS API Testing cURL commands for Windows Command Prompt
1. [Authenticate](#Authenticate)

    * [200 OK](#Authenticate-200)
    * [400 Unauthorized](#Authenticate-401)

2. [SendServiceRequest (Southbound)](#SendServiceRequest)

    * [201 Created](#SendServiceRequest-200)
    * [401 Unauthorized](#SendServiceRequest-401)
    * [400 Bad Request](#SendServiceRequest-400)

3. [SubmitAlert (Southbound)](#SubmitAlert)

    * [201 Created](#SubmitAlert-201)
    * [401 Unauthorized](#SubmitAlert-401)
    * [400 Bad Request](#SubmitAlert-400)

4. [CircuitIdUpdates (Northbound)](#CircuitIdUpdates)

    * [202 Accepted](#CircuitIdUpdates-202)
    * [401 Unauthorized](#CircuitIdUpdates-401)
    * [400 Bad Request](#CircuitIdUpdates-400)
    * [404 Not Found](#CircuitIdUpdates-404)

---

## <span id="Authenticate">Authenticate (Southbound)</span>
### <span id="Authenticate-200">Authenticate : VALID REQUEST</span>
#### Expected Response Code
```
200 OK
```
#### Request Headers Sent
```
Content-Type: application/json
```
#### Request Body Sent
```
{
  "userName": "TBD",
  "password": "TBD"
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Content-Type: application/json" ^
  -d '{"userName":"TBD","password":"TBD"}' ^
  qa-csims01/api/authentication/authenticate
```
#### Server Response Body
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA
```

---

### <span id="Authenticate-401">Authenticate : INVALID Username/Password</span>
#### Expected Response Code
```
401 Unauthorized
```
#### Request Headers Sent
```
Content-Type: application/json
```
#### Request Body Sent
```
{
  "userName": "wrongUser",
  "password": "badPass"
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Content-Type: application/json" ^
  -d '{"userName":"wrongUser","password":"badPass"}' ^
  qa-csims01/api/authentication/authenticate
```
#### Server Response Body
```
User name or password is incorrect.
```

---

## <span id="SendServiceRequest">SendServiceRequest (Southbound)</span>
### <span id="SendServiceRequest-200">SendServiceRequest : VALID REQUEST</span>
#### Expected Response Code
```
200 OK
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA
```
#### Request Body Sent
```
{
  "requestItemID": "987654321",
  "requestSysID": ".",
  "provisionTaskID": "123456789",
  "provisionTaskSysID": ".",
  "requesterContactName": "FirstName LastName",
  "requesterContactEmail": "your@email.com",
  "provisionTaskDescription": "Breif description of this request."
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID":"987654321","requestSysID":".","provisionTaskID":"123456789","provisionTaskSysID":".","requesterContactName":"FirstName LastName","requesterContactEmail":"your@email.com","provisionTaskDescription":"Breif description of this request."}' ^
  qa-csims01/v1/servicerequest/sendservicerequest
```
#### Server Response Body
```
{
  "responseCode": "Success",
  "httpCode": 201,
  "responseMessage": "524d00b9-09bc-4ac4-a309-4ee963b24772",
  "responseObject": null,
  "errorMessage": null
}
```

---

### <span id="SendServiceRequest-401">SendServiceRequest : INVALID JWT Token</span>
#### Expected Response Code
```
401 Unauthorized
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer abcdefghijklmnopqrstuvwxyz1234567890
```
#### Request Body Sent
```
{
  "requestItemID": "987654321",
  "requestSysID": ".",
  "provisionTaskID": "123456789",
  "provisionTaskSysID": ".",
  "requesterContactName": "FirstName LastName",
  "requesterContactEmail": "your@email.com",
  "provisionTaskDescription": "Breif description of this request."
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer abcdefghijklmnopqrstuvwxyz1234567890" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID":"987654321","requestSysID":".","provisionTaskID":"123456789","provisionTaskSysID":".","requesterContactName":"FirstName LastName","requesterContactEmail":"your@email.com","provisionTaskDescription":"Breif description of this request."}' ^
  qa-csims01/v1/servicerequest/sendservicerequest
```

---

### <span id="SendServiceRequest-400">SendServiceRequest : INVALID Body</span>
*requestItemId already exists*
#### Expected Response Code
```
400 Bad Request
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA
```
#### Request Body Sent
```
{
  "requestItemID": "987654321",
  "requestSysID": ".",
  "provisionTaskID": "123456789",
  "provisionTaskSysID": ".",
  "requesterContactName": "FirstName LastName",
  "requesterContactEmail": "your@email.com",
  "provisionTaskDescription": "Breif description of this request."
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID":"987654321","requestSysID":".","provisionTaskID":"123456789","provisionTaskSysID":".","requesterContactName":"FirstName LastName","requesterContactEmail":"your@email.com","provisionTaskDescription":"Breif description of this request."}' ^
  qa-csims01/v1/servicerequest/sendservicerequest
```
#### Server Response Body
```
{
  "responseCode": "Warning",
  "httpCode": 400,
  "responseMessage": null,
  "responseObject": null,
  "errorMessage": "Record already exists."
}
```

---

## <span id="SubmitAlert">SubmitAlert REQUESTS</span>
### <span id="SubmitAlert-201">SubmitAlert : VALID REQUEST</span>
#### Expected Response Code
```
201 Created
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA
```
#### Request Body Sent
```
{
  "alert":
    {
      "subject": "Production Node WF-FES0150B-EX4800C.***.******.*** is UP",
      "name": "WF-FES0150B-EX4800C.***.******.***",
      "ipAddress": "127.0.0.101",
      "location": "Starbucks || GPS Coordinates : (37.33182,-122.03118)","date": "July 5th, 2022 4:20AM"
    }
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"alert":{"subject": "Production Node WF-FES0150B-EX4800C.***.******.*** is UP","name": "WF-FES0150B-EX4800C.***.******.***","ipAddress": "127.0.0.101","location": "Starbucks || GPS Coordinates : (37.33182,-122.03118)","date": "July 5th, 2022 4:20AM"}}' ^
  localhost/v2/alert/create
```

---

### <span id="SubmitAlert-401">SubmitAlert : INVALID JWT Token</span>
#### Expected Response Code
```
401 Unauthorized
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer abcdefghijklmnopqrstuvwxyz1234567890
```
#### Request Body Sent
```
{
  "alert":
    {
      "subject": "Production Node WF-FES0150B-EX4800C.***.******.*** is UP",
      "name": "WF-FES0150B-EX4800C.***.******.***",
      "ipAddress": "127.0.0.101",
      "location": "Starbucks || GPS Coordinates : (37.33182,-122.03118)","date": "July 5th, 2022 4:20AM"
    }
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer abcdefghijklmnopqrstuvwxyz1234567890" ^
  -H "Content-Type: application/json" ^
  -d '{"alert":{"subject": "Production Node WF-FES0150B-EX4800C.***.******.*** is UP","name": "WF-FES0150B-EX4800C.***.******.***","ipAddress": "127.0.0.101","location": "Starbucks || GPS Coordinates : (37.33182,-122.03118)","date": "July 5th, 2022 4:20AM"}}' ^
  localhost/v2/alert/create
```

---

### <span id="SubmitAlert-400">SubmitAlert : INVALID Body</span>
*Data error eg. an incorrect variable name*
#### Expected Response Code
```
400 Bad Request
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA
```
#### Request Body Sent
```
{
  "alert":
    {
      "alertSubject": "Production Node WF-FES0150B-EX4800C.***.******.*** is UP",
      "name": "WF-FES0150B-EX4800C.***.******.***",
      "ipAddress": "127.0.0.101",
      "location": "Starbucks || GPS Coordinates : (37.33182,-122.03118)","date": "July 5th, 2022 4:20AM"
    }
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"alert":{"subject": "Production Node WF-FES0150B-EX4800C.***.******.*** is UP","name": "WF-FES0150B-EX4800C.***.******.***","ipAddress": "127.0.0.101","location": "Starbucks || GPS Coordinates : (37.33182,-122.03118)","date": "July 5th, 2022 4:20AM"}}' ^
  localhost/v2/alert/create
```

---

## <span id="CircuitIdUpdates">CircuitIdUpdates (Northbound)</span>
### <span id="CircuitIdUpdates-202">CircuitIdUpdates : VALID REQUEST</span>
#### Expected Response Code
```
202 Accepted
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Basic username:password
```
#### Request Body Sent
```
{
  "requestItemID": "987654321",
  "circuitIDs": "01;20;003;4000;0500;"
}
```
#### Request CURL
```
curl -X PATCH  ^
  -H "Authorization: Basic username:password" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID": "987654321","circuitIDs": "01;20;003;4000;0500;"}' ^
  https://sfo-mid01.commission.flysfo.com/api/safia/csims_integration/updateSCTask
```

---

### <span id="CircuitIdUpdates-401">CircuitIdUpdates : INVALID JWT Token</span>
#### Expected Response Code
```
401 Unauthorized
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Basic wrongUsername:wrongPassword
```
#### Request Body Sent
```
{
  "requestItemID": "987654321",
  "circuitIDs": "01;20;003;4000;0500;"
}
```
#### Request CURL
```
curl -X PATCH  ^
  -H "Authorization: Basic wrongUsername:wrongPassword" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID": "987654321","circuitIDs": "01;20;003;4000;0500;"}' ^
  https://sfo-mid01.commission.flysfo.com/api/safia/csims_integration/updateSCTask
```

---

### <span id="CircuitIdUpdates-400">CircuitIdUpdates : INVALID Body</span>
*Data error eg. an incorrect variable name*
#### Expected Response Code
```
400 Bad Request
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Basic username:password
```
#### Request Body Sent
```
{
  "ID": "987654321",
  "circuitIDs": "01;20;003;4000;0500;"
}
```
#### Request CURL
```
curl -X PATCH  ^
  -H "Authorization: Basic username:password" ^
  -H "Content-Type: application/json" ^
  -d '{"ID": "987654321","circuitIDs": "01;20;003;4000;0500;"}' ^
  https://sfo-mid01.commission.flysfo.com/api/safia/csims_integration/updateSCTask
```

---

### <span id="CircuitIdUpdates-404">CircuitIdUpdates : INVALID ID</span>
#### Expected Response Code
```
404 Not Found
```
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Basic username:password
```
#### Request Body Sent
```
{
  "requestItemID": "0001000",
  "circuitIDs": "01;20;003;4000;0500;"
}
```
#### Request CURL
```
curl -X PATCH  ^
  -H "Authorization: Authorization: Basic username:password" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID": "0001000","circuitIDs": "01;20;003;4000;0500;"}' ^
  https://sfo-mid01.commission.flysfo.com/api/safia/csims_integration/updateSCTask
```

