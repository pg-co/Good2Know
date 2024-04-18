[[_TOC_]]

# How to authenticate against Dynamics WebAPI

## Default HTTP authorization
### Request
```http
POST https://login.microsoftonline.com/{AZURE_TENANT_ID}/oauth2/v2.0/token HTTP/1.1
Host: login.microsoftonline.com
Content-Type: application/x-www-form-urlencoded

client_id={AZURE_CLIENT_ID}
&scope=https://{DYNAMICS_ORGANIZATION}.api.crm4.dynamics.com/.default
&client_secret={AZURE_CLIENT_SECRET}
&grant_type=client_credentials
```

### Response
```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "token_type": "Bearer",
  "expires_in": 3599,
  "ext_expires_in": 3599,
  "access_token": "ACCESS_TOKEN"
}
```


## Custom Connector

You first need to create a new ![Custom Connector](../../power-plattform/connectors/Create%20a%20custom%20connector.md)
