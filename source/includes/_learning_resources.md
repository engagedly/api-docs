# Learning

The Learning endpoints expose your organisation's courses and playlists, their
content structure, and learner reporting data. They are read-only and served on
the `/beta` surface:

- `GET https://api.engagedly.com/beta/learning/resources` — list courses and playlists.
- `GET https://api.engagedly.com/beta/learning/resources/<ID>/contents` — the content hierarchy of one course/playlist.
- `GET https://api.engagedly.com/beta/learning/learner_reports` — learner enrolment data with course information.

Two identifiers appear throughout and are the stable keys you use to map records
back to your own data:

- `short_code` — the human-readable unique code of a course/playlist.
- `learning_resource_id` (also returned as `id` on the resource itself) — the internal unique ID of a course/playlist.

<aside class="notice">These endpoints are read-only.</aside>

## List Resources

`GET https://api.engagedly.com/beta/learning/resources`

Returns a paginated list of the organisation's learning resources (courses and
playlists). All parameters are optional; with none supplied the full org list is
returned, newest activity first.

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
search_text | string | Case-insensitive match on the resource title.
competency_search_text | string | Case-insensitive match on the resource's competency names.
types[] | array | Resource type(s). Values: `Course`, `Playlist`, `Section`. Example: `types[]=Course&types[]=Playlist`.
resource_ids[] | array | Restrict to specific resource IDs. Example: `resource_ids[]=1234`.
state[] | array | Publication state(s). Values: `unpublished`, `published`, `unpublished_edit`.
languages[] | array | Language code(s), e.g. `languages[]=en`.
providers[] | array | Content provider(s), e.g. `engagedly`, `udemy`, `go1`, `linkedin-learning`, `opensesame`, `bizz-library`, `thinkific-academy`, `learning-planet`.
authors[] | array | Restrict to resources by the given author user ID(s).
levels[] | array | Difficulty level(s), e.g. `Beginner`, `Intermediate`, `Advanced`.
tags[] | array | Restrict to the given tag(s).
durations[min_limit] / durations[max_limit] | object | Duration range in minutes. Example: `durations[min_limit]=30&durations[max_limit]=120`.
certified | boolean | When `true`, only resources that grant a certificate.
ratings | number | Minimum average rating (1–5).
in_library | boolean | When `true`, only resources in the content library.
short_code | string | Return the resource with this exact short code.
archived | boolean | When `true`, only archived resources; when `false` (default), only active ones.
sort | string | Sort field, optionally prefixed with `-` for descending order (ascending by default). One of `title`, `average_rating`, `published_on`, `created_at`, `updated_at`, `assigned_on`, `completed_at`. Example: `sort=-created_at`.
page | integer | Page number, starting at 1.
size | integer | Items per page. Maximum 50.

> Sample Request

```shell
curl "https://api.engagedly.com/beta/learning/resources?types[]=Course&page=1&size=25" \
  -H "ClientKey: xxxxxxxxxxxxxx" \
  -H "SecretKey: xxxxxxxxxxxxxx"
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
            "id": 1234,
            "title": "Workplace Safety Fundamentals",
            "description": "Core safety practices for the workplace.",
            "provider": "engagedly",
            "archived": false,
            "language": "en",
            "duration": "01:00:00",
            "short_code": "WSF-101",
            "level": "Beginner",
            "type": "Course",
            "state": "Published",
            "in_library": true,
            "published_on": "Jul 07, 2026",
            "average_rating": 4.5,
            "tags": ["compliance", "safety"],
            "competencies": [],
            "created_at": "Jun 01, 2026",
            "updated_at": "Jul 07, 2026",
            "cover_image": "https://social.engagedly.com/uploads/cover/file/1234/cover.jpg",
            "categories": [
                { "id": 5, "title": "Compliance" }
            ],
            "author": {
                "id": "c3d4e5f6-2718-4e45-9721-27535991becf",
                "name": "Course Author",
                "email": "author@teamyogi.com",
                "status": "Active",
                "manager": { "id": "a1b2c3d4-2718-4e45-9721-27535991becf", "name": "Jane Doe" },
                "designation": "L&D Manager",
                "display_picture": {}
            },
            "co_authors": [],
            "settings": {},
            "attributes": {},
            "content_details": null,
            "skills": []
        }
    ]
}
```

### Response Fields

