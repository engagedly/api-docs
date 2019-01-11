# Departments

## List all departments

`GET https://api.engagedly.com/beta/departments`

> Sample Request

```shell
GET https://api.engagedly.com/beta/departments
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
        "total_records": 5
    },
    "data": [
        {
            "id": "f5afec62-21ff-40d3-a06e-9a2162ef6b69",
            "name": "Customer Support",
            "members_count": "10",
            "administrators_count": "2"
        }
    ]
}
```

## Get a single department

`GET https://api.engagedly.com/beta/departments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the department

> Sample Request

```shell
GET https://api.engagedly.com/api/beta/departments/f5afec62-21ff-40d3-a06e-9a2162ef6b69
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
        "id": "f5afec62-21ff-40d3-a06e-9a2162ef6b69",
        "name": "Customer Support",
        "members_count": "10",
        "administrators_count": "2",
        "members": [
            {
                "id": "b62167d0-2718-4e45-9721-27535991becf",
                "name": "Adam Smith",
                "email": "adam.smith@teamyogi.com",
                "first_name": "Adam",
                "middle_name": null,
                "last_name": "Smith",
                "display_picture": {
                    "medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
                    "small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
                },
                "is_admin": true
            },
        ]
    }
}
```

## Create a new department

`POST https://api.engagedly.com/beta/departments`

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
    <td>Name of the department</td>
  </tr>
  <tr>
    <td>members</td>
    <td>array</td>
    <td>Array of user ids</td>
  </tr>
</table>

> Sample Request

```shell
POST https://api.engagedly.com/api/beta/departments
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
        "id": "f5afec62-21ff-40d3-a06e-9a2162ef6b69",
        "name": "Customer Support",
        "members_count": "10",
        "administrators_count": "2",
        "members": [
            {
                "id": "b62167d0-2718-4e45-9721-27535991becf",
                "name": "Adam Smith",
                "email": "adam.smith@teamyogi.com",
                "first_name": "Adam",
                "middle_name": null,
                "last_name": "Smith",
                "display_picture": {
                    "medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
                    "small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
                },
                "is_admin": true
            },
        ]
    }
}
```

## Update an existing department

`PUT https://api.engagedly.com/beta/departments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the department

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
    <td>Name of the department</td>
  </tr>
  <tr>
    <td>members</td>
    <td>array</td>
    <td>Array of user ids</td>
  </tr>
</table>

> Sample Request

```shell

PUT https://api.engagedly.com/beta/departments/f5afec62-21ff-40d3-a06e-9a2162ef6b69

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
        "name": "Customer Support",
        "members": [
            {
                "id": "b62167d0-2718-4e45-9721-27535991becf",
                "name": "Adam Smith",
                "email": "adam.smith@teamyogi.com",
                "first_name": "Adam",
                "middle_name": null,
                "last_name": "Smith",
                "display_picture": {
                    "medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
                    "small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
                },
                "is_admin": true
            },
        ]
    }
}
```

## Delete a department

`DELETE https://api.engagedly.com/beta/departments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the department

> Sample Request

```shell
DELETE https://api.engagedly.com/beta/departments/f5afec62-21ff-40d3-a06e-9a2162ef6b69
```

> Sample Response

```http
204 No Content
```
