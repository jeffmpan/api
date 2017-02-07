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

SWITCH.CM builds distribution platforms for airlines & hotels.  Our API allows you to seamlessly synchronize the following data with thousands of booking websites:

- pricing & availability data
- guest reservation data

# Test Environment

To start, you'll have the following development environments:

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

## Retrieve Rooms API

SWITCH.CM uses the Retrieve Rooms message to retrieve a list of active rooms for a property.

## What is the Retrieved Rooms API use for? ##

The Retrieve Rooms API allows users of the SWITCH.CM channel manager to see what rooms & rate plans are available to map to your booking channel.  Without the Retrieve Rooms API, SWITCH.CM doesn't have any knowledge of the rooms & rate plans you wish to receive availability & rates for.  Below is a screenshot of where the information you provide on the Retrieve Rooms API is utilized.

Please ONLY return a list of 'Active' Room Code & Rate Code combinations in your Retrieved Rooms API.

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

