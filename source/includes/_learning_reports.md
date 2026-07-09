## Learner Report

The Learner Report endpoint returns learner data together with course
information for your organisation. Each row represents one learner's enrolment
in one course (a learner is the pairing of a user and a course), and carries the
unique identifiers you can use to map the data back to your own records:

- `learner.id` — the user's unique Engagedly ID (stable across Engagedly services).
- `short_code` — the unique code of the course; use this to map rows to your course data.
- `learning_resource_id` — the internal unique ID of the course.

`GET https://api.engagedly.com/beta/learning/learner_reports`

### Query Parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
resource_types[] | array | no | Resource type(s) to report on. Values `Course`, `Playlist`. Both are returned when omitted. Example: `resource_types[]=Course`.
learning_resource_id | integer | no | Restrict the report to a single course by its internal ID.
learning_resource_ids[] | array | no | Restrict the report to specific courses by internal ID. Example: `learning_resource_ids[]=1234&learning_resource_ids[]=5678`.
page | integer | no | Page number, starting at 1.
size | integer | no | Items per page. Maximum 50.
filter_hash | object | no | Column filtering and sorting. See Filtering and Sorting below.

### Filtering and Sorting

Column filtering and sorting are passed through the `filter_hash` parameter. Under `filter`, each key is a column; the payload shape depends on the column's data type (the four shapes are described below). `sort` takes a single field and direction.

> filter_hash structure

```json
{
  "filter_hash": {
    "filter": {
      "completion_status": { "values": ["Completed"] },
      "assigned_on": { "type": "inRange", "dateFrom": "2026-01-01", "dateTo": "2026-06-30" }
    },
    "sort": { "field_name": "completed_on", "order": "desc" }
  }
}
```

#### Text filters

Case-insensitive "contains" match.

> Text filter payload

```json
{ "filter": "acme" }
```

Key | Filters on
--- | ----------
title | Course title
categories | Course category title
language | Course language
learner_name | Learner name
learner_email | Learner email
learner_manager_name | Learner's manager name
learner_hr_managers | Learner's HR manager name
learner_secondary_managers | Learner's secondary manager name
learner_employee_id | Learner's employee ID
resource_assigner_name | Assigner name
author_name | Course author name
author_email | Course author email (Engagedly-authored courses only)

#### Set filters

One or more allowed values.

> Set filter payload

```json
{ "values": ["Completed", "Failed"] }
```

Fixed-value keys:

Key | Allowed values
--- | --------------
completion_status | `Completed`, `In Progress`, `Not Started`, `Failed`, `Evaluation Pending`
compliance_status | `Compliant`, `Not Compliant`, `null`
certified | `Yes`, `No`
mandatory | `Yes`, `No`
self_enrolled | `Yes`, `No`
archived | `Yes`, `No`
learner_status | `Active`, `Blocked`
learner_differently_abled | `Yes`, `No`
learner_veteran_status | `Yes`, `No`
provider | `Engagedly`, `Udemy`, `Go1`, `BizLibrary`, `LinkedIn Learning`, `OpenSesame`, `Engagedly Academy`, `Learning Planet`

Open-ended keys — values are your organisation's configured strings:

Key | Filters on
--- | ----------
learner_job_title | Job title
learner_location | Location
learner_department | Department
learner_business_units | Business unit
learner_employee_type | Employee type
learner_gender | Gender
learner_ethnicity | Ethnicity

#### Date filters

An operator (`type`) with one or two dates in `YYYY-MM-DD` format. Single-date operators use only `dateFrom`.

> Date filter payload

```json
{ "type": "inRange", "dateFrom": "2026-01-01", "dateTo": "2026-06-30" }
```

Key | Supported operators (`type`)
--- | ----------------------------
assigned_on | `equals`, `inRange`, `assignedBefore` (`lessThan`), `assignedAfter` (`greaterThan`)
due_date | `equals`, `inRange`, `With Due Date`, `Without Due Date`
completed_on | `equals`, `inRange`
compliant_till | `equals`, `inRange`, `null`
learner_birthdate | `equals`, `inRange`
learner_hire_date | `equals`, `inRange`

`With Due Date`, `Without Due Date`, and `null` require no date value.

#### Number filters

A numeric value passed as a string.

> Number filter payload

```json
{ "filter": "5" }
```

Key | Meaning
--- | -------
points | Exact points earned
overall_time_taken | Time spent, in minutes
delay_in_days | Days completed past the due date
learner_age | Age in years

`overdue_by` (number of days overdue) additionally supports operators — `equals`, `inRange`, `greaterThan`, `lessThan` — where `inRange` uses `filter` and `filterTo`:

> overdue_by payload

```json
{ "type": "inRange", "filter": "1", "filterTo": "30" }
```

#### Custom demographic fields

Organisation-specific custom fields can be filtered with a `learner_custom_<fieldKey>` key, using whichever payload shape (text, set, or date) matches the field.

#### Sorting

Sort with `filter_hash.sort`, where `order` is `asc` or `desc`.

> Sort payload

```json
{ "field_name": "completed_on", "order": "desc" }
```

Sortable `field_name` values: `assigned_on`, `due_date`, `completion_status`, `compliance_status`, `completed_on`, `compliant_till`, `overall_time_taken`, `certified`, `points`, `provider`, `title`, `learner_name`, `resource_assigner_name`, `learner_manager_name`, `language`, `learner_email`, `author_name`, `author_email`, `overdue_by`.

> Sample Request

