# Simplified Product Data (SPD)

**Simplified Product Data** is an open source data structure designed to provide developers with easy access to detailed product information _(including parsed barcode data)_ when a [GS1 Digital Link](https://orcascan.com/solutions/how-to-create-a-gs1-digital-link-qr-code-059f8b29) barcode is scanned.

For example this [GS1 Digital Link homepage](https://orca.link/01/05065016432004) returns [SPD](example.json) when requested using `Accept: application/json`:

```bash
curl -H "Accept: application/json" https://id.juxfood.com/01/05065016432004
```

## Data Structure

SPD contains 3 top level objects:
* [product](#product)
* [org](#org)
* [links](#links)

### `product`

Detailed product information:

Property       | Type            | Description
:--------------|-----------------|:------------------------------------------------------------
`url`          | `string`        | URL of the product page
`language`     | `string`        | Language code for the product information
`title`        | `string`        | Title of the product
`description`  | `string`        | A brief description of the product
`images`       | `array[object]` | Array of objects containing [product images](#productimages)
`barcode`      | `object`        | Object containing [decoded barcode data](#productbarcode)
`price`        | `string`        | Price of the product
`currency`     | `string`        | Currency code for the price
`availability` | `string`        | Availability status of the product

#### `product.images`

Array of product image objects _(see [example.json](example.json#L7))_:

Property | Type     | Description
:--------|----------|:------------------------
`url`    | `string` | URL of the product image
`type`   | `string` | Image mime type

#### `product.barcode`

Decoded barcode information _(see [example.json](example.json#L13))_:

Property          | Type            | Description
:-----------------|-----------------|:-------------------------------------------------------------------
`isValid`         | `boolean`       | True if valid, otherwise false
`gtin`            | `string`        | The GS1 Global Trade Item Number (GTIN)
`gtin8`           | `string`        | 8 digit version of the GTIN
`gtin12`          | `string`        | 12 digit version of the GTIN
`gtin13`          | `string`        | 13 digit version of the GTIN
`gtin14`          | `string`        | 14 digit version of the GTIN
`machineReadable` | `string`        | Machine readable version incuding hidden characters
`humanReadable`   | `string`        | Human Readable Interpretation (HRI) version
`digitalLink`     | `string`        | GS1 Digital Link version of the barcode
`imageUrl`        | `string`        | Url to access the barcode image
`values`          | `array[object]` | Array of decoded barcode values _(expiry dates, lot numbers etc)_

### `org`

High level organisation information:

Property     | Type     | Description
:------------|:---------|:------------------------------------------------------------------------------
`url`        | `string` | URL of the organization's homepage
`name`       | `string` | Name of the organization
`faviconUrl` | `string` | URL of the organization's favicon
`logoUrl`    | `string` | URL of the organization's logo
`logoColors` | `object` | Object containing [logo color information](#orglogocolors)

#### `org.logoColors`

Logo color information _(see [example.json](example.json#L43))_:

Property     | Type            | Description
:------------|:----------------|:----------------------------------------------------
`lightest`   | `string`        | lightest color found in the logo in hex format
`darkest`    | `string`        | darkest color found in the logo in hex format
`dominant`   | `string`        | Most dominant colour found in the logo in hex format
`background` | `string`        | Background color found  in the logo in hex format
`palette`    | `array[string]` | Array of colours found in the logo

### `links`

Array of related links _(see [example.json](example.json#L58))_:

Property | Type     | Description
:--------|:---------|:-------------------------------------------
`href`   | `string` | URL associated with the link
`rel`    | `string` | The relationship of the link to the product
`method` | `string` | HTTP method used to access the link
`title`  | `string` | A descriptive title for the link

### Complete Data Structure

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
      "digitalLink": "https://id.juxfood.com/01/05065016432004",
      "imageUrl": "https://id.juxfood.com/01/05065016432004.svg",
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
      "href": "https://id.juxfood.com/01/05065016432004.json",
      "rel": "self",
      "method": "GET"
    },
    {
      "href": "https://raw.githubusercontent.com/orca-scan/simplified-product-data/v1.0.0/schema.json",
      "rel": "describedby",
      "method": "GET"
    }
  ]
}
```

## Motivation

The new [GS1 Digital Link barcode](https://orcascan.com/solutions/how-to-create-a-gs1-digital-link-qr-code-059f8b29#how-does-gs1-digital-link-work) will replace all retail barcodes by 2027. It's designed to connect physical products to the internet by turning each [GS1 GTIN](https://orcascan.com/solutions/how-to-create-a-gs1-digital-link-qr-code-059f8b29#what-is-a-gs1-gtin) into a URL that humans and machines can follow for data.

The trouble is, the [GS1 Digital Link spec](https://ref.gs1.org/standards/digital-link/uri-syntax/) still requires developer to:
* Parse barcode values within their application code
* Follow links and execute multiple request for basic product information
* Navigate complex JSON objects to extract basic product data

The goal of [SPD](https://github.com/orca-scan/simplified-product-data) is to provide the above information to the developer in the first request.

## Background

**Simplified Product Data** was created by the [Orca Scan team](https://orcascan.com/about-us) as part of the [GS1 Digital Link](https://orcascan.com/solutions/how-to-create-a-gs1-digital-link-qr-code-059f8b29) solution. Orca Scan automatically generates a GS1 Digital Link homepage for every GS1 GTIN, the SPD format is returned when requesting a GS1 Digital Link URL with the HTTP header `Accept: application/json`.

## How to Contribute

There are a couple of ways to get involved:

* **Suggestions:** share your feedback/concerns/suggestions via GitHub Issues
* **Contribute:** submit a Pull Requests with improvements

## License

Licensed under the [MIT License](LICENSE) &copy; [Orca Scan](https://orcascan.com)