# Products

## Get product details

> Example product details request

```shell
curl https://api.zinc.io/v1/products/0923568964?retailer=amazon \
  -u client_token:
```

> Example product details response

```shell
{
  "cleaned_product_description": "",
  "product_description": "",
  "retailer": "amazon",
  "epid": {
    "type": "ISBN",
    "value": "0923568964"
  },
  "epids":[
    {
      "type": "EAN",
      "value": "9780923568962"
    },
    {
      "type": "ISBN",
      "value": "0923568964"
    }
  ],
  "product_details": [
    "Series: The Easy Way!",
    "Paperback: 60 pages",
    "Publisher: XanEdu Publishing Inc; 2nd Edition edition (September 28, 2009)",
    "Language: English",
    "ISBN-10: 0923568964",
    "ISBN-13: 978-0923568962",
    "Product Dimensions: 8.3 x 5.3 x 0.2 inches",
    "Shipping Weight: 3.5 ounces"
  ],
  "title": "APA: The Easy Way! [Updated for APA 6th Edition]",
  "variant_specifics": null,
  "product_id": "0923568964"
}
```

### Product detail attributes

Attribute | Type | Description
--------- | ---- | -----------
cleaned_product_description | String | The description of the product
product_description | String | Description of the product
retailer | String | The retailer for the product
epid | Object |
epids | Array |
product_details | Array | TODO
title | String | Title of the product
variant_specifics | Array | TODO
product_id | String | The retailer's unique identifier for the product

## Get product offers

> Example product offers request

```shell
curl https://api.zinc.io/v1/products/0923568964/offers/retailer=amazon \
  -u client_token:
```

> Example product offers response

```shell
{
  "retailer": "amazon",
  "offers":[
    {
      "addon": false,
      "condition": "New",
      "handling_days_max": 0,
      "handling_days_min": 0,
      "international": false,
      "merchant_id": "ATVPDKIKX0DER",
      "offerlisting_id": "lUai8vEbhC%2F2vYZDwaePlc4baWiHzAy9XJncUR%2FpQ9l4VOrs%2FfpYt4ZtreQaB%2BPL1xJwz5OpIc%2BJjyymHg3iv4YkZvWy5z7flil7n7lUDWNPY76YUhMNdw%3D%3D",
      "price": 9.79,
      "ship_price": 0
      "prime": true,
      "prime_only": false,
      "seller_name": "Amazon.com",
      "seller_num_ratings": 1000000,
      "seller_percent_positive": 100,
    }
  ]
}
```

### Product offers attributes

Attribute | Type | Description
--------- | ---- | -----------
retailer | String | The retailer for the product offers
offers | Array | An array of [product offer objects](#product-offer-object) for a particular product on a retailer

## Product offer object

Attribute | Type | Description
--------- | ---- | -----------
addon | Boolean | Whether or not the product is an addon item that can only be purchased in a bundle
condition | String | The condition of the product. Possible values are `New`, `Refurbished`, `Used - Like New`, `Used - Very Good`, `Used - Good`, `Used - Acceptable`, `Unacceptable`.
handling_days_max | Number | The maximum number of days required for shipping and handling
handling_days_min | Number | The minimum number of days required for shipping and handling
international | Boolean | Whether or not the product ships from outside of the United States
merchant_id | String | The merchant's unique identifier for the product
offerlisting_id | String | (`amazon` and `amazon_uk` only). The unique identifier that identifies an item sold by any merchant on Amazon
price | Number | The price of the item, not including shipping
ship_price | Number | The price of the shipping for the item
prime | Boolean | (`amazon` and `amazon_uk` only). Whether or not the product ships using Amazon Prime
prime_only | Boolean | (`amazon` and `amazon_uk` only). Whether or not the product only ships using Amazon Prime
seller_name | String | The name of the seller of the current offer
seller_num_ratings | Number | The number of ratings that tha seller has accumulated
seller_percent_positive | Number | Number between 0 and 100 denoting the percentage of positive ratings the seller has received
