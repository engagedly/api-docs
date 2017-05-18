---
title: Engagedly API Reference

language_tabs:
  - shell

search: true
---

# Introduction

Engagedly is a cloud based new age Performance Management Software that redefines performance appraisals by simplifying and incorporating elements of employee engagement into the performance review process.

Engagedly API are designed to be REST (**Representational State Transfer**) APIs. These 'RESTful' APIs allows operations such as reading, modifying, adding or deleting data from your Engagedly Instance.

<aside class="notice">Engagedly APIs does not support Cross-Origin Resource Sharing (CORS).</aside>

### API Commands

Engagedly APIs are plain JSON over HTTP and use the following HTTP verbs:

COMMAND   | PURPOSE
--------- | --------------------------
GET       | To get one or more entities
POST      | To create an entity
PUT       | To update an entity
DELETE    | To delete an entity


### API Versioning and Structure

All Engagedly APIs require specifying an API version in the request URL.  The most current version of the API is beta. API endpoint for the current beta version is   

`https://api.engagedly.com/platform/beta/`  

<aside class="notice">All API requests must be made over HTTPS. Calls made over plain HTTP will fail.</aside>

# Getting Started

## Authentication
Each call to the API is authenticated by including your client key and secret key in the request. Client key and secret key are obtained and managed through Engagedly Portal. Please read the instructions below in order to obtained your client key and secret key. 

Please note that you need to have Site Administrator account to obtain the keys and these keys will carry the permissions of the user who has generated them.

### Obtaining your client key and secret key

You can obtain your client key and secret key from settings page after login into Engagedly as Site Administrator. You can generate the client key and secret key after navigating to Integrations and then to Engagedly API. 

<aside class="notice">The secret key will be shown only once so make sure you copy it</aside>

### Authenticating the request

To authenticate the API call, client key and secret key needs to be included as part of the header.

> Sample Request

```shell
curl "http://api.engagedly.com/platform/beta/users"
  -H "ClientKey: xxxxxxxxxxxxxx"
  -H "SecretKey: xxxxxxxxxxxxxx"
```

## Schema

**Blank Fields**  
Blank fields are included as null instead of being omitted.  

**Date Input**  
Input for date fields is expected to be in one of the following formats
YYYY-MM-DD   
YYYY-MM-DDTHH:MM  

## Errors
Engagedly uses conventional HTTP status codes to indicate success or failure of an API call. In general, status codes in the 2xx range means success, 4xx range means there was an error in the provided information, and those in the 5xx range indicates server side errors. Commonly used HTTP status codes are listed below.

CODE | DESCRIPTION
---  | ------------
200  | OK -- Everything worked as expected.
201  | Created -- The request was a success and one or more resources have been created.
400  | Bad Request -- The request cannot be performed. Usually because of malformed parameter or missing parameter.
401  | Unauthorized -- Request was rejected because of invalid AuthToken.
402  | Request Failed -- The parameters were valid but the request failed.
403  | Forbidden -- The user does not have enough permission or possibly not an user of the respective organization to access the resource.
404  | Not Found -- The URL you’ve sent is wrong. It’s possible that the resource you’ve requested has been moved to another URL.
405  | Method Not Allowed -- The requested resource does not support the HTTP method used. 
406  | Not Acceptable -- The requested response type is not supported by the client.
409  | Conflict -- The request conflicts with another request (perhaps due to using the same idempotent key).
429  | Too Many Requests -- Too many requests within a certain time frame.
500  | Server Errors -- Something went wrong on Stripe's end. (These are rare.)


In addition to the HTTP status code, most errors will also return a response body that contains more information for debugging the error.

# Users

## Get All Users

```shell
curl "http://api.engagedly.com/platform/beta/users"
  -H "ClientKey: xxxxxxxxxxxxxx"
  -H "SecretKey: xxxxxxxxxxxxxx"
```

> Sample Response

```json
{
  "success": true,
  "data": [
    {
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
        "passport": "https://social.engagedly.com/uploads/picture/file/9634/passport_Denzel.jpg",
        "thumb": "https://social.engagedly.com/uploads/picture/file/9634/thumb_Denzel.jpg",
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
    }]
}
```

This endpoint returns all the users

### HTTP Request

`GET http://api.engagedly.com/platform/beta/users`

## Get User Details

```shell
curl "https://api.engagedly.con/api/platform/beta/users/b62167d0-2718-4e45-9721-27535991becf"
  -H "ClientKey: xxxxxxxxxxxxxx"
  -H "SecretKey: xxxxxxxxxxxxxx"
```

> Sample Response

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
      "passport": "https://social.engagedly.com/uploads/picture/file/9634/passport_Denzel.jpg",
      "thumb": "https://social.engagedly.com/uploads/picture/file/9634/thumb_Denzel.jpg",
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

This endpoint returns the details of the user

### HTTP Request

`GET http://api.engagedly.com/platform/beta/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve


## Create a User

> Sample Request

```shell

$ curl https://api.engagedly.con/api/platform/beta/users
-H "Content-Type: application/json;charset=UTF-8"
-H "ClientKey: xxxxxxxxxxxxxx"
-H "SecretKey: xxxxxxxxxxxxxx"
-d '{
    "first_name": "Adam",
    "middle_name": "",
    "last_name": "smith",
    "email": "adam.smith@teamyogi.com",
    "employee_id": "0001",
    "joining_date": "2014-01-01",
    "birthdate": "1980-12-12"
}'

```

> Sample Response

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
    "education": null,
    "about_me": null,
    "display_picture": {
    },
    "job_title": {
    },
    "joining_date": "2014-01-01",
    "location": {
    }
  }
}
```

This endpoint creates a user in your organization

### HTTP Request
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
    <td>birthdate</td>
    <td>date</td>
    <td>Date of birth of the user</td>
  </tr>
</table>

## Update a user

> Sample Request

```shell

$ curl https://api.engagedly.con/api/platform/beta/users/b62167d0-2718-4e45-9721-27535991becf
-H "Content-Type: application/json;charset=UTF-8"
-H "ClientKey: xxxxxxxxxxxxxx"
-H "SecretKey: xxxxxxxxxxxxxx"
-d '{
    "first_name": "Adam",
    "middle_name": "",
    "last_name": "smith",
    "email": "adam.smith@teamyogi.com",
    "employee_id": "0001",
    "joining_date": "2014-01-01",
    "birthdate": "1980-12-12"
}'

```

> Sample Response

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
    "education": null,
    "about_me": null,
    "display_picture": {
    },
    "job_title": {
    },
    "joining_date": "2014-01-01",
    "location": {
    }
  }
}
```

Updates a user in your organization

### HTTP Request
`PUT http://api.engagedly.com/platform/beta/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to update

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
</table>


