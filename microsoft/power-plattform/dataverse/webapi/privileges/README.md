[[_TOC_]]

# Privileges

## How to add privileges to a [Security Role](../security-roles/README.md)

To add privileges you need to first fetch the nessecary information:
- PriviligeId
- PriviligeName
- BusinessUnitId
- Depth

### Fetch Information
#### Privileges
To find get the **PrivilegeId** & **PrivilegeName** you need to fetch all Privileges and select you choice.

##### Request
```http
GET https://{DYNAMICS_ORG}.api.crm4.dynamics.com/api/data/v9.0/privileges HTTP/1.1
Content-Type: application/json
Authorization: Bearer {ACCESS_TOKEN}
```

##### Response
```json
{
  "@odata.context": "https://{DYNAMICS_ORG}.api.crm4.dynamics.com/api/data/v9.0/$metadata#privileges",
  "value": [
    {
      "@odata.etag": "W/\"89610\"",
      "overwritetime": "1900-01-01T00:00:00Z",
      "solutionid": "{SOLUTION_GUID}",
      "introducedversion": "8.2.0.0",
      "canbebasic": false,
      "canbedeep": false,
      "ismanaged": true,
      "accessright": 65536,
      "canbeglobal": true,
      "privilegeid": "{PRIVILEGE_ID_GUID}",
      "canbeentityreference": false,
      "privilegerowid": "{PRIVILEGE_OWNER_ID_GUID}",
      "componentstate": 0,
      "name": "prvCreate{TABLE_SCHEMA_NAME}",
      "versionnumber": 89610,
      "canbeparententityreference": false,
      "canbelocal": false,
      "canberecordfilter": null,
      "iscustomizable": null
    },
    {
      "@odata.etag": "W/\"89611\"",
      "overwritetime": "1900-01-01T00:00:00Z",
      "solutionid": "{SOLUTION_GUID}",
      "introducedversion": "8.2.0.0",
      "canbebasic": false,
      "canbedeep": false,
      "ismanaged": true,
      "accessright": 65536,
      "canbeglobal": true,
      "privilegeid": "{PRIVILEGE_ID_GUID}",
      "canbeentityreference": false,
      "privilegerowid": "{PRIVILEGE_OWNER_ID_GUID}",
      "componentstate": 0,
      "name": "prvRead{TABLE_SCHEMA_NAME}",
      "versionnumber": 89611,
      "canbeparententityreference": false,
      "canbelocal": false,
      "canberecordfilter": null,
      "iscustomizable": null
    },
  ],
  "@odata.nextLink": "{next_link}"
}
```
#### BusinessUnit

##### Request
```http
GET https://{DYNAMICS_ORG}.crm4.dynamics.com//api/data/v9.0/businessunits HTTP/1.1
Content-Type: application/json
Authorization: Bearer {ACCESS_TOKEN}
```
##### Response
```json
{
  "@odata.context": "https://{DYNAMICS_ORG}.crm4.dynamics.com/api/data/v9.0/$metadata#businessunits",
  "value": [
    {
      "@odata.etag": "W/\"235837441\"",
      "address1_shippingmethodcode": 1,
      "_organizationid_value": "{GUID}",
      "address1_addressid": "{GUID}",
      "address1_addresstypecode": 1,
      "address2_addresstypecode": 1,
      "_parentbusinessunitid_value": "{GUID}",
      "_createdby_value": "{GUID}",
      "workflowsuspended": false,
      "createdon": "2024-04-16T11:20:03Z",
      "address2_shippingmethodcode": 1,
      "modifiedon": "2024-04-16T11:20:03Z",
      "inheritancemask": 1023,
      "_modifiedby_value": "{GUID}",
      "isdisabled": false,
      "versionnumber": 235837441,
      "address2_addressid": "{GUID}",
      "businessunitid": "{GUID}",
      "name": "{BUSINESS_UNIT_NAME}",
      "address2_line2": null,
      "address2_upszone": null,
      "address2_stateorprovince": null,
      "address1_telephone2": null,
      "divisionname": null,
      "tickersymbol": null,
      "address1_line3": null,
      "disabledreason": null,
      "address2_name": null,
      "address2_utcoffset": null,
      "address2_fax": null,
      "address2_line3": null,
      "address1_postofficebox": null,
      "description": null,
      "address1_county": null,
      "address1_city": null,
      "address1_name": null,
      "address2_postalcode": null,
      "picture": null,
      "overriddencreatedon": null,
      "address2_telephone2": null,
      "_createdonbehalfby_value": null,
      "address2_postofficebox": null,
      "address1_utcoffset": null,
      "stockexchange": null,
      "address1_telephone3": null,
      "_transactioncurrencyid_value": null,
      "address2_latitude": null,
      "creditlimit": null,
      "address2_telephone3": null,
      "_modifiedonbehalfby_value": null,
      "emailaddress": null,
      "address1_postalcode": null,
      "importsequencenumber": null,
      "ftpsiteurl": null,
      "address1_fax": null,
      "websiteurl": null,
      "address2_city": null,
      "address2_line1": null,
      "utcoffset": null,
      "_calendarid_value": null,
      "costcenter": null,
      "address1_telephone1": null,
      "address1_upszone": null,
      "address1_country": null,
      "fileasname": null,
      "address1_stateorprovince": null,
      "address1_longitude": null,
      "address1_line2": null,
      "address1_line1": null,
      "address2_country": null,
      "address1_latitude": null,
      "address2_county": null,
      "address2_longitude": null,
      "address2_telephone1": null,
      "exchangerate": null
    },
    ...
  ]
}
```


You can also use odata $filter to filter for a specific table-privilege:

```http
GET https://{DYNAMICS_ORG}.api.crm4.dynamics.com/api/data/v9.0/privileges?$filter=name eq 'prvRead{TABLE_SCHEMA_NAME}' HTTP/1.1
Content-Type: application/json
Authorization: Bearer {ACCESS_TOKEN}
```

### Add Privileges

For the **Depth** parameter you need to use one of the following **Names**.

> [!TIP]
> When you set **Privileges** via the **PowerPlattform Admin Center** the depth **Local** is used by default.

| Name | Value | Description |
| -- | -- | -- | 
| Basic | 0 | Indicates basic privileges. |
| Local | 1 | Indicates local privileges. |
| Deep | 2 | Indicates deep privileges. |
| Global | 3 | Indicates global privileges. |
| RecordFilter | 4 | Indicates privileges determined by associated RecordFilter. |

Now you just need to fill out the parameters finally add the privileges to a role.

#### Request
```http
POST https://{DYNAMICS_ORG}.crm4.dynamics.com//api/data/v9.0/roles({role_id})/Microsoft.Dynamics.CRM.AddPrivilegesRole HTTP/1.1
Content-Type: application/json
Authorization: Bearer {ACCESS_TOKEN}

{
  "Privileges": [
    {
      "Depth": "Local",
      "PrivilegeId": "{PRIVILEGE_GUID}",
      "BusinessUnitId": "{BUSINESS_UNIT_GUID}",
      "PrivilegeName": "prvRead{TABLE_SCHEMA_NAME}"
    }
  ]
}
```

#### Response
```json
HTTP/1.1 204 No Content
```
