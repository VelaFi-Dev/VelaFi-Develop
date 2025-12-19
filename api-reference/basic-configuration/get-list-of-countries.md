---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/kcqCFfOVAdQbR1YyMZUY/api-reference/basic-configuration/get-list-of-countries
---

# Get List of Countries

This section details the API endpoint used to retrieve a list of countries. It provides options to filter the results based on their validity.

#### Endpoint Information

* **Request Method**: `GET`
* **Request Path**: `/v2/base/countrys`

#### Request Parameters

**Query Parameters**

| Parameter  | Type    | Required | Description                                                                                                    |
| ---------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------- |
| hasFindAll | boolean | No       | Whether to query all countries (default is `false` for valid countries only). Use `true` to get all countries. |

#### Response Structure

The response will contain the following fields:

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [{
        "country": "Mexico",  // Name of the country
        "abbr": "MX"          // ISO 3166-1 code of the country
    }]
}
```

#### Example Response

```json
{
    "code": 200,
    "msg": "SUCCESS",
    "data": [
        {
            "country": "Mexico",
            "abbr": "MX"
        },
        {
            "country": "Argentina",
            "abbr": "AR"
        },
        {
            "country": "Brazil",
            "abbr": "BR"
        }
        // Additional countries may be included
    ]
}
```

### Notes

* By default, the API only returns valid countries unless `hasFindAll` is set to `true`.
* The response includes both the country name and its corresponding ISO 3166-1 code for easy reference.
