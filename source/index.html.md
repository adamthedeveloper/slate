---
title: Storefront API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='mailto:tech@brilliantmade.com'>Sign Up for a Developer Key</a>

includes:
  - errors
  - request_response_codes

search: true
---

# Introduction

Welcome to the Brilliant Storefront API! You can use our API to access Storefront API endpoints as explained in this document.
To gain access, please reach out to your company's Storefront Admin, or [email us](mailto:tech@brilliantmade.com).

# Authentication

> To access every API entry point, you will need to supply an Authorization header.
It can be generated like this:

```ruby
# Ruby Example
# Generate your string by combinging the api key with your
# secret key. Notice the colon between them. 
str = "#{my_assigned_api_key}:#{my_assigned_secret_key}"

# Returns the Base64-encoded version of str. 
# This method complies with RFC 4648. No line feeds are added. 
my_enc_str = Base64.strict_encode64(str)
```

```shell
# With shell, you can just pass the correct header with each request
curl https://api.brilliantmade.com/V2/every/entrypoint
  -H "Authorization: Basic value_of_my_enc_str"
```

> 

Brilliant uses API keys to allow access to the API. Store Administrators can create a new Brilliant API key in their [dashboard](https://www.brilliantmade.com/dashboard).

Brilliant Store API expects a Basic Authorization Header containing a base64 encoded API Key and API Secret Key combined with a colon between them. Example:

<code>API Key: f20e78a1d15cd2e976dddad7301d5c6a1137b2c49c67c382355a3775665047e1</code>

<code>API Secret Key: 8e02bf3ad43f9f0079850ea91510c4b6182e19480d963d3ddd73e2565ea5b279</code>

Concatenate them delimited with a colon like so:
<code>f20e78a1d15cd2e976dddad7301d5c6a1137b2c49c67c382355a3775665047e1:8e02bf3ad43f9f0079850ea91510c4b6182e19480d963d3ddd73e2565ea5b279</code>

Now, base64 encode this final value in [RFC 4648](https://tools.ietf.org/html/rfc4648) format. You should get the following without new lines and carriage returns:

<code>ZjIwZTc4YTFkMTVjZDJlOTc2ZGRkYWQ3MzAxZDVjNmExMTM3YjJjNDljNjdjMzgyMzU1YTM3NzU2NjUwNDdlMTo4ZTAyYmYzYWQ0M2Y5ZjAwNzk4NTBlYTkxNTEwYzRiNjE4MmUxOTQ4MGQ5NjNkM2RkZDczZTI1NjVlYTViMjc5</code>

`Authorization: Basic ZjIwZTc4YTFkMTVjZDJlOTc2ZGRkYWQ3MzAxZDVjNmExMTM3YjJjNDljNjdjMzgyMzU1YTM3NzU2NjUwNDdlMTo4ZTAyYmYzYWQ0M2Y5ZjAwNzk4NTBlYTkxNTEwYzRiNjE4MmUxOTQ4MGQ5NjNkM2RkZDczZTI1NjVlYTViMjc5`

<aside class="notice">
Make sure you are careful with your API Keys. You absolutely must safeguard your API Secret Key. Keep it private.
</aside>

# Store

## Get your store information

```shell
curl "https://api.brilliantmade.com/V2/store"
  -H "Authorization: Basic <auth string>"
```

> The above command returns JSON structured like this:

```json
{
  "name":"Brilliant Store",
  "inactive":false,
  "products":[
    {
      "id":24452,
      "name":"Top Tier Gift Set",
      "description":"Includes a MIIR wide-mouth water bottle, 2 La Newyorkina brownies, and a Fabrizio white soft cover notebook.",
      "inactive":false,
      "inventory_required":true,
      "variants":[
        {
          "id":72774,
          "product_id":24452,
          "inventory_count":-1,
          "size":null,
          "color":null,
          "flavor":null,
          "images": {
            "thumb": "https://assets.example.com/uploads/variant_photo/photo/152292/thumb_bri-deluxe-pack.jpg",
            "medium": "https://assets.example.com/uploads/variant_photo/photo/152292/medium_bri-deluxe-pack.jpg",
            "large": "https://assets.example.com/uploads/variant_photo/photo/152292/large_bri-deluxe-pack.jpg",
            "xlarge": "https://assets.example.com/uploads/variant_photo/photo/152292/xlarge_bri-deluxe-pack.jpg"
          }
        }
      ]
    },
    {
      "id":24454,
      "name":"Bottle + Notebook Gift Set",
      "description":"Includes a MIIR wide-mouth water bottle and a Fabrizio white soft cover notebook",
      "inactive":false,
      "inventory_required":true,
      "variants":[
        {
          "id":72776,
          "product_id":24454,
          "inventory_count":22,
          "size":null,
          "color":null,
          "flavor":null,
          "images": {
            "thumb": "https://assets.example.com/uploads/variant_photo/photo/152292/thumb_bri-deluxe-pack.jpg",
            "medium": "https://assets.example.com/uploads/variant_photo/photo/152292/medium_bri-deluxe-pack.jpg",
            "large": "https://assets.example.com/uploads/variant_photo/photo/152292/large_bri-deluxe-pack.jpg",
            "xlarge": "https://assets.example.com/uploads/variant_photo/photo/152292/xlarge_bri-deluxe-pack.jpg"
          }
        }
      ]
    },
    {
      "id":24453,
      "name":"Notebook + Two Brownies",
      "description":"Includes 2 La Newyorkina brownies, and a Fabrizio white soft cover notebook.",
      "inactive":false,
      "inventory_required":true,
      "variants":[
        {
          "id":72775,
          "product_id":24453,
          "inventory_count":-1,
          "size":null,
          "color":null,
          "flavor":null,
          "images": {
            "thumb": "https://assets.example.com/uploads/variant_photo/photo/152292/thumb_image.jpg",
            "medium": "https://assets.example.com/uploads/variant_photo/photo/152292/medium_image.jpg",
            "large": "https://assets.example.com/uploads/variant_photo/photo/152292/large_image.jpg",
            "xlarge": "https://assets.example.com/uploads/variant_photo/photo/152292/xlarge_image.jpg"
          }
        }
      ]
    },
    {
      "id":24455,
      "name":"Desk Essentials",
      "description":"A fun and colorful Maine Pouch, packed with some of our favorite goodies in a custom box. Contents include a slide-out gum pack, half-sticky note cube, two gel pens, a vanilla lip balm ball, and a set of pinback buttons that say \"Brilliant\", \"I (HEART) Marketing\" and \"Branding Geek\".",
      "inactive":false,
      "inventory_required":true,
      "variants":[
        {
          "id":72777,
          "product_id":24455,
          "inventory_count":70,
          "size":null,
          "color":null,
          "flavor":null,
          "images": {
            "thumb": "https://assets.example.com/uploads/variant_photo/photo/152292/thumb_image.jpg",
            "medium": "https://assets.example.com/uploads/variant_photo/photo/152292/medium_image.jpg",
            "large": "https://assets.example.com/uploads/variant_photo/photo/152292/large_image.jpg",
            "xlarge": "https://assets.example.com/uploads/variant_photo/photo/152292/xlarge_image.jpg"
          }
        }
      ]
    },
    {
      "id":24456,
      "name":"16 oz. Wide Mouth Bottle",
      "description":"16 oz. double wall vacuum insulated bottle stays cold for 24 hours, and hot for 12. Fits most standard cup holders. BPA free.",
      "inactive":false,
      "inventory_required":true,
      "variants":[
        {
          "id":72778,
          "product_id":24456,
          "inventory_count":20,
          "size":null,
          "color":null,
          "flavor":null,
          "images": {
            "thumb": "https://assets.example.com/uploads/variant_photo/photo/152292/thumb_image.jpg",
            "medium": "https://assets.example.com/uploads/variant_photo/photo/152292/medium_image.jpg",
            "large": "https://assets.example.com/uploads/variant_photo/photo/152292/large_image.jpg",
            "xlarge": "https://assets.example.com/uploads/variant_photo/photo/152292/xlarge_imge.jpg"
          }
        }
      ]
    }
  ]
}
```

This endpoint retrieves your store information, including the products and variants assigned
to your store. The variant ID's are what you will submit within your orders. 

Products contain general information, such as the product's name and description, whether or not
the product is active and if inventory is required to accept an order or not.

The variants have unique properties, such as size and color. They also display inventory data, eg. number of variants in stock.
Before submitting an order, ensure that the stock on hand is greater than or equal to the quantity you are ordering
or the order will not be created. We advise checking inventory immediately before submitting
your order to avoid unexpected errors.

### HTTP Request

`GET https://api.brilliantmade.com/V2/store`

### Query Parameters

None

<aside class="success">
Remember — we're here to help! Email tech@brilliantmade.com if you need support.
</aside>

## Fetch Store Orders

```shell
curl "https://api.brilliantmade.com/V2/store/orders?page=1&per=5"
  -X GET
  -H "Authorization: my_auth_keys"
```

> Example return value

```json
{
  "orders": [
    {
      "id": 14002,
      "created_at": "2018-08-21T03:24:34.000Z",
      "updated_at": "2018-08-21T03:24:34.000Z",
      "status": "created",
      "ship_status": null,
      "order_item_count": 1
    },
    {
      "id": 14001,
      "created_at": "2018-08-21T02:17:17.000Z",
      "updated_at": "2018-08-21T02:17:17.000Z",
      "status": "created",
      "ship_status": null,
      "order_item_count": 1
    },
    {
      "id": 13986,
      "created_at": "2018-08-17T17:42:23.000Z",
      "updated_at": "2018-08-17T17:42:23.000Z",
      "status": "created",
      "ship_status": null,
      "order_item_count": 1
    },
    {
      "id": 13985,
      "created_at": "2018-08-17T16:45:30.000Z",
      "updated_at": "2018-08-17T16:45:30.000Z",
      "status": "created",
      "ship_status": null,
      "order_item_count": 1
    },
    {
      "id": 13982,
      "created_at": "2018-08-17T07:57:24.000Z",
      "updated_at": "2018-08-17T07:57:24.000Z",
      "status": "created",
      "ship_status": null,
      "order_item_count": 1
    }
  ],
  "pagination": {
    "page": 1,
    "per_page": 5,
    "total_pages": 2,
    "total_orders": 7
  }
}
```

Paginate through all of your store orders. They are ordered by their creation date descending.

To paginate, include query parameters like so:

<code>?page=2&per=20</code>

Max number per page is 20. [Contact us](mailto:tech@brilliantmade.com) if you need something special.

### HTTP Request

`GET https://api.brilliantmade.com/V2/store/orders?page=<int>&per=<int>`

### Query Parameters

Parameter | Description
--------- | -----------
page      | Page number. Default is 1
per       | Number of orders per page. Default and maximum is 20.

## Fetch an Order

```shell
curl "https://api.brilliantmade.com/V2/store/order/123"
  -X GET
  -H "Authorization: my_auth_keys"
```

> The return value should be structured like this:

```json
{
  "id": 123,
  "created_at": "2018-08-21T03:24:34.000Z",
  "updated_at": "2018-08-21T03:24:34.000Z",
  "status": "created",
  "ship_status": null,
  "shipping_address": {
    "name": "Jill Gilgooley",
    "company": "Test Co.",
    "address_1": "123 Test Pl. W.",
    "address_2": null,
    "city": "Bothell",
    "state": "WA",
    "postal_code": "98021",
    "country": "US",
    "phone": "(555)555-5555"
  },
  "order_items": [
    {
      "variant_id": 79029,
      "quantity": 1,
      "notes": "Test Note"
    }
  ],
  "webhook_url": "https://example.com/order_listener",
  "custom_data": {
    "my": "data"
  }  
}
```

Using an order ID, fetch the current order data.

### HTTP Request

`GET https://api.brilliantmade.com/V2/store/order/{ID}`

### Query Parameters

ID of the order.


## Create an Order

Orders are placed using variant ids, quantities, and a shipping address. You can also pass
an optional webhook url that will be called whenever a status change happens on the order. The
webhook entry point must accept a POST request with a JSON body. 

You can also pass an optional object in your payload called "custom_data". Place anything
you want into the custom data object. Brilliant does not modify it and we will send it
to your webhook entry point as part of the post body for your convenience.

```shell
curl "https://api.brilliantmade.com/V2/store/order"
  -X POST
  -H "Authorization: my_auth_keys"
  -d '{"order_items":[], "shipping_address":{}, "custom_data":{}, "webhook_url":""}'
```

> The post body should be structured like so:

```json
{
  "order_items": [
    {
      "variant_id": 1234,
      "quantity": 2,
      "note": "Some text"
    },
    {
      "variant_id": 5678,
      "quantity": 1,
      "note": "Some more text"
    }
  ],
  "shipping_address": {
    "name": "John Smith",
    "company": "Test Co.",
    "address_1": "123 Test St.",
    "address_2": null,
    "city": "Bothell",
    "state": "WA",
    "postal_code": "98021",
    "country": "US",
    "phone": "(555)555-5555"
  },
  "custom_data": {
    "something": "anything",
    "this": "that"
  },
  "webhook_url": "https://api.example.com/brilliant/listener?hi=bye"
}
```

> The above command returns JSON structured like this:

```json
{
  "code": 1200,
  "message": "Success",
  "payload": {
    "order_items": [
      {
        "variant_id": 1234,
        "quantity": 2,
        "notes": "Some text"
      },
      {
        "variant_id": 1234,
        "quantity": 2,
        "notes": "Some more text"
      }
    ],
    "shipping_address": {
      "name": "John Smith",
      "company": "Test Co.",
      "address_1": "123 Test St.",
      "address_2": null,
      "city": "Bothell",
      "state": "WA",
      "postal_code": "98021",
      "country": "US",
      "phone": "(555)555-5555"
    },
    "webhook_url": "https://api.example.com/brilliant/listener?hi=bye",
    "custom_data": {
      "something": "anything",
      "this": "that"
    }
  }
}
```

> If the order is unsuccessful, the response will include some error information:

```json
{
    "code": 2501,
    "invalid_records": [
        {
            "name": "Jan Wayward",
            "company": "Test Co.",
            "address_1": "22411 Test Pl. W.",
            "address_2": null,
            "city": "Bothell",
            "state": "Washington",
            "postal_code": "98021",
            "country": "US",
            "phone": "(555)955-5555"
        }
    ],
    "message": "Address state State must be a valid 2 character state abbreviation",
    "body": {
        "order_items": [
            {
                "variant_id": 72799,
                "quantity": 1,
                "notes": "Test 2 Note"
            },
            {
                "variant_id": 72800,
                "quantity": 5,
                "notes": "Test 3 Note"
            }
        ],
        "shipping_address": {
            "name": "Jan Wayward",
            "company": "Test Co.",
            "address_1": "22411 Test Pl. W.",
            "address_2": null,
            "city": "Bothell",
            "state": "Washington",
            "postal_code": "98021",
            "country": "US",
            "phone": "(555)955-5555"
        },
        "webhook_url": "https://example.com/order_listener",
        "custom_data": {
            "my": "context"
        }
    }
}
```

### HTTP Request

`POST https://api.brilliantmade.com/V2/store/order`

### URL Parameters

None

### POST Body Info

Addresses have some required fields:

Parameter | Description
--------- | -----------
name      | Name of recipient
address_1 | Required. 
address_2 | Optional.
city      | Required.
state     | Required. 2 characters.
postal_code | Required.
country   | Required. 2 characters.
phone     | Optional. Phone number of recipient

<aside class="notice">
Caution on Addresses: US states need to be 2 characters. So do countries. 
</aside>

Order items also have required fields:

Parameter | Description
--------- | -----------
variant_id | Required. The ID of the variant you wish to order.
quantity | Required. The number of variants you wish to order.
note | Optional.

<aside class="notice">
Caution on order items: Don't submit duplicates. The variant ids need to be unique
across all of the order items. Adjust quantities instead. 
</aside>
 
### Additional, Optional Post Data

Parameter | Description
--------- | -----------
webhook_url | Required if custom_data is set. This is a callback url that you expect us to call when your order status changes.
custom_data | Optional. This is a JSON object holding data that you would like us to send back to you with every webhook call. Brilliant doesn't modify this data.
 
 