```shell
curl "https://api.engagedly.com/beta/learning/learner_reports?resource_types[]=Course&page=1&size=25" \
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
            "id": 90210,
            "learning_resource_id": 1234,
            "learning_resource_title": "Workplace Safety Fundamentals",
            "short_code": "WSF-101",
            "completion_status": "Completed",
            "points": 100,
            "completed_on": "Jul 07, 2026",
            "certified": true,
            "mandatory": true,
            "progress": 100,
            "provider": "engagedly",
            "archive": false,
            "categories": [
                { "id": 5, "title": "Compliance" }
            ],
            "learner": {
                "id": "b62167d0-2718-4e45-9721-27535991becf",
                "name": "Adam Smith",
                "email": "adam.smith@teamyogi.com",
                "status": "Active",
                "manager": { "id": "a1b2c3d4-2718-4e45-9721-27535991becf", "name": "Jane Doe" }
            },
            "assigner": {
                "id": "a1b2c3d4-2718-4e45-9721-27535991becf",
                "name": "Jane Doe",
                "email": "jane.doe@teamyogi.com"
            },
            "manager": { "id": "a1b2c3d4-2718-4e45-9721-27535991becf", "name": "Jane Doe" },
            "hr_managers": [],
            "secondary_managers": [],
            "author": {
                "id": "c3d4e5f6-2718-4e45-9721-27535991becf",
                "name": "Course Author"
            },
            "assigned_on": "Jun 01, 2026",
            "overall_time_taken": 3600,
            "due_date": "Jul 10, 2026",
            "delay_in_days": null,
            "language": "en",
            "learning_resource_duration": 3600,
            "compliance_status": "Compliant",
            "valid_till": null,
            "is_self_assigned": false
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
    <td>Unique ID of this learner enrolment record.</td>
  </tr>
  <tr>
    <td>learning_resource_id</td>
    <td>integer</td>
    <td>Internal unique ID of the course.</td>
  </tr>
  <tr>
    <td>learning_resource_title</td>
    <td>string</td>
    <td>Title of the course.</td>
  </tr>
  <tr>
    <td>short_code</td>
    <td>string</td>
    <td>Unique code of the course. Use this to map the row to your course data.</td>
  </tr>
  <tr>
    <td>completion_status</td>
    <td>string</td>
    <td>One of <code>Not Started</code>, <code>In Progress</code>, <code>Completed</code>, <code>Failed</code>, <code>Evaluation Pending</code>.</td>
  </tr>
  <tr>
    <td>points</td>
    <td>integer</td>
    <td>Points earned.</td>
  </tr>
  <tr>
    <td>completed_on</td>
    <td>string</td>
    <td>Date the learner completed the course, or <code>null</code>.</td>
  </tr>
  <tr>
    <td>certified</td>
    <td>boolean</td>
    <td>Whether the learner is certified.</td>
  </tr>
  <tr>
    <td>mandatory</td>
    <td>boolean</td>
    <td>Whether the course is mandatory for the learner.</td>
  </tr>
  <tr>
    <td>progress</td>
    <td>integer</td>
    <td>Completion percentage.</td>
  </tr>
  <tr>
    <td>provider</td>
    <td>string</td>
    <td>Content provider (for example <code>engagedly</code>).</td>
  </tr>
  <tr>
    <td>archive</td>
    <td>boolean</td>
    <td>Whether the course is archived.</td>
  </tr>
  <tr>
    <td>categories</td>
    <td>array</td>
    <td>Categories the course belongs to.</td>
  </tr>
  <tr>
    <td>learner</td>
    <td>object</td>
    <td>The learner. <code>learner.id</code> is the user's unique Engagedly ID. Includes name, email, status, manager, and available demographic fields.</td>
  </tr>
  <tr>
    <td>assigner</td>
    <td>object</td>
    <td>The user who assigned the course, or <code>null</code>.</td>
  </tr>
  <tr>
    <td>manager</td>
    <td>object</td>
    <td>The learner's manager, or <code>null</code>.</td>
  </tr>
  <tr>
    <td>hr_managers</td>
    <td>array</td>
    <td>The learner's HR managers.</td>
  </tr>
  <tr>
    <td>secondary_managers</td>
    <td>array</td>
    <td>The learner's secondary managers.</td>
  </tr>
  <tr>
    <td>author</td>
    <td>object</td>
    <td>The course author, or <code>null</code>.</td>
  </tr>
  <tr>
    <td>assigned_on</td>
    <td>string</td>
    <td>Date the course was assigned.</td>
  </tr>
  <tr>
    <td>overall_time_taken</td>
    <td>integer</td>
    <td>Total time spent, in seconds.</td>
  </tr>
  <tr>
    <td>due_date</td>
    <td>string</td>
    <td>Due date, or <code>null</code>.</td>
  </tr>
  <tr>
    <td>delay_in_days</td>
    <td>integer</td>
    <td>Days completed past the due date, or <code>null</code>.</td>
  </tr>
  <tr>
    <td>language</td>
    <td>string</td>
    <td>Course language.</td>
  </tr>
  <tr>
    <td>learning_resource_duration</td>
    <td>integer</td>
    <td>Estimated course duration, in seconds.</td>
  </tr>
  <tr>
    <td>compliance_status</td>
    <td>string</td>
    <td>Compliance status, where applicable.</td>
  </tr>
  <tr>
    <td>valid_till</td>
    <td>string</td>
    <td>Date the completion is valid until (for recurring courses), or <code>null</code>.</td>
  </tr>
  <tr>
    <td>is_self_assigned</td>
    <td>boolean</td>
    <td>Whether the learner self-enrolled.</td>
  </tr>
</table>
