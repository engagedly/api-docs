# Activities

## Get all public Praises

`GET https://api.engagedly.com/beta/activities/praises`

> Sample Request

```shell
GET https://api.engagedly.com/beta/activities/praises
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
        "page": 2,
        "size": 50,
        "has_more": false,
        "total_records": 1
    },
    "data": [
        {
            "id": 107781,
            "activity_type": "Praise",
            "activity_date": "2019-01-30T06:56:24.895Z",
            "last_updated_at": "2019-01-30T06:56:24.895Z",
            "title": null,
            "content": "goodd work...",
            "pinned": false,
            "author": {
                "name": "Aaron Kutcher",
                "id": "9fcb1375-e11a-4492-b7e8-39d3912231dd",
                "display_picture": {
                    "large": "http://social.engagedly.local:3005/uploads/picture/file/3073/reduced_images__2_.jpg",
                    "original": "http://social.engagedly.local:3005/uploads/picture/file/3073/images__2_.jpg",
                    "reduced": "http://social.engagedly.local:3005/uploads/picture/file/3073/reduced_images__2_.jpg"
                },
                "designation": "Promoter"
            },
            "audience": [
                {
                    "name": "Everyone",
                    "id": "6e9c487c-c23a-44ec-9fe6-a4a4e527552c",
                    "display_picture": {
                        "large": null,
                        "original": null,
                        "reduced": null
                    },
                    "type": "Group"
                }
            ],
            "links": [],
            "attachments": [],
            "comment_details": {
                "count": 0
            },
            "like_details": {
                "count": 0,
                "is_liked": false
            },
            "can_edit": true,
            "can_delete": true,
            "recognized_actors": [
                {
                    "name": "Looks L  Das",
                    "id": "e5838577-2612-44f8-a684-167fdcf2e524",
                    "display_picture": {
                        "large": null,
                        "original": null,
                        "reduced": null
                    },
                    "designation": "Accountant"
                }
            ]
        },
        {
            "id": 107780,
            "activity_type": "Praise",
            "activity_date": "2019-01-30T06:54:25.287Z",
            "last_updated_at": "2019-01-30T06:54:25.287Z",
            "title": null,
            "content": "good work...",
            "pinned": false,
            "author": {
                "name": "Aaronn Astons",
                "id": "9fcb1375-e11a-4492-b7e8-39d3912231dd",
                "display_picture": {
                    "large": "http://social.engagedly.local:3005/uploads/picture/file/3073/reduced_images__2_.jpg",
                    "original": "http://social.engagedly.local:3005/uploads/picture/file/3073/images__2_.jpg",
                    "reduced": "http://social.engagedly.local:3005/uploads/picture/file/3073/reduced_images__2_.jpg"
                },
                "designation": "Promoter"
            },
            "audience": [
                {
                    "name": "Everyone",
                    "id": "6e9c487c-c23a-44ec-9fe6-a4a4e527552c",
                    "display_picture": {
                        "large": null,
                        "original": null,
                        "reduced": null
                    },
                    "type": "Group"
                }
            ],
            "links": [],
            "attachments": [],
            "comment_details": {
                "count": 0
            },
            "like_details": {
                "count": 0,
                "is_liked": false
            },
            "can_edit": true,
            "can_delete": true,
            "recognized_actors": [
                {
                    "name": "Looks L  Das",
                    "id": "e5838577-2612-44f8-a684-167fdcf2e524",
                    "display_picture": {
                        "large": null,
                        "original": null,
                        "reduced": null
                    },
                    "designation": "Accountant"
                }
            ]
        }
      ]
    }
```
