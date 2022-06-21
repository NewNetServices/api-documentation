# NNS SFO CSIMS API Testing cURL commands for Windows Command Prompt

## CreateServiceOrder REQUESTS
### CreateServiceOrder : VALID REQUEST
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
  "RequestItemId": "987654321",
  "ProvisioningTaskId": "123456789",
  "RequestorContactName": "FirstName LastName",
  "RequestorContactEmail": "your@email.com",
  "RequestorContactPhone": "800-333-5555",
  "ProvisioingTaskShortDescription": "Breif description of this request."
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"RequestItemId":"987654321","ProvisioningTaskId":"123456789","RequestorContactName":"FirstName LastName","RequestorContactEmail":"your@email.com","RequestorContactPhone":"800-333-5555","ProvisioingTaskShortDescription":"Breif description of this request."}' ^
  localhost/v2/serviceorder/create
```

---

### CreateServiceOrder : INVALID JWT Token
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
  "RequestItemId": "987654321",
  "ProvisioningTaskId": "123456789",
  "RequestorContactName": "FirstName LastName",
  "RequestorContactEmail": "your@email.com",
  "RequestorContactPhone": "800-333-5555",
  "ProvisioingTaskShortDescription": "Breif description of this request."
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer abcdefghijklmnopqrstuvwxyz1234567890" ^
  -H "Content-Type: application/json" ^
  -d '{"RequestItemId":"987654321","ProvisioningTaskId":"123456789","RequestorContactName":"FirstName LastName","RequestorContactEmail":"your@email.com","RequestorContactPhone":"800-333-5555","ProvisioingTaskShortDescription":"Breif description of this request."}' ^
  localhost/v2/serviceorder/create
```

---

### CreateServiceOrder : INVALID Body
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
  "Id": "987654321",
  "ProvisioningTaskId": "123456789",
  "RequestorContactName": "FirstName LastName",
  "RequestorContactEmail": "your@email.com",
  "RequestorContactPhone": "800-333-5555",
  "ProvisioingTaskShortDescription": "Breif description of this request."
}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"Id":"987654321","ProvisioningTaskId":"123456789","RequestorContactName":"FirstName LastName","RequestorContactEmail":"your@email.com","RequestorContactPhone":"800-333-5555","ProvisioingTaskShortDescription":"Breif description of this request."}' ^
  localhost/v2/serviceorder/create
```

---