<table>
  <tr>
    <th width="28%">ATTRIBUTE</th>
    <th width="16%">TYPE</th>
    <th width="56%">DESCRIPTION</th>
  </tr>
  <tr>
    <td>id</td>
    <td>integer</td>
    <td>Internal unique ID of the resource (the <code>learning_resource_id</code>). Use this to fetch its contents.</td>
  </tr>
  <tr>
    <td>title</td>
    <td>string</td>
    <td>Title of the course/playlist.</td>
  </tr>
  <tr>
    <td>description</td>
    <td>string</td>
    <td>Description text.</td>
  </tr>
  <tr>
    <td>provider</td>
    <td>string</td>
    <td>Content provider (for example <code>engagedly</code>).</td>
  </tr>
  <tr>
    <td>archived</td>
    <td>boolean</td>
    <td>Whether the resource is archived.</td>
  </tr>
  <tr>
    <td>language</td>
    <td>string</td>
    <td>Language code.</td>
  </tr>
  <tr>
    <td>duration</td>
    <td>string</td>
    <td>Estimated duration, formatted <code>HH:MM:SS</code>.</td>
  </tr>
  <tr>
    <td>short_code</td>
    <td>string</td>
    <td>Unique code of the resource. Use this to map to your own data.</td>
  </tr>
  <tr>
    <td>level</td>
    <td>string</td>
    <td>Difficulty level.</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Resource type: <code>Course</code>, <code>Playlist</code>, or <code>Section</code>.</td>
  </tr>
  <tr>
    <td>state</td>
    <td>string</td>
    <td>Publication state: <code>Published</code>, <code>Unpublished</code>, or <code>UnpublishedEdit</code>.</td>
  </tr>
  <tr>
    <td>in_library</td>
    <td>boolean</td>
    <td>Whether the resource is in the content library.</td>
  </tr>
  <tr>
    <td>published_on</td>
    <td>string</td>
    <td>Date the resource was published, or <code>null</code>.</td>
  </tr>
  <tr>
    <td>average_rating</td>
    <td>number</td>
    <td>Average learner rating (1–5), or <code>null</code>.</td>
  </tr>
  <tr>
    <td>tags</td>
    <td>array</td>
    <td>Free-form tags.</td>
  </tr>
  <tr>
    <td>competencies</td>
    <td>array</td>
    <td>Associated competencies.</td>
  </tr>
  <tr>
    <td>categories</td>
    <td>array</td>
    <td>Categories the resource belongs to (each <code>{ id, title }</code>).</td>
  </tr>
  <tr>
    <td>author</td>
    <td>object</td>
    <td>The resource author. For provider content this carries the provider's display name and logo.</td>
  </tr>
  <tr>
    <td>co_authors</td>
    <td>array</td>
    <td>Additional authors/maintainers.</td>
  </tr>
  <tr>
    <td>skills</td>
    <td>array</td>
    <td>Associated skills.</td>
  </tr>
  <tr>
    <td>created_at / updated_at</td>
    <td>string</td>
    <td>Creation and last-update dates.</td>
  </tr>
</table>

## Get Resource Contents

`GET https://api.engagedly.com/beta/learning/resources/<ID>/contents`

Returns the ordered content hierarchy of a single course or playlist. A course
is organised into **sections**, each containing **units** (the individual
content items — attachments, rich text, links, quizzes, videos, SCORM/AICC/LTI
packages, etc.). A playlist instead nests child resources under `contents`.
Only **published** content is returned (the learner view).

### URL Parameters

Parameter | Description
--------- | -----------
ID | The `learning_resource_id` of the course/playlist (the `id` from the List Resources response).

> Sample Request

