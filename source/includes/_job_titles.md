# Job Titles

## List all job titles

`GET http://api.engagedly.com/platform/beta/job_titles`

> Sample Request

```shell
GET http://api.engagedly.com/platform/beta/job_titles
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
            "description": "",
            "responsibilities": ""
        }
    ]
}
```

## Get a single job title

`GET http://api.engagedly.com/platform/beta/job_titles/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the job title

> Sample Request

```shell
GET https://api.engagedly.con/api/platform/beta/job_titles/1
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
        "description": "",
        "responsibilities": ""
    }
}
```

## Create a new job title

`POST http://api.engagedly.com/platform/beta/job_titles`

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
    <td>Name of the job title</td>
  </tr>
  <tr>
    <td>description</td>
    <td>string</td>
    <td>Description of the job title</td>
  </tr>
  <tr>
    <td>responsibilities</td>
    <td>string</td>
    <td>Responsibilities of the job titles</td>
  </tr>
</table>

> Sample Request

```shell
POST  https://api.engagedly.con/api/platform/beta/job_titles
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
        "description": "",
        "responsibilities": ""
    }
}
```


## Update an existing job title

`PUT http://api.engagedly.com/platform/beta/job_titles/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the job title

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
    <td>Name of the job title</td>
  </tr>
  <tr>
    <td>description</td>
    <td>string</td>
    <td>Description of the job title</td>
  </tr>
  <tr>
    <td>responsibilities</td>
    <td>string</td>
    <td>Responsibilities of the job titles</td>
  </tr>
</table>

> Sample Request

```shell
PUT https://api.engagedly.con/api/platform/beta/job_titles/1
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
        "description": "",
        "responsibilities": ""
    }
}
```

## Delete a job title 

`DELETE http://api.engagedly.com/platform/beta/job_titles/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the job title 

> Sample Request

```shell
DELETE https://api.engagedly.con/api/platform/beta/job_titles/1
```

> Sample Response

```http
204 No Content
```
