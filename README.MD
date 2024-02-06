# Simplified Product Data (SPD)

Simplified Product Data is a developer friendly product data structure designed to make it as simple as possible for developers to ingest detailed product data, including decoded barcode information with the minimal effort.

## Goals

* Must be a valid JSON object
* Must be concise
* Must be human readable
* Must include parsed barcode information

## Example

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

## License

Licensed under [MIT License](LICENSE) &copy; [Orca Scan](https://orcascan.com)