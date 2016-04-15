# Object reference

## Product object

> Example product object

```shell
{
  "product_id": "0923568964",
  "quantity": 1,
  "variants": [
    {
      "dimension": "color",
      "value": "Red",
    }
  ],
  "seller_selection_criteria": {
    "prime": true,
    "handling_days_max": 6,
    "condition_in": ["New"],
  }
}
```

Attribute | Type | Description
--------- | ---- | -----------
product_id | String | The retailer's unique identifier for the product. Note that Zinc does not support digital purchases or Amazon prime pantry items.
quantity | Number | The number of products to purchase.
variants | Array | An array of variant objects containing information about the types of values of a specific product variant to select. A variant contains `dimension` field describing the type of the variant (e.g. "color" or "size") and a `value` field describing the specific value to select.
seller_selection_criteria | Object | A [seller selection criteria](#seller-selection-criteria-object) object containing information about which offers to choose when there are multiple offers available. If not provided, the default seller selection criteria will have `prime: true`, `handling_days_max: 6`, and `condition_in: ["New"]`.

## Seller selection criteria object

> Example seller selection criteria object

```shell
{
  "prime": true,
  "handling_days_max": 6,
  "condition_in": ["New"],
}
```

Seller selection criteria allow you to filter multiple offers for a product from a retailer. They give you fine grained control when a retailer has multiple offers for a single product. This happens frequently when third party or affiliated merchants are selling on a platform, such as o Amazon.

The seller selection criteria serve as a series of optional filters to narrow down the potential set of offers to something reasonable. After all the filters have been applied, Zinc will select the cheapest offer that is still available. For example, if `handling_days_max: 6` is applied, then the Zinc API will order the cheapest offer where the shipping will arrive in 6 days or less.

Attribute | Type | Description
--------- | ---- | -----------
addon | Boolean | (Amazon only) Specifies whether the selected offer should be an addon item
buy_box | Boolean | (Amazon only) Specifies whether the selected offer should be Amazon's default buy box offer
condition_in | Array | An array of item conditions that the Zinc API must order from
condition_not_in | Array | An array of item conditions that the Zinc API must not order from
handling_days_max | Number | The maximum number of allowable days for shipping and handling
international | Boolean | Specifies whether the item should come from an international supplier
max_item_price | Number | The maximum allowable price for an item
merchant_id_in | Array | An array of merchant ids that the Zinc API must order from
merchant_id_not_in | Array | An array of merchant ids that the Zinc API must not order from
min_seller_num_ratings | Number | (Amazon only) The minimum number of ratings required for an Amazon seller's offer to be selected
min_seller_percent_positive_feedback | Number | (Amazon only) The minimum percentage of positive feedback required for an Amazon seller's offer to be selected
prime | Boolean | (Amazon only) Specifies whether the selected offer should be an Amazon Prime offer

## Address object

> Example address object

```shell
{
  "first_name": "Tim",
  "last_name": "Beaver",
  "address_line1": "77 Massachusetts Avenue",
  "address_line2": "",
  "zip_code": "02139",
  "city": "Cambridge",
  "state": "MA",
  "country": "US",
  "phone_number": "5551230101"
}
```

Attribute | Type | Description
--------- | ---- | -----------
first_name | String | The first name of the addressee
last_name | String | The last name of the addressee
address_line1 | String | The house number and street name
address_line2 | String | The suite, post office box, or apartment number (optional)
zip_code | String | The zip code of the address
city | String | The city of the address
state | String | The USPS abbreviation for the state of the address (e.g. AK)
country | String | The ISO abbreviation for the country of the address (e.g. US). A list of all available two-letter country codes can be found [here](http://www.theodora.com/country_digraphs.html).
phone_number | String | The phone number associated with the address

## Payment method object

> Example payment object

```shell
{
  "name_on_card": "Ben Bitdiddle",
  "number": "5555555555554444",
  "security_code": "123",
  "expiration_month": 1,
  "expiration_year": 2015,
  "use_gift": false
}
```

Attribute | Type | Description
--------- | ---- | -----------
name_on_card | String | The full name on the credit/debit card
number | String | The credit/debit card number
security_code | String | The card verification value on the back of the credit/debit card
expiration_month | Number | The month of the expiration of the card (e.g. January is 1, February is 2)
expiration_year | Number | The year of the expiration of the card (e.g. 2016)
use_gift | Boolean | Whether or not to use the gift balance on the retailer account. If true, then the gift balance will first be used up completely before the card will be charged. Only works for retailers which support gift balance (`amazon` and `amazon_uk`).

## Webhooks object

> Example webhooks object

```shell
{
  "order_placed": "http://mywebsite.com/zinc/order_placed",
  "order_failed": "http://mywebsite.com/zinc/order_failed",
  "tracking_obtained": "http://mywebsite.com/zinc/tracking_obtained"
}
```

Attribute | Type | Description
--------- | ---- | -----------
order_placed | String | The webhook URL to send data to when an order is placed
order_failed | String | The webhook URL to send data to when an order fails
tracking_obtained | String | The webhook URL to send data to when tracking for an order is retrieved

## Retailer credentials object

> Example retailer credentials object

```shell
{
  "email": "timbeaver@gmail.com",
  "password": "myRetailerPassword"
}
```

Attribute | Type | Description
--------- | ---- | -----------
email | String | The email for the retailer account
password | String | The password for the retailer account

## Price components object

> Example price components object

```shell
{
  "shipping" : 0,
  "subtotal" : 1999,
  "tax" : 0,
  "total" : 1999
}
```

Attribute | Type | Description
--------- | ---- | -----------
shipping | Number | The price for shipping
subtotal | Number | The total price of the order before tax and other price adjustments
tax | Number | The tax collected on the order
total | Number | The total price paid for the order
gift_certificate | Number | (Optional) The amount of value used on a gift certificate placed on the account

## Merchant order ids object

> Example merchant order ids object

```shell
{
  "merchant_order_id" : "112-1234567-7272727",
  "merchant" : "amazon",
  "account" : "timbeaver@gmail.com",
  "placed_at" : ISODate("2014-07-02T23:51:08.366Z")
}
```

Attribute | Type | Description
--------- | ---- | -----------
merchant_order_id | String | The identifier provided by the retailer for the order that was placed
merchant | String | The retailer on which the order was placed
account | String | The account on which the order was placed
placed_at | Date | The date and time at which the order was placed

## Product offer object

> Example product offer object

```shell
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
  "seller_percent_positive": 100
}
```

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
