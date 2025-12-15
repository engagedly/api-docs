# User Attributes

The User Attributes system provides organizations with the flexibility to capture and store additional information specific to individual users beyond the standard system fields. This enhanced user management system allows for better data organization, reporting, and user-specific customization.

### Types of Attributes

**System Attributes**

These are built-in attributes provided by the Engagedly platform.
They cover standard HR and user profile information and cannot be deleted (though visibility and usage may be configurable depending on your setup).Predefined by the Engagedly system.

Identified in configuration by: `preset: true`

**Custom Attributes**

These are organization-defined attributes created to support specific business rules, workflows, or reporting needs.Fully configurable by your organization. Can be added/modified as your business evolves

Identified in configuration by: `preset: false`

Custom attributes are generally referenced using keys like:

- `custom-attribute-93cbf`
- `custom-attribute-d3b49`

### Important Notes

- **Mandatory Fields**: Required attributes (`mandatory: true`) must be provided during user creation and user updation
- **Select Options**: For single-select and multiple-select attributes, use the `value` from `attribute_options` array
- **Boolean Field**: For boolean field true/false values are only accepted
- **Date Format**: Dates can be passed in either of the following formats:
  - `MMM DD, YYYY` (e.g., `Jan 02, 2022`)
  - `YYYY-MM-DD` (e.g., `2024-01-15`)

## List all user attributes

`GET https://api.engagedly.com/beta/user-attributes`

### Description

Retrieves all available user attributes including both system attributes and custom attributes. This endpoint returns the details about each attribute including field configurations, validation rules, and available options.

> Sample Request

```shell
GET https://api.engagedly.com/beta/user-attributes
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
      "name": "Title",
      "attribute_key": "title",
      "preset": true,
      "mandatory": false,
      "data_type": "single-select",
      "attribute_options": [
        {
          "id": 313,
          "value": "Mr."
        },
        {
          "id": 314,
          "value": "Ms."
        },
        {
          "id": 315,
          "value": "Mrs."
        },
        {
          "id": 316,
          "value": "Dr."
        },
        {
          "id": 317,
          "value": "Mx."
        }
      ]
    },
    {
      "id": 33,
      "name": "Gender",
      "attribute_key": "gender",
      "preset": true,
      "mandatory": false,
      "data_type": "single-select",
      "attribute_options": [
        {
          "id": 11,
          "value": "Male"
        },
        {
          "id": 12,
          "value": "Female"
        },
        {
          "id": 13,
          "value": "Other"
        }
      ]
    },
    {
      "id": 17,
      "name": "Email",
      "attribute_key": "email",
      "preset": true,
      "mandatory": true,
      "data_type": "text",
      "attribute_options": null
    },
    {
      "id": 2,
      "name": "First Name",
      "attribute_key": "first_name",
      "preset": true,
      "mandatory": true,
      "data_type": "text",
      "attribute_options": null
    },
    {
      "id": 4,
      "name": "Last Name",
      "attribute_key": "last_name",
      "preset": true,
      "mandatory": true,
      "data_type": "text",
      "attribute_options": null
    },
    {
      "id": 22,
      "name": "Departments",
      "attribute_key": "departments",
      "preset": true,
      "mandatory": false,
      "data_type": "multiple-select",
      "attribute_options": []
    },
    {
      "id": 23,
      "name": "Business Units",
      "attribute_key": "business_units",
      "preset": true,
      "mandatory": false,
      "data_type": "multiple-select",
      "attribute_options": []
    },
    {
      "id": 865,
      "name": "Department",
      "attribute_key": "custom-attribute-93cbf",
      "preset": false,
      "mandatory": true,
      "data_type": "text",
      "attribute_options": null
    },
    {
      "id": 866,
      "name": "Employee Grade",
      "attribute_key": "custom-attribute-d3b49",
      "preset": false,
      "mandatory": false,
      "data_type": "number",
      "attribute_options": null
    },
    {
      "id": 867,
      "name": "Hire Date",
      "attribute_key": "custom-attribute-f622b",
      "preset": false,
      "mandatory": false,
      "data_type": "date",
      "attribute_options": null
    },
    {
      "id": 868,
      "name": "Performance Rating",
      "attribute_key": "custom-attribute-eb39c",
      "preset": false,
      "mandatory": false,
      "data_type": "single-select",
      "attribute_options": [
        {
          "id": 605,
          "value": "Exceeds Expectations"
        },
        {
          "id": 606,
          "value": "Meets Expectations"
        },
        {
          "id": 607,
          "value": "Below Expectations"
        },
        {
          "id": 608,
          "value": "Needs Improvement"
        }
      ]
    },
    {
      "id": 869,
      "name": "Skills",
      "attribute_key": "custom-attribute-f0453",
      "preset": false,
      "mandatory": false,
      "data_type": "multiple-select",
      "attribute_options": [
        {
          "id": 607,
          "value": "JavaScript"
        },
        {
          "id": 608,
          "value": "Python"
        },
        {
          "id": 872,
          "value": "Project Management"
        },
        {
          "id": 873,
          "value": "Leadership"
        },
        {
          "id": 874,
          "value": "Communication"
        },
        {
          "id": 875,
          "value": "Data Analysis"
        }
      ]
    },
    {
      "id": 870,
      "name": "Remote Work Eligible",
      "attribute_key": "custom-attribute-cabda",
      "preset": false,
      "mandatory": false,
      "data_type": "boolean",
      "attribute_options": null
    }
  ]
}
```

### Response Fields

| Field             | Type    | Description                                                                                     |
| ----------------- | ------- | ----------------------------------------------------------------------------------------------- |
| id                | integer | Unique identifier for the user attribute                                                        |
| name              | string  | Display name of the attribute                                                                   |
| attribute_key     | string  | Internal key used in API requests (e.g., "custom-attribute-93cbf")                              |
| preset            | boolean | Denotes whether a system attribute. Value is set true for system and false for custom attribute |
| mandatory         | boolean | Denotes whether this attribute is required                                                      |
| data_type         | string  | Type of field. Option are text, number, date, boolean, single-select and multiple-select        |
| attribute_options | array   | List options for select, multi-select attributes                                                |

### Supported Data Types

| Data Type       | Description                   | Example Values                                            | Use Cases                              |
| --------------- | ----------------------------- | --------------------------------------------------------- | -------------------------------------- |
| text            | Free text input               | "Engineering", "Marketing Manager"                        | Names, descriptions, free-form text    |
| number          | Numeric input                 | 5, 8.5, 10                                                | Grades, ratings, quantities            |
| date            | Date input                    | "2024-01-15", "2024-12-31"                                | Hire dates, birth dates, deadlines     |
| boolean         | True/false input              | true, false                                               | Yes/no questions, flags                |
| single-select   | Single choice from options    | "Exceeds Expectations", "Meets Expectations"              | Categories, status, single choice      |
| multiple-select | Multiple choices from options | ["JavaScript", "Python"], ["Leadership", "Communication"] | Skills, interests, multiple categories |
