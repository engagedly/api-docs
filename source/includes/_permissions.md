# Permissions

## List all permissions

`GET https://api.engagedly.com/beta/permissions`

> Sample Request

```shell
GET https://api.engagedly.com/beta/permissions
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
        "size": 25,
        "has_more": false,
        "total_records": 1
    },
    "data": [
        {
            "id": 1,
            "name": "Site Administrator",
            "is_admin": true,
            "description": "This role will be by default given to the admin. This role will contain all the permission. This role cannot be seperately given or remove to any other user. The user that has been marked as the org admin will by default get this role and will be removed from the role when the user is removed from the admin"
        }
    ]
}
```