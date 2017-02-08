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

### HTTP Request

`POST https://api.switch.dev/api/room/fetch`

```shell
curl -k  -L -X POST -H 'X-Switch-Token: 8c6zfkwf4a1160ankv6r48rve' -H 'Content-Type: application/json' -d '{
  "property_id": "25"
}' 'https://api.switch.dev/api/room/fetch'
```

> JSON RESPONSE:

```json
{
  "rooms": [
    {
      "name": "Master Suite",
      "id": "4",
      "room_type": "base",
      "base_price": "45.00",
      "labels": [
        {
          "id": "57",
          "name": "A"
        },
        {
          "id": "58",
          "name": "B"
        },
        {
          "id": "59",
          "name": "C"
        },
        {
          "id": "60",
          "name": "D"
        },
        {
          "id": "61",
          "name": "E"
        }
      ]
    },
    {
      "name": "Mixed Dorm",
      "id": "5",
      "room_type": "base",
      "base_price": "20.00",
      "labels": [
        {
          "id": "62",
          "name": "A-1"
        },
        {
          "id": "63",
          "name": "A-2"
        },
        {
          "id": "64",
          "name": "A-3"
        },
        {
          "id": "65",
          "name": "A-4"
        },
        {
          "id": "66",
          "name": "B-1"
        },
        {
          "id": "67",
          "name": "B-2"
        },
        {
          "id": "68",
          "name": "B-3"
        },
        {
          "id": "69",
          "name": "B-4"
        }
      ]
    }
  ]
}
```


### Parameters

Parameter | Description | Mandatory
--------- | ----------- | ---------
property_id | The ID of the property | *



## Create Rooms API

To create room

### HTTP Request

`POST https://api.switch.dev/api/room/create`

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



### Parameters

Parameter | Description | Mandatory
--------- | ----------- | ---------
property_id | The ID of the property | *
rooms | Multiple rooms  | *
name | name of the room  | *


## Create Reservation API

????

### HTTP Request

`POST https://api.switch.dev/api/reservation/create`

```shell
curl -k  -L -X POST -H 'X-Switch-Token: 8c6zfkwf4a1160ankv6r48rve' -H 'Content-Type: application/json' -d '{
  "property_id": "25",
  "reservations": [
      {
        "booking_id": "101657667746",
        "booking_date": "2017-02-17",
        "organiser_name": "John Doe",
        "rooms": [
          {
            "booked_room": "4",
            "status": "waiting for guest",
            "check_in": "2017-02-17",
            "check_out": "2017-02-19",
            "guest": {
              "name": "John Doe",
              "email": "476115+bulk@switch.cm",
              "phone": "6478219711",
              "address": "90 queens drive",
              "city": "Toronto",
              "zip": "M6l3e2"
            },
            "nights": [
              {
                "date": "2017-02-17",
                "price": "149.00",
                "assigned_room": "57"
              },
              {
                "date": "2017-02-18",
                "price": "275.00",
                "assigned_room": "57"
              }
            ]
          }
        ]
      },
      {
        "booking_id": "101657667747",
        "booking_date": "2017-02-17",
        "organiser_name": "John Doe2",
        "rooms": [
          {
            "booked_room": "4",
            "status": "waiting for guest",
            "check_in": "2017-02-19",
            "check_out": "2017-02-20",
            "guest": {
              "name": "John Doe2",
              "email": "476115+bulk@switch.cm",
              "phone": "6478219711",
              "address": "100 queens drive",
              "city": "Toronto",
              "zip": "M6l3e2"
            },
            "nights": [
              {
                "date": "2017-02-19",
                "price": "149.00",
                "assigned_room": "58"
              }
            ]
          }
        ]
      }
    ]
}' 'https://api.switch.dev/api/reservation/create'
```



### Parameters

Parameter | Description | Mandatory
--------- | ----------- | ---------
property_id | The ID of the property | *
rooms | Multiple rooms  | *
name | name of the room  | *



## Modify Reservation API

????

### HTTP Request

`POST https://api.switch.dev/api/reservation/modify`

```shell
curl -k  -L -X POST -H 'X-Switch-Token: 8c6zfkwf4a1160ankv6r48rve' -H 'Content-Type: application/json' -d '{
  "property_id": "25",
  "reservations": [
      {
        "booking_id": "101657667746",
        "booking_date": "2017-02-17",
        "organiser_name": "John Doe",
        "rooms": [
          {
            "booked_room": "4",
            "status": "waiting for guest",
            "check_in": "2017-02-17",
            "check_out": "2017-02-19",
            "guest": {
              "name": "John Doe",
              "email": "476115+bulk@switch.cm",
              "phone": "6478219711",
              "address": "90 queens drive",
              "city": "Toronto",
              "zip": "M6l3e2"
            },
            "nights": [
              {
                "date": "2017-02-17",
                "price": "149.00",
                "assigned_room": "57"
              },
              {
                "date": "2017-02-18",
                "price": "275.00",
                "assigned_room": "57"
              }
            ]
          }
        ]
      },
      {
        "booking_id": "101657667747",
        "booking_date": "2017-02-17",
        "organiser_name": "John Doe2",
        "rooms": [
          {
            "booked_room": "4",
            "status": "waiting for guest",
            "check_in": "2017-02-19",
            "check_out": "2017-02-20",
            "guest": {
              "name": "John Doe2",
              "email": "476115+bulk@switch.cm",
              "phone": "6478219711",
              "address": "100 queens drive",
              "city": "Toronto",
              "zip": "M6l3e2"
            },
            "nights": [
              {
                "date": "2017-02-19",
                "price": "149.00",
                "assigned_room": "58"
              }
            ]
          }
        ]
      }
    ]
}' 'https://api.switch.dev/api/reservation/modify'
```



### Parameters

Parameter | Description | Mandatory
--------- | ----------- | ---------
property_id | The ID of the property | *
rooms | Multiple rooms  | *
name | name of the room  | *