```shell
curl "https://api.engagedly.com/beta/learning/resources/1234/contents" \
  -H "ClientKey: xxxxxxxxxxxxxx" \
  -H "SecretKey: xxxxxxxxxxxxxx"
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
            "id": 4567,
            "title": "Getting Started",
            "description": "Introduction to the course.",
            "type": "Section",
            "status": "Published",
            "ongoing_edit": false,
            "position": 1,
            "content_status": "Published",
            "units": [
                {
                    "id": 8901,
                    "title": "Welcome",
                    "description": "A short intro video.",
                    "type": "VideoContent",
                    "position": 1,
                    "duration": 5,
                    "unit_details": {},
                    "status": "Active",
                    "content_status": "Active",
                    "ongoing_edit": false,
                    "mark_for_deletion": false,
                    "has_impact": false,
                    "completion_watch_threshold_pct": null,
                    "completion_time_threshold_pct": null,
                    "completion_require_scroll": false,
                    "created_at": "2026-06-01T10:00:00.000Z",
                    "updated_at": "2026-07-07T10:00:00.000Z"
                },
                {
                    "id": 8902,
                    "title": "Safety Quiz",
                    "description": "Check your understanding.",
                    "type": "Quiz",
                    "position": 2,
                    "duration": 10,
                    "unit_details": {},
                    "status": "Active",
                    "content_status": "Active",
                    "ongoing_edit": false,
                    "mark_for_deletion": false,
                    "has_impact": false,
                    "completion_watch_threshold_pct": null,
                    "completion_time_threshold_pct": null,
                    "completion_require_scroll": false,
                    "created_at": "2026-06-01T10:05:00.000Z",
                    "updated_at": "2026-07-07T10:05:00.000Z"
                }
            ]
        }
    ]
}
```

### Response Fields

Each element of `data` is a **section**:

<table>
  <tr>
    <th width="28%">ATTRIBUTE</th>
    <th width="16%">TYPE</th>
    <th width="56%">DESCRIPTION</th>
  </tr>
  <tr>
    <td>id</td>
    <td>integer</td>
    <td>Section ID.</td>
  </tr>
  <tr>
    <td>title / description</td>
    <td>string</td>
    <td>Section title and description.</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Always <code>Section</code>.</td>
  </tr>
  <tr>
    <td>status</td>
    <td>string</td>
    <td>Publication state of the section.</td>
  </tr>
  <tr>
    <td>position</td>
    <td>integer</td>
    <td>Order of the section within the resource.</td>
  </tr>
  <tr>
    <td>content_status</td>
    <td>string</td>
    <td>One of <code>Published</code>, <code>Unpublished</code>, <code>UnpublishedEdit</code>, <code>MarkedForDeletion</code>.</td>
  </tr>
  <tr>
    <td>units</td>
    <td>array</td>
    <td>The content items in the section (present for courses). Playlists carry nested resources under <code>contents</code> instead.</td>
  </tr>
</table>

Each element of `units` is a content item:

<table>
  <tr>
    <th width="28%">ATTRIBUTE</th>
    <th width="16%">TYPE</th>
    <th width="56%">DESCRIPTION</th>
  </tr>
  <tr>
    <td>id</td>
    <td>integer</td>
    <td>Unit ID.</td>
  </tr>
  <tr>
    <td>title / description</td>
    <td>string</td>
    <td>Unit title and description.</td>
  </tr>
  <tr>
    <td>type</td>
    <td>string</td>
    <td>Content type: <code>Attachment</code>, <code>RichText</code>, <code>Link</code>, <code>Quiz</code>, <code>SurveyStep</code>, <code>VideoContent</code>, <code>InstructorTraining</code>, <code>SCORM</code>, <code>AICC</code>, or <code>LTI</code>.</td>
  </tr>
  <tr>
    <td>position</td>
    <td>integer</td>
    <td>Order of the unit within the section.</td>
  </tr>
  <tr>
    <td>duration</td>
    <td>integer</td>
    <td>Estimated duration in minutes.</td>
  </tr>
  <tr>
    <td>unit_details</td>
    <td>object</td>
    <td>Type-specific detail (varies by <code>type</code> — e.g. a link URL, attachment file, quiz configuration, video source).</td>
  </tr>
  <tr>
    <td>status</td>
    <td>string</td>
    <td><code>Active</code> or <code>Draft</code>.</td>
  </tr>
  <tr>
    <td>content_status</td>
    <td>string</td>
    <td>One of <code>Active</code>, <code>Draft</code>, <code>UnpublishedEdit</code>, <code>MarkedForDeletion</code>.</td>
  </tr>
  <tr>
    <td>completion_watch_threshold_pct / completion_time_threshold_pct / completion_require_scroll</td>
    <td>mixed</td>
    <td>Completion criteria for the unit, where configured.</td>
  </tr>
  <tr>
    <td>created_at / updated_at</td>
    <td>string</td>
    <td>Creation and last-update timestamps.</td>
  </tr>
</table>
