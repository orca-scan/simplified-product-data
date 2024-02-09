# Simplified Product Data (SPD)

**Simplified Product Data** is an open source data structure designed to provide developers with easy access to detailed product information _(including parsed barcode data)_ with minimal effort. It was created to remove the need for developers to build complex parsers or barcode decoders into their applications, by ensuring key product information is accessible upon request.

The data structure is broken down into 3 top level objects:
* [product](#product)
* [org](#org)
* [links](#links)

For a better understanding of how this works, see the [Complete Data Structure](#complete-data-structure).

## `product`

Object containing detailed product information:

Property       | Type     | Description
:--------------|----------|:----------------------------------------------------------------------------
`url`          | `string` | URL of the product page
`language`     | `string` | Language code for the product information
`title`        | `string` | Title of the product
`description`  | `string` | A brief description of the product
`images`       | `array`  | Array of objects containing product images. See [example.json](example.json#L7)
`barcode`      | `object` | Object containing decoded barcode data. See [example.json](example.json#L13)
`price`        | `string` | Price of the product
`currency`     | `string` | Currency code for the price
`availability` | `string` | Availability status of the product

### `product.images`

Array of product images:

Property | Type     | Description
:--------|----------|:------------------------
`url`    | `string` | URL of the product image
`type`   | `string` | Image mime type

### `product.barcode`

Object containing detailed barcode information:

Property          | Type      | Description
:-----------------|-----------|:-------------------------------------------------------------------
`isValid`         | `boolean` | True if valid, otherwise false
`gtin`            | `string`  | The GS1 Global Trade Item Number (GTIN)
`gtin8`           | `string`  | 8 digit version of the GTIN
`gtin12`          | `string`  | 12 digit version of the GTIN
`gtin13`          | `string`  | 13 digit version of the GTIN
`gtin14`          | `string`  | 14 digit version of the GTIN
`machineReadable` | `string`  | Machine readable version of the barocde _(inc hidden characters)_
`humanReadable`   | `string`  | Barcode in Human Readable Interpretation (HRI) format
`digitalLink`     | `string`  | GS1 Digital Link version of the barcode
`imageUrl`        | `string`  | Url to the barcode image
`values`          | `array`   | Array of extracted barcode values _(expiry dates, lot numbers etc)_

## `org`

Object containing high level organisation information:

Property     | Type     | Description
:------------|:---------|:------------------------------------------------------------------------------
`url`        | `string` | URL of the organization's homepage
`name`       | `string` | Name of the organization
`faviconUrl` | `string` | URL of the organization's favicon
`logoUrl`    | `string` | URL of the organization's logo
`logoColors` | `object` | Object containing logo color information. See [example.json](example.json#L43)

## `links`

Any array of objects containing related links:

Property | Type     | Description
:--------|:---------|:-------------------------------------------
`href`   | `string` | URL associated with the link
`rel`    | `string` | The relationship of the link to the product
`method` | `string` | HTTP method used to access the link
`title`  | `string` | A descriptive title for the link

<!-- ## Goals

* Must be a valid JSON object
* Must be concise
* Must be human readable
* Must include decoded barcode data -->

## Complete Data Structure

```json
{
  "product": {
    "url": "https://www.juxfood.com/products/beetroot-80g",
    "language": "en",
    "title": "Beetroot 80g Pot",
    "description": "9 small fresh beetroots in every pot! Unlock cardiovascular benefits with beets",
    "images": [
      {
        "url": "http://www.juxfood.com/cdn/shop/files/11_a223a8ca-d342-44ff-baf4-fbd48246e188.png?v=1706723201",
        "type": "image/png"
      }
    ],
    "barcode": {
      "isValid": true,
      "gtin": "05065016432004",
      "gtin8": "",
      "gtin12": "",
      "gtin13": "5065016432004",
      "gtin14": "05065016432004",
      "machineReadable": "\u001d0105065016432004",
      "humanReadable": "(01)05065016432004",
      "digitalLink": "https://orca.link/01/05065016432004",
      "imageUrl": "https://orca.link/01/05065016432004.svg",
      "values": [
        {
          "ai": "01",
          "name": "GTIN",
          "description": "Global Trade Item Number",
          "raw": "05065016432004",
          "value": "05065016432004"
        }
      ]
    },
    "price": "",
    "currency": "",
    "availability": ""
  },
  "org": {
    "url": "https://www.juxfood.com/",
    "name": "JUXfood",
    "faviconUrl": "https://www.juxfood.com/cdn/shop/files/JUX_LOGO_BLACK_square.png?crop=center&height=32&v=1693931039&width=32",
    "logoUrl": "https://www.juxfood.com/cdn/shop/files/jux-logo.png?v=1686223843&width=500",
    "logoColors": {
      "lightest": "#313131",
      "darkest": "#040404",
      "dominant": "#040404",
      "background": "#00000000",
      "palette": [
        "#313131",
        "#040404",
        "#1c1c1c",
        "#141414",
        "#0c0c0c",
        "#041008"
      ]
    }
  },
  "links": [
    {
      "href": "https://www.juxfood.com/products/beetroot-80g",
      "rel": "gs1:pip",
      "method": "GET",
      "title": "Info"
    },
    {
      "href": "https://www.juxfood.com/collections/all",
      "rel": "gs1:promotion",
      "method": "GET",
      "title": "Promotion"
    },
    {
      "href": "https://www.juxfood.com/blogs/recipes",
      "rel": "gs1:recipeInfo",
      "method": "GET",
      "title": "Recipe"
    },
    {
      "href": "https://www.facebook.com/JUXfood",
      "title": "Facebook",
      "rel": "facebook",
      "method": "GET"
    },
    {
      "href": "https://www.instagram.com/juxfood/",
      "title": "Instagram",
      "rel": "instagram",
      "method": "GET"
    },
    {
      "href": "https://www.linkedin.com/company/juxfood/",
      "title": "Linked In",
      "rel": "linkedin",
      "method": "GET"
    },
    {
      "href": "https://www.tiktok.com/@juxfood",
      "title": "TikTok",
      "rel": "tiktok",
      "method": "GET"
    },
    {
      "href": "https://id.gs1.org/01/05065016432004",
      "rel": "resolver",
      "method": "GET"
    },
    {
      "href": "https://orca.link/01/05065016432004.json",
      "rel": "self",
      "method": "GET"
    },
    {
      "href": "https://orca.link/schema.json",
      "rel": "describedby",
      "method": "GET"
    }
  ]
}
```

## How to Contribute

There are a couple of ways to get involved:

* **Suggestions:** share your feedback/suggestions via GitHub Issues
* **Contribute:** submit a pull requests with improvements

## License

Licensed under the [MIT License](LICENSE) &copy; [Orca Scan](https://orcascan.com)