# Users

## List all users

`GET https://api.engagedly.com/beta/users`

### URL Parameters for extra information

Parameter | Description
--------- | -----------
include | primary_reporter,direct_reports

> Sample Request

```shell
GET https://api.engagedly.com/beta/users
```
> Sample Request with extra information

```shell
GET https://api.engagedly.com/beta/users?include=primary_reporter,direct_reports
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
			"employee_id": "E007",
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

`GET https://api.engagedly.com/beta/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user

### URL Parameters for extra information

Parameter | Description
--------- | -----------
include | direct_reports

> Sample Request

```shell
GET https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf
```

> Sample Request with extra information

```shell
GET https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf?include=direct_reports
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
		"employee_id": "E007",
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

`POST https://api.engagedly.com/beta/users`

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
POST https://api.engagedly.com/beta/users
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
		"employee_id": "E007",
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

`PUT https://api.engagedly.com/beta/users/<ID>`

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
PUT https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf
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
		"employee_id": "E007",
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

## Update user's profile picture

`PUT https://api.engagedly.com/beta/users/<ID>/profile/picture`

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
		<td>profile_picture </td>
		<td>array</td>
		<td>bytes of the picture</td>
	</tr>
</table>

> Sample Request

```shell
PUT https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf/profile/picture
```

> Sample Response

```http
200 OK
content-type: application/json
```

```json
{
  	"success": true
}
```

## Deactivate an user

`PUT https://api.engagedly.com/beta/users/<ID>/deactivate`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user


> Sample Request

```shell
PUT https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf/deactivate
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
		"status": "Blocked",
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
		}
  	}
}
```

## Activate an user

`PUT https://api.engagedly.com/beta/users/<ID>/activate`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user


> Sample Request

```shell
PUT https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf/activate
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
		}
  	}
}
```

## Permissions of an user

`GET https://api.engagedly.com/beta/users/<ID>/permissions`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user


> Sample Request

```shell
GET https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf/permissions
```

> Sample Response

```http
200 OK
content-type: application/json
```

```json
{
    "success": true,
    "data": [
        {
            "id": 1,
            "name": "Cycle - create / edit / delete performance review cycles",
            "is_admin": null,
            "description": ""
        },
        {
            "id": 2,
            "name": "Site Administrator",
            "is_admin": true,
            "description": "This role will be by default given to the admin. This role will contain all the permission. This role cannot be seperately given or remove to any other user. The user that has been marked as the org admin will by default get this role and will be removed from the role when the user is removed from the admin"
        }
    ]
}
```

## Update permissions of an user

`PUT https://api.engagedly.com/beta/users/<ID>/permissions`

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
		<td>permission_ids </td>
		<td>array</td>
		<td>array of permissions ids</td>
	</tr>
</table>


> Sample Request

```shell
PUT https://api.engagedly.com/api/beta/users/b62167d0-2718-4e45-9721-27535991becf/permissions
```

> Sample Response

```http
200 OK
content-type: application/json
```

```json
{
    "success": true,
    "data": [
        {
            "id": 2070,
            "name": "Cycle - create / edit / delete performance review cycles",
            "is_admin": null,
            "description": ""
        },
        {
            "id": 45,
            "name": "Site Administrator",
            "is_admin": true,
            "description": "This role will be by default given to the admin. This role will contain all the permission. This role cannot be seperately given or remove to any other user. The user that has been marked as the org admin will by default get this role and will be removed from the role when the user is removed from the admin"
        }
    ]
}
```
