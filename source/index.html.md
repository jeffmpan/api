---
title: API Reference

language_tabs:
  - curl

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

SWITCH.CM builds distribution platforms for airlines & hotels.  Our API will allow you to seamlessly synchronize the following data with thousands of booking websites:

- pricing & availability data
- guest reservation data

# Test Environment

To start, we’ll set up the following development environments:

- a test xxx.switch.cm account (to simulate a real property)
- a test booking.com account (to simulate your inventory on an OTA)

> To authorize, use this code:

```curl
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "X-Switch-Token: yourtokengoeshere"
```

> Make sure to replace `yourtokengoeshere` with your API key.

# API's

## Room List Request (Send)

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/api/room/create</h6>
	</div>
</div>

```shell
curl -k  -L -X POST -H 'X-Switch-Token: 8c6zfkwf4a1160ankv6r48rve' -H 'Content-Type: application/json' -d '{
  "property_id": "25",
  "rooms": [
    {
      "name": "Mixed Dorm",
      "price": "200.00",
      "type": "base",
      "labels": [
        {
          "name": "room a"
        },
        {
          "name": "room b"
        }
      ]
    },
    {
      "name": "Female Dorm",
      "price": "300.00",
      "type": "base",
      "labels": [
        {
          "name": "room 1"
        }
      ]
    }
  ]
}' 'https://api.switch.dev/api/room/create'
```

> JSON:

```json
{
  "property_id": "25",
  "rooms": [
    {
      "name": "Mixed Dorm",
      "price": "200.00",
      "type": "base",
      "labels": [
        {
          "name": "room a"
        },
        {
          "name": "room b"
        }
      ]
    },
    {
      "name": "Female Dorm",
      "price": "300.00",
      "type": "base",
      "labels": [
        {
          "name": "room 1"
        }
      ]
    }
  ]
}
```


### Parameters

Parameter | Description
--------- | -----------
property_id | The ID of the property

