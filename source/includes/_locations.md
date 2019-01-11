# Locations

## List all locations

`GET https://api.engagedly.com/beta/locations`

> Sample Request

```shell
GET https://api.engagedly.com/beta/locations
```

> Sample Response

```http
200 OK
content-type: application/json
```

```json
{
    "success": true,
    "pagination": {
        "page": 1,
        "size": 30,
        "has_more": false,
        "total_records": 1
    },
    "data": [
        {
            "id": "1",
            "name": "Head Office",
            "address_line1": "",
            "address_line2" : "",
            "city": "",
            "state": "",
            "country" : "",
            "postal_code" : ""
        }
    ]
}
```

## Get a single location

`GET https://api.engagedly.com/beta/locations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

> Sample Request

```shell
GET https://api.engagedly.com/api/beta/locations/1
```

> Sample Response

```http
200 OK
content-type: application/json
```

```json
{
    "success": true,
    "data": {
        "id": "1",
        "name": "Head Office",
        "address_line1": "",
        "address_line2" : "",
        "city": "",
        "state": "",
        "country" : "",
        "postal_code" : ""
    }
}
```

## Create a new location

`POST https://api.engagedly.com/beta/locations`

### Parameters

<table>
  <tr>
    <th width="30%">ATTRIBUTE</th>
    <th width="30%">TYPE</th>
    <th width="60%">DESCRIPTION</th>
  </tr>
  <tr>
    <td>name </td>
    <td>string</td>
    <td>Name of the location</td>
  </tr>
  <tr>
    <td>address_line1</td>
    <td>string</td>
    <td>Line 1 of the address</td>
  </tr>
  <tr>
    <td>address_line2</td>
    <td>string</td>
    <td>Line 2 of the address</td>
  </tr>
  <tr>
    <td>city</td>
    <td>string</td>
    <td>City of the location</td>
  </tr>
  <tr>
    <td>state</td>
    <td>string</td>
    <td>State of the location</td>
  </tr>
  <tr>
    <td>country</td>
    <td>string</td>
    <td>Country of the location</td>
  </tr>
    <tr>
    <td>postal_code</td>
    <td>string</td>
    <td>Postal code of the location</td>
  </tr>
</table>

> Sample Request

```shell
POST https://api.engagedly.com/api/beta/locations
```

> Sample Response

```http
201 Created
content-type: application/json
```

```json
{
    "success": true,
    "data": {
        "id": "1",
        "name": "Head Office",
        "address_line1": "",
        "address_line2" : "",
        "city": "",
        "state": "",
        "country" : "",
        "postal_code" : ""
    }
}
```

## Update an existing location

`PUT https://api.engagedly.com/beta/locations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

### Parameters

<table>
  <tr>
    <th width="30%">ATTRIBUTE</th>
    <th width="30%">TYPE</th>
    <th width="60%">DESCRIPTION</th>
  </tr>
  <tr>
    <td>name </td>
    <td>string</td>
    <td>Name of the location</td>
  </tr>
  <tr>
    <td>address_line1</td>
    <td>string</td>
    <td>Line 1 of the address</td>
  </tr>
  <tr>
    <td>address_line2</td>
    <td>string</td>
    <td>Line 2 of the address</td>
  </tr>
  <tr>
    <td>city</td>
    <td>string</td>
    <td>City of the location</td>
  </tr>
  <tr>
    <td>state</td>
    <td>string</td>
    <td>State of the location</td>
  </tr>
  <tr>
    <td>country</td>
    <td>string</td>
    <td>Country of the location</td>
  </tr>
    <tr>
    <td>postal_code</td>
    <td>string</td>
    <td>Postal code of the location</td>
  </tr>
</table>


> Sample Request

```shell
PUT https://api.engagedly.com/api/beta/locations/1
```

> Sample Response

```http
200 OK
content-type: application/json
```

```json
{
    "success": true,
    "data": {
        "id": "1",
        "name": "Head Office",
        "address_line1": "",
        "address_line2" : "",
        "city": "",
        "state": "",
        "country" : "",
        "postal_code" : ""
    }
}
```

## Delete a location 

`DELETE https://api.engagedly.com/beta/locations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

> Sample Request

```shell
DELETE https://api.engagedly.com/api/beta/locations/1
```

> Sample Response

```http
204 No Content
```