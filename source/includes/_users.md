# Users

## List all users

`GET http://api.engagedly.com/platform/beta/users`

> Sample Request

```shell
GET http://api.engagedly.com/platform/beta/users
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
			"id": "b62167d0-2718-4e45-9721-27535991becf",
			"name": "Adam Smith",
			"status": "Active",
			"email": "adam.smith@teamyogi.com",
			"first_name": "Adam",
			"middle_name": null,
			"last_name": "Smith",
			"display_picture": {
				"medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
				"small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
			},
			"job_title": {
				"id": "261",
				"name": "CEO"
			},
			"location": {
				"id": "11",
				"name": "United States"
			}
		}
	]
}
```

## Get a single user

`GET http://api.engagedly.com/platform/beta/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user

> Sample Request

```shell
GET https://api.engagedly.con/api/platform/beta/users/b62167d0-2718-4e45-9721-27535991becf
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
		"id": "b62167d0-2718-4e45-9721-27535991becf",
		"name": "Adam Smith",
		"status": "Active",
		"email": "adam.smith@teamyogi.com",
		"first_name": "Adam",
		"middle_name": null,
		"last_name": "Smith",
		"education": "BS- Anthropology, Stanford University",
		"about_me": "I love exploring whether it is in business or ancient sites. Lets discover together.",
		"display_picture": {
			"medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
			"large": "https://social.engagedly.com/uploads/picture/file/9634/large_thumbnail_Denzel.jpg",
			"small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
		},
		"job_title": {
		"id": "261",
		"name": "CEO"
		},
    	"joining_date": null,
		"location": {
		"id": "11",
		"name": "United States"
		},
		"departments": [
			{
            	"id": "1",
            	"name": "Customer Support",
            	"is_admin" : true
       		 }
		]
  	}
}
```

## Create a new user

`POST http://api.engagedly.com/platform/beta/users`

### Parameters

<table>
	<tr>
		<th width="30%">ATTRIBUTE</th>
		<th width="30%">TYPE</th>
		<th width="60%">DESCRIPTION</th>
	</tr>
	<tr>
		<td>first_name </td>
		<td>string</td>
		<td>First name of the user</td>
	</tr>
	<tr>
		<td>middle_name</td>
		<td>string</td>
		<td>Middle name of the user</td>
	</tr>
	<tr>
		<td>last_name</td>
		<td>string</td>
		<td>Last name of the user</td>
	</tr>
	<tr>
		<td>email</td>
		<td>string</td>
		<td>Email Id of the user</td>
	</tr>
	<tr>
		<td>employee_id</td>
		<td>string</td>
		<td>Employee Id</td>
	</tr>
	<tr>
		<td>joining_date</td>
		<td>date</td>
		<td>Date of which employee was hired</td>
	</tr>
	<tr>
		<td>birth_date</td>
		<td>date</td>
		<td>Date of birth of the user</td>
	</tr>
	<tr>
		<td>location</td>
		<td>string</td>
		<td>Id of the location</td>
	</tr>
	<tr>
		<td>job_title</td>
		<td>string</td>
		<td>Id of the job title</td>
	</tr>
	<tr>
		<td>departments</td>
		<td>array of department ids</td>
		<td>Array of departments for which this use would be part of</td>
	</tr>
</table>

> Sample Request

```shell
POST http://api.engagedly.com/platform/beta/users
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
		"id": "b62167d0-2718-4e45-9721-27535991becf",
		"name": "Adam Smith",
		"status": "Active",
		"email": "adam.smith@teamyogi.com",
		"first_name": "Adam",
		"middle_name": null,
		"last_name": "Smith",
		"education": "BS- Anthropology, Stanford University",
		"about_me": "I love exploring whether it is in business or ancient sites. Lets discover together.",
		"display_picture": {
			"medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
			"large": "https://social.engagedly.com/uploads/picture/file/9634/large_thumbnail_Denzel.jpg",
			"small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
		},
		"job_title": {
		"id": "261",
		"name": "CEO"
		},
    	"joining_date": null,
		"location": {
		"id": "11",
		"name": "United States"
		},
		"departments": [
			{
            	"id": "1",
            	"name": "Customer Support",
            	"is_admin" : true
       		 }
		]
  	}
}
```

## Update an existing user

`PUT http://api.engagedly.com/platform/beta/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user

### Parameters

<table>
	<tr>
		<th width="30%">ATTRIBUTE</th>
		<th width="30%">TYPE</th>
		<th width="60%">DESCRIPTION</th>
	</tr>
	<tr>
		<td>first_name </td>
		<td>string</td>
		<td>First name of the user</td>
	</tr>
	<tr>
		<td>middle_name</td>
		<td>string</td>
		<td>Middle name of the user</td>
	</tr>
	<tr>
		<td>last_name</td>
		<td>string</td>
		<td>Last name of the user</td>
	</tr>
	<tr>
		<td>email</td>
		<td>string</td>
		<td>Email Id of the user</td>
	</tr>
	<tr>
		<td>employee_id</td>
		<td>string</td>
		<td>Employee Id</td>
	</tr>
	<tr>
		<td>joining_date</td>
		<td>date</td>
		<td>Date of which employee was hired</td>
	</tr>
	<tr>
		<td>birth_date</td>
		<td>date</td>
		<td>Date of birth of the user</td>
	</tr>
	<tr>
		<td>location</td>
		<td>string</td>
		<td>Id of the location</td>
	</tr>
	<tr>
		<td>job_title</td>
		<td>string</td>
		<td>Id of the job title</td>
	</tr>
	<tr>
		<td>departments</td>
		<td>array of department ids</td>
		<td>Array of departments for which this use would be part of</td>
	</tr>
</table>

> Sample Request

```shell
PUT https://api.engagedly.con/api/platform/beta/users/b62167d0-2718-4e45-9721-27535991becf
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
		"id": "b62167d0-2718-4e45-9721-27535991becf",
		"name": "Adam Smith",
		"status": "Active",
		"email": "adam.smith@teamyogi.com",
		"first_name": "Adam",
		"middle_name": null,
		"last_name": "Smith",
		"education": "BS- Anthropology, Stanford University",
		"about_me": "I love exploring whether it is in business or ancient sites. Lets discover together.",
		"display_picture": {
			"medium": "https://social.engagedly.com/uploads/picture/file/9634/reduced_Denzel.jpg",
			"large": "https://social.engagedly.com/uploads/picture/file/9634/large_thumbnail_Denzel.jpg",
			"small": "https://social.engagedly.com/uploads/picture/file/9634/small_Denzel.jpg"
		},
		"job_title": {
		"id": "261",
		"name": "CEO"
		},
    	"joining_date": null,
		"location": {
		"id": "11",
		"name": "United States"
		},
		"departments": [
			{
            	"id": "1",
            	"name": "Customer Support",
            	"is_admin" : true
       		 }
		]
  	}
}
```