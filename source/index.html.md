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
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# API's

## Room List Request (Send)

## New Event Webhook (Receive)

The Booking Notification API allows partners to receive new, modified or cancelled reservations in near real time, as customers make these bookings.

As this is a notification-based API, where Switch initiates the notifications, partners interested in implementing this API need to contact Switch to get started. It is possible to gain access to a test system that will generate booking notifications to the address of your choice. In order to get started with this, please contact info@switch.cm .

> Response:

```json
{
  "switchcm_id": "16",
  "total_bookings": 2,
  "bookings": [
    {
      "ota_id": 5,
      "booking_id": "1455994472",
      "booking_date": "2016-12-02",
      "organiser_name": "Julio Edwards",
      "rooms": [
        {
          "ota_room_name": "Single Bed in Mixed Dormitory Room",
          "check_in": "2016-12-03",
          "check_out": "2016-12-05",
          "pms_room_type": "189",
          "room_rate_name": "Standard Rate",
          "room_rate_id": "3977877",
          "status": "waiting for guest",
          "total_price": "90.00",
          "taxes": 0,
          "comission": "13.50",
          "room_type": "189",
          "room_rate": "3977877",
          "switch_id": "1821",
          "guests": [
            {
              "name": "Julio Edwards",
              "email": "tteste.848138@guest.booking.com"
            }
          ],
          "nights": [
            {
              "date": "2016-12-03",
              "price": "45.00"
            },
            {
              "date": "2016-12-04",
              "price": "45.00"
            }
          ]
        }
      ],
      "cc": [],
      "note": "I am travelling for business and I may be using a business credit card.You have a booker that prefers communication by emailhi"
    },
    {
      "ota_id": 5,
      "booking_id": "1765547633",
      "booking_date": "2016-12-02",
      "organiser_name": "John Doe",
      "rooms": [
        {
          "ota_room_name": "",
          "check_in": "2016-12-03",
          "check_out": "2016-12-05",
          "pms_room_type": "17",
          "room_rate_name": "",
          "room_rate_id": null,
          "status": "waiting for guest",
          "total_price": "90.00",
          "taxes": 0,
          "comission": "13.50",
          "room_type": "17",
          "room_rate": null,
          "switch_id": "1820",
          "guests": [
            {
              "name": "John Doe",
              "email": "tteste.950791@guest.booking.com"
            }
          ],
          "nights": [
            {
              "date": "2016-12-03",
              "price": "45.00"
            },
            {
              "date": "2016-12-04",
              "price": "45.00"
            }
          ]
        }
      ],
      "cc": [],
      "note": "I am travelling for business and I may be using a business credit card.You have a booker that prefers communication by emailhi"
    }
  ]
}
```

## New Event Webhook (Send)

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Full Reservation Query (Send)

## Full Reservation Query (Receive)
