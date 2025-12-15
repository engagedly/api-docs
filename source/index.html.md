---
title: Engagedly API Reference

language_tabs:
  - shell

includes:
  - user_attributes
  - users
  - departments
  - businesses
  - locations
  - job_titles
  - permissions
  - activities

search: true

api_endpoint: https://api.engagedly.com/beta
---

# Introduction

Engagedly is a cloud based new age Performance Management Software that redefines performance appraisals by simplifying and incorporating elements of employee engagement into the performance review process.

Engagedly API are designed to be REST (**Representational State Transfer**) APIs. These 'RESTful' APIs allows operations such as reading, modifying, adding or deleting data from your Engagedly Instance.

<aside class="notice">Engagedly APIs does not support Cross-Origin Resource Sharing (CORS).</aside>

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
curl "https://api.engagedly.com/beta/users"
  -H "ClientKey: xxxxxxxxxxxxxx"
  -H "SecretKey: xxxxxxxxxxxxxx"
```

## Requests

All Engagedly APIs require specifying an API version in the request URL. The most current version of the API is beta. API endpoint for the current beta version is

`https://api.engagedly.com/beta/`

<aside class="notice">All API requests must be made over HTTPS. Calls made over plain HTTP will fail.</aside>

### JSON Bodies

All POST, PUT, PATCH requests are JSON encoded and must have have content type of application/json, or the API will return a 415 Unsupported Media Type status code.

```shell
$ curl https://api.engagedly.com/beta/users/b62167d0-2718-4e45-9721-27535991becf \
    -X PUT \
    -H 'Content-Type: application/json' \
    -H "ClientKey: xxxxxxxxxxxxxx" \
    -H "SecretKey: xxxxxxxxxxxxxx" \
    -d '{"first_name":"John"}'

```

### API Commands

Engagedly APIs are plain JSON over HTTP and use the following HTTP verbs:

| COMMAND | PURPOSE                     |
| ------- | --------------------------- |
| GET     | To get one or more entities |
| POST    | To create an entity         |
| PUT     | To update an entity         |
| DELETE  | To delete an entity         |

## Responses

All response bodies are JSON encoded.

A single resource is represented as a JSON object. A collection of resources is represented as a JSON array of objects

Blank fields will be included as a null instead of ommited. If the field is an array, it will be included as an empty array i.e. [].

Timestamps are in UTC and formatted as ISO8601.

## HTTP Status Codes

Engagedly uses conventional HTTP status codes to indicate success or failure of an API call. In general, status codes in the 2xx range means success, 4xx range means there was an error in the provided information, and those in the 5xx range indicates server side errors. Commonly used HTTP status codes are listed below.

| CODE | DESCRIPTION                                                                                                                          |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------ |
| 200  | OK -- Everything worked as expected.                                                                                                 |
| 201  | Created -- The request was a success and one or more resources have been created.                                                    |
| 204  | No Content - Request succeeded, but no response body.                                                                                |
| 400  | Bad Request -- The request cannot be performed. Usually because of malformed parameter or missing parameter.                         |
| 401  | Unauthorized -- Request was rejected because of invalid AuthToken.                                                                   |
| 402  | Request Failed -- The parameters were valid but the request failed.                                                                  |
| 403  | Forbidden -- The user does not have enough permission or possibly not an user of the respective organization to access the resource. |
| 404  | Not Found -- The URL you’ve sent is wrong. It’s possible that the resource you’ve requested has been moved to another URL.           |
| 405  | Method Not Allowed -- The requested resource does not support the HTTP method used.                                                  |
| 406  | Not Acceptable -- The requested response type is not supported by the client.                                                        |
| 409  | Conflict -- The request conflicts with another request (perhaps due to using the same idempotent key).                               |
| 415  | Unsupported Media Type - POST/PUT/PATCH request occurred without a application/json content type.                                    |
| 422  | Unprocessable Entry - A request to modify or create a resource failed due to a validation error.                                     |
| 429  | Too Many Requests -- Too many requests within a certain time frame.                                                                  |
| 500  | Server Errors -- Something went wrong on Engagedly's end.                                                                            |

### Error Response

In addition to the HTTP status code, most errors will also return a response body that contains more information for debugging the error.

**Error Type**

| TYPE                  | DESCRIPTION                                                                                                                                          |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| api_connection_error  | Could not connect to Engagedly API                                                                                                                   |
| authentication_error  | Could not authenticate properly                                                                                                                      |
| invalid_request_error | Invalid request errors arise when your request has invalid parameters.                                                                               |
| validation_error      | Errors triggered by our client-side libraries when failing to validate fields (e.g., when a card number or expiration date is invalid or incomplete) |

**Error Codes**

> Sample Error Response

```json
{
  "error_type": "validation_error",
  "errors": [
    {
      "field": "name",
      "message": "Mandatory attribute missing",
      "code": "missing_field"
    },
    {
      "field": "code",
      "message": "Value already existing",
      "code": "duplicate_value"
    }
  ]
}
```

## Pagination

Most of the API responses that returns the list of objects are paginated. The parameters that control the pagination are 'page' and 'size', indicating the page number and the items per page values. Within the response, a pagination attribute will be set and will contain the provided 'page' and 'size' along with 'has_more' and 'record_count' indicating whether there are more items that can be fetched and total number of records.

The page number starts with 1 and by default the number of records returned are 25. The maximum number of records (size) that can be returned is 50.
