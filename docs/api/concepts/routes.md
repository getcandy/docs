# Routes

::: warning ISSUE For Alec
API Ref doesn't appear to have query params set for the route search, https://api-reference.getcandy.io/#operation/get-routes-search
:::


Not to be confused with the routing in your Laravel app, GetCandy routes are database entries that allow you to specify "routes" to different resources, such as products and categories.

Rather than the API forcing you to load products or categories by ID, routes allow us to store SEO-friendly URL slugs that relate to a GetCandy resource.

e.g. 

```json
{
  "id": "4md86slw",
  "element_type": "GetCandy\Api\Core\Products\Models\Product",
  "element_id": 8,
  "default": true,
  "redirect": false,
  "slug": "organic-linen-mask-grey-skies",
  "path": "???????",
  "locale": "en",
  "description": "??????",
  "drafted_at": null,
  "draft_parent_id": null
}
```

You can see how we can then use our slug to create nice website URLs, e.g. `https://mystore.com/products/M10-stainless-steel-nuts`.

Routes have both a `path` and `slug` field available, each route must be unique across both of these fields. For example if you have a route with a path "tools" and slug "drill", you can create an additional route with the slug "drill" providing the path is different to "tools". This can be useful if migrating from a previous site with different URL formats.

To load a route entry, you would perform a request similar to the following...

```js
const res = await axios.get(
  'https://api.mystore.com/api/v1/routes/search', 
  { 
    params: { 
      path: null,
      slug: 'organic-linen-mask-grey-skies',
      include: 'element'
    } 
  });
```

And the response would give you...


::: warning ISSUE For Alec
The response doesn't appear to be the same as the API reference. E.g. `element_type` vs `type`.
:::

```json
{
  "data":{
    "id":"p6z2ev6r",
    "default":true,
    "redirect":false,
    "locale":"en",
    "path":null,
    "slug":"organic-linen-mask-grey-skies",
    "description":null,
    "type":"product",
    "element":{
      "data":{
        "id":"qg6zr4n9",
        "drafted_at":null,
        "option_data":[
          
        ],
        "variants_count":null,
        "created_at":"2020-11-19T10:36:12.000000Z",
        "updated_at":"2020-11-19T10:36:12.000000Z",
        "name":"Organic linen mask - grey skies",
        "description":"<p><br \/>Hand-made face mask made from 4 layers of grey organic linen. Soft organic cotton earloops allow the mask to be easily put on and removed. Simply knot them for a perfect, smooth fit.&nbsp;Light, breathable, washable at 90 degrees and reusable. Please note that this is not a medical grade mask. However, linen is one of the oldest known fabrics used by mankind and is resilient and functional. More importantly, linen has naturally antibacterial properties. &nbsp;There is no size difference between men\/women apart from slight variation in colour. Available in a <strong><span style=\"text-decoration: underline;\"><a href=\"https:\/\/www.plumo.com\/categories\/Reusable-Masks\/\" target=\"_blank\">variety of colours.<\/a><\/span><\/strong><\/p>\r\n<p><strong>For every mask sold, Pl&uuml;mo is&nbsp;supporting NHS staff and volunteers caring for Covid-19 patients&nbsp;by donating to NHS charities. For more information please visit :&nbsp;<span style=\"text-decoration: underline;\"><a href=\"https:\/\/www.crowdfunder.co.uk\/nhs-charities-together\" target=\"_blank\">https:\/\/www.crowdfunder.co.uk\/nhs-charities-together<\/a><\/span><\/strong><\/p>\r\n<p><span style=\"background-color: #ffffff;\"><strong>&nbsp;<\/strong><\/span><br \/><strong>DETAILS <\/strong><br \/><br \/> - 4 layers of natural 100% linen fabric <br \/>- High quality protective mask <br \/>- Reusable <br \/>- Can be washed at high temperatures (80-100 &deg;C) <br \/>- Do not tumble dry<br \/>- Slightly stretch ear loops<br \/>- Adjust shape for a snug fit by simply knotting the earloops<br \/>- Easy to use and comfortable<br \/>- No slit for filter, wash instead on high temperature (no paper waste)<br \/>- Non medical grade<\/p>\r\n<p>Sterile package - for your safety, these items are non-returnable<\/p>\r\n<p><strong>SIZE AND FIT<\/strong>&nbsp;<\/p>\r\n<p><strong> Width<\/strong> 12.8cm&nbsp; - measuring one side only, nose to side<br \/><strong> Height<\/strong> 14.5cm <br \/><strong>Width including ear loops<\/strong> 19cm<\/p>"
      }
    }
  }
}

```


::: tip API Reference
[View the API Reference section for Routes](https://api-reference.getcandy.io/#tag/Routes)
:::
