# Businesses

## List all businesses

`GET https://api.engagedly.com/beta/businesses`

> Sample Request

```shell
GET https://api.engagedly.com/beta/businesses
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
        "total_records": 2
    },
    "data": [
        {
            "id": "f5afec62-21ff-40d3-a06e-9a2162ef6b69",
            "name": "Manufacturing Unit",
            "members_count": "10",
            "administrators_count": "2"
        },
        {
            "id": "23eceer-21ff-23cd-a06e-9a2162ef6b69",
            "name": "EMCA-Unit",
            "members_count": "5",
            "administrators_count": "1"
        }
    ]
}
```

## Get a single business

`GET https://api.engagedly.com/beta/businesses/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the business

> Sample Request

```shell
GET https://api.engagedly.com/api/beta/businesses/23eceer-21ff-23cd-a06e-9a2162ef6b69
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
       "id": "23eceer-21ff-23cd-a06e-9a2162ef6b69",
       "name": "EMCA-Unit",
       "members_count": 1,
       "administrators_count": 1,
       "members": [
           {
               "id": "a178a039-4e79-4e3e-87f0-c88440a6d8c6",
               "name": "ROBERT J  Jacob",
               "email": "robert.jacob@engagedly.com",
               "first_name": "ROBERT",
               "middle_name": "J",
               "last_name": "Jacob",
               "display_picture": {
                   "medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
                   "small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
               },
               "is_admin": false
           }
       ]
   }

}
```

## Create a new business

`POST https://api.engagedly.com/beta/businesses`

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
    <td>Name of the business</td>
  </tr>
  <tr>
    <td>members</td>
    <td>array</td>
    <td>Array of user ids</td>
  </tr>
</table>

> Sample Request

```shell
POST https://api.engagedly.com/api/beta/businesses
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
       "id": "23eceer-21ff-23cd-a06e-9a2162ef6b69",
       "name": "EMCA-Unit",
       "members_count": 1,
       "administrators_count": 1,
       "members": [
           {
               "id": "a178a039-4e79-4e3e-87f0-c88440a6d8c6",
               "name": "ROBERT J  Jacob",
               "email": "robert.jacob@engagedly.com",
               "first_name": "ROBERT",
               "middle_name": "J",
               "last_name": "Jacob",
               "display_picture": {
                   "medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
                   "small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
               },
               "is_admin": false
           }
       ]
   }
}
```

## Update an existing business

`PUT https://api.engagedly.com/beta/businesses/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the business

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
    <td>Name of the business</td>
  </tr>
  <tr>
    <td>members</td>
    <td>array</td>
    <td>Array of user ids</td>
  </tr>
</table>

> Sample Request

```shell

PUT https://api.engagedly.com/beta/businesses/23eceer-21ff-23cd-a06e-9a2162ef6b69

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
       "id": "23eceer-21ff-23cd-a06e-9a2162ef6b69",
       "name": "EMCA-Unit-Updated",
       "members_count": 1,
       "administrators_count": 1,
       "members": [
           {
               "id": "a178a039-4e79-4e3e-87f0-c88440a6d8c6",
               "name": "ROBERT J  Jacob",
               "email": "robert.jacob@engagedly.com",
               "first_name": "ROBERT",
               "middle_name": "J",
               "last_name": "Jacob",
               "display_picture": {
                   "medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
                   "small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
               },
               "is_admin": false
           }
       ]
   }
}
```

## Delete a business

`DELETE https://api.engagedly.com/beta/businesses/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the business

> Sample Request

```shell
DELETE https://api.engagedly.com/beta/businesses/23eceer-21ff-23cd-a06e-9a2162ef6b69
```

> Sample Response

```http
204 No Content
```
