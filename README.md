# geocoder-arcgis-geojson

Isomorphic geocoding for reuse across our JavaScript libraries. This library is built to match the API of [geocoder-arcgis](https://www.npmjs.com/package/geocoder-arcgis) in order to facilitate a quick conversion of our applications to use ESRI's geocoder.  Read the ESRI docs [here](https://developers.arcgis.com/labs/rest/get-an-access-token/). Coordinates must be anything that can be parsed by [lonlng](https://github.com/conveyal/lonlng).

-   [Examples](#examples)
-   [API Documentation](#api)

## Examples

All API methods (except autocomplete) accept the options `clientId`, `clientSecret` and `forStorage`.  When using `forStorage`, the `clientId` and `clientSecret` options are required.

### `Autocomplete`

```js
import {autocomplete} from 'isomorphic-mapzen-search'

autocomplete({
  boundary: {
    rect: {
      minLon: minLon,
      minLat: minLat,
      maxLon: maxLon,
      maxLat: maxLat
    }
  },
  focusPoint: {lat: 39.7691, lon: -86.1570},
  text: '1301 U Str'
}).then((result) => {
  console.log(result)
}).catch((err) => {
  console.error(err)
})
```

### `Reverse`

```js
import {reverse} from 'isomorphic-mapzen-search'

reverse({
  point: {
    lat: 39.7691,
    lng: -86.1570
  }
}).then((result) => {
  console.log(result)
}).catch((err) => {
  console.error(err)
})
```

### `search({apiKey, text, ...options})`

```js
import {search} from 'isomorphic-mapzen-search'

search({
  text: '1301 U Street NW, Washington, DC',
  focusPoint: {lat: 39.7691, lon: -86.1570},
  boundary: {
    rect: {
      minLon: minLon,
      minLat: minLat,
      maxLon: maxLon,
      maxLat: maxLat
    }
  }
}).then((geojson) => {
  console.log(geojson)
}).catch((err) => {
  console.error(err)
})
```

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

-   [autocomplete](#autocomplete)
-   [reverse](#reverse)
-   [search](#search)

### autocomplete

[index.js:64-98](https://github.com/conveyal/geocoder-arcgis-geojson/blob/e7e51f5a03d9ca00deaa9718e2c957022a4b792c/index.js#L64-L98 "Source code on GitHub")

Search for and address using
ESRI's [suggest](https://developers.arcgis.com/rest/geocode/api-reference/geocoding-suggest.htm)
service.  This service does not return geojson, instead it returns the list
of address suggestions and corresponding magicKeys

**Parameters**

-   `$0` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)**
    -   `$0.clientId` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?**
    -   `$0.clientSecret` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?**
    -   `$0.boundary` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?**
    -   `$0.focusPoint` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?**
    -   `$0.text` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** query text
    -   `$0.url` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** optional URL to override ESRI suggest endpoint

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)** A Promise that'll get resolved with the suggest result

### reverse

[index.js:113-157](https://github.com/conveyal/geocoder-arcgis-geojson/blob/e7e51f5a03d9ca00deaa9718e2c957022a4b792c/index.js#L113-L157 "Source code on GitHub")

Reverse geocode using
ESRI's [reverseGeocode](https://developers.arcgis.com/rest/geocode/api-reference/geocoding-reverse-geocode.htm)
service.

**Parameters**

-   `$0` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)**
    -   `$0.clientId` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?**
    -   `$0.clientSecret` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?**
    -   `$0.forStorage` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Specifies whether result is inteded to be stored (optional, default `false`)
    -   `$0.point` **{lat: [number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), lon: [number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)}** Point to reverse geocode
    -   `$0.url` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** optional URL to override ESRI reverseGeocode endpoint

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)** A Promise that'll get resolved with reverse geocode result

### search

[index.js:176-251](https://github.com/conveyal/geocoder-arcgis-geojson/blob/e7e51f5a03d9ca00deaa9718e2c957022a4b792c/index.js#L176-L251 "Source code on GitHub")

Search for an address using
ESRI's [findAddressCandidates](https://developers.arcgis.com/rest/geocode/api-reference/geocoding-find-address-candidates.htm)
service.

**Parameters**

-   `$0` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)**
    -   `$0.clientId` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?**
    -   `$0.clientSecret` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?**
    -   `$0.boundary` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?**
    -   `$0.focusPoint` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?**
    -   `$0.forStorage` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Specifies whether result is inteded to be stored (optional, default `false`)
    -   `$0.magicKey` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** magicKey to use in searching as obtained from `suggest` results
    -   `$0.size` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)**  (optional, default `10`)
    -   `$0.text` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The address text to query for
    -   `$0.url` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** optional URL to override ESRI reverseGeocode endpoint

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)** A Promise that'll get resolved with search result
