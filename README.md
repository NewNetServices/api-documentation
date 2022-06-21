# NNS SFO CSIMS API Testing cURL commands for Windows Command Prompt

## CreateServiceOrder REQUESTS
### CreateServiceOrder : VALID REQUEST
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA
```
#### Request Body Sent
```
{"requestItemID":"987654321"}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID":"987654321"}' ^
  localhost/v2/serviceorder/create
```
#### Expected Response Code
```
201 Created
```
#### Expected Response Header
```
Content-Type: application/json; charset=utf-8
```
#### Expected Response Body
```
{
  "data": {
    "serviceOrderNumber": 8003285278
  },
  "details": {
    "version": "2022.5.10",
    "date": "2022-06-21T18:14:54.936Z"
  }
}
```

---

### CreateServiceOrder : INVALID JWT Token
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer abcdefghijklmnopqrstuvwxyz1234567890
```
#### Request Body Sent
```
{"requestItemID":"987654321"}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer abcdefghijklmnopqrstuvwxyz1234567890" ^
  -H "Content-Type: application/json" ^
  -d '{"requestItemID":"987654321"}' ^
  localhost/v2/serviceorder/create
```
#### Expected Response Code
```
401 Unauthorized
```
#### Expected Response Header
```

```
#### Expected Response Body
```

```

---

### CreateServiceOrder : INVALID Body
#### Request Headers Sent
```
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA
```
#### Request Body Sent
```
{"id":"987654321"}
```
#### Request CURL
```
curl -X POST  ^
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoibm9haHMiLCJqdGkiOiI0Y2ZkNDY1My1hOTRmLTQ4MGUtYjAxOC0wYTJmODEyZGU5OTEiLCJodHRwOi8vc2NoZW1hcy5taWNyb3NvZnQuY29tL3dzLzIwMDgvMDYvaWRlbnRpdHkvY2xhaW1zL3JvbGUiOiJhZG1pbiIsImV4cCI6MTYzNTkyNTA0MywiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo2MTk1NSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6NDIwMCIsIlJvbGUiOiJhZG1pbiIsIlVzZXJOYW1lIjoibm9haHMiLCJSSWQiOiIxNDVlOGQ4OC0wMmFkLTQ4N2MtODg3ZC00ZjdkNDc2Nzg4ZWQifQ._zt1whTRjVhbOzQqUqOlIpaksVcDmoIjhLV_wiabuhA" ^
  -H "Content-Type: application/json" ^
  -d '{"id":"987654321"}' ^
  localhost/v2/serviceorder/create
```
#### Expected Response Code
```
400 Bad Request
```
#### Expected Response Header
```

```
#### Expected Response Body
```

```

