---
creation date: 2021-05-14 11:40
modification date: Friday 14th May 2021 11:40:30
tags: ["#google", "#maps", "#dev"]
author: Jimmy Briggs
---

## Table of contents
-   [Introduction](https://developers.google.com/maps/documentation/distance-matrix/overview#Introduction)
    -   [Before you begin](https://developers.google.com/maps/documentation/distance-matrix/overview#before-you-begin)
-   [Distance Matrix requests](https://developers.google.com/maps/documentation/distance-matrix/overview#DistanceMatrixRequests)
    -   [Request parameters](https://developers.google.com/maps/documentation/distance-matrix/overview#request-parameters)
    -   [Required parameters](https://developers.google.com/maps/documentation/distance-matrix/overview#required-parameters)
    -   [Optional parameters](https://developers.google.com/maps/documentation/distance-matrix/overview#optional-parameters)
    -   [Travel modes](https://developers.google.com/maps/documentation/distance-matrix/overview#travel_modes)
    -   [Traffic information](https://developers.google.com/maps/documentation/distance-matrix/overview#distance-matrix-advanced)
    -   [Restrictions](https://developers.google.com/maps/documentation/distance-matrix/overview#Restrictions)
    -   [Unit systems](https://developers.google.com/maps/documentation/distance-matrix/overview#unit_systems)
    -   [Location Modifiers](https://developers.google.com/maps/documentation/distance-matrix/overview#location-modifiers)
-   [Distance Matrix responses](https://developers.google.com/maps/documentation/distance-matrix/overview#distance-matrix-responses)
    -   [Distance Matrix response elements](https://developers.google.com/maps/documentation/distance-matrix/overview#directions-response-elements)
    -   [Status codes](https://developers.google.com/maps/documentation/distance-matrix/overview#status-codes)
    -   [Error messages](https://developers.google.com/maps/documentation/distance-matrix/overview#error-messages)
    -   [Rows](https://developers.google.com/maps/documentation/distance-matrix/overview#rows)
    -   [Elements](https://developers.google.com/maps/documentation/distance-matrix/overview#elements)
-   [The sensor parameter](https://developers.google.com/maps/documentation/distance-matrix/overview#sensor)

## Introduction

The Distance Matrix API is a service that provides travel distance and time for a matrix of origins and destinations. The API returns information based on the recommended route between start and end points, as calculated by the Google Maps API, and consists of rows containing `duration` and `distance` values for each pair.

**Note:** This service does **not** return **detailed route information**. Route information can be obtained by passing the desired single origin and destination to the **[Directions API](https://developers.google.com/maps/documentation/directions)**.

### Before you begin

This document is intended for developers who wish to compute travel distance and time between a number of points within maps provided by one of the Google Maps APIs. It provides an introduction to using the API and reference material on the available parameters.

Before you start developing with the Distance Matrix API, review the [authentication requirements](https://developers.google.com/maps/documentation/distance-matrix/get-api-key) (you need an API key) and the [API usage and billing](https://developers.google.com/maps/documentation/distance-matrix/usage-and-billing) information (you need to enable billing on your project).

## Distance Matrix requests

A Distance Matrix API request takes the following form:

https://maps.googleapis.com/maps/api/distancematrix/outputFormat?parameters 

where `outputFormat` may be either of the following values:

-   `json` (recommended), indicates output in JavaScript Object Notation (JSON); or
-   `xml`, indicates output as XML.

**Note**: URLs must be [properly encoded](https://developers.google.com/maps/documentation/distance-matrix/web-service-best-practices#BuildingURLs) to be valid and are limited to 8192 characters for all web services. Be aware of this limit when constructing your URLs. Note that different browsers, proxies, and servers may have different URL character limits as well.

#### HTTPS or HTTP

HTTPS is recommended whenever possible, and is required for applications that include sensitive user data - such as a user's location - in requests.

If HTTPS is not possible, to access the Distance Matrix API over HTTP, use:

**http**://maps.googleapis.com/maps/api/distancematrix/outputFormat?parameters 

### Request parameters

Certain parameters are required while others are optional. As is standard in URLs, all parameters are separated using the ampersand (`&`) character. All reserved characters (for example the plus sign "+") must be [URL-encoded](https://developers.google.com/maps/documentation/directions/web-service-best-practices#BuildingURLs). The list of parameters and their possible values are enumerated below.

### Required parameters

-   `origins` — The starting point for calculating travel distance and time. You can supply one or more locations separated by the pipe character (`|`), in the form of a place ID, an address, or latitude/longitude coordinates:
    
    -   If you supply a place ID, you must prefix it with `place_id:`. You can only specify a place ID if the request includes an API key or a Google Maps Platform Premium Plan client ID. You can retrieve place IDs from the Geocoding API and the Places API (including Place Autocomplete). For an example using place IDs from Place Autocomplete, see [Place Autocomplete and Directions](https://developers.google.com/maps/documentation/javascript/examples/places-autocomplete-directions). For more about place IDs, see the [place ID overview](https://developers.google.com/maps/documentation/places/web-service/place-id).
    -   If you pass an address, the service geocodes the string and converts it to a latitude/longitude coordinate to calculate distance. This coordinate may be different from that returned by the Geocoding API, for example a building entrance rather than its center.
        
        origins\=Bobcaygeon+ON|24+Sussex+Drive+Ottawa+ON
        
        Note: using place IDs is preferred over using addresses or latitude/longitude coordinates. Using coordinates will always result in the point being snapped to the road nearest to those coordinates - which may not be an access point to the property, or even a road that will quickly or safely lead to the destination.
        
    -   If you pass latitude/longitude coordinates, they will snap to the nearest road. Passing a place ID is preferred. If you do pass coordinates, ensure that no space exists between the latitude and longitude values.
        
        origins\=41.43206,-81.38992|-33.86748,151.20699
        
          
        
        origins\=place\_id:ChIJ3S\-JXmauEmsRUcIaWtf4MzE
        
    -   Plus codes must be formatted as a global code or a compound code. Format plus codes as shown here (plus signs are url-escaped to `%2B` and spaces are url-escaped to `%20`):
        -   **global code** is a 4 character area code and 6 character or longer local code (849VCWC8+R9 is `849VCWC8%2BR9`).
        -   **compound code** is a 6 character or longer local code with an explicit location (CWC8+R9 Mountain View, CA, USA is `CWC8%2BR9%20Mountain%20View%20CA%20USA`).
    
    -   Alternatively, you can supply an encoded set of coordinates using the [Encoded Polyline Algorithm](https://developers.google.com/maps/documentation/utilities/polylinealgorithm). This is particularly useful if you have a large number of origin points, because the URL is significantly shorter when using an encoded polyline.
        -   Encoded polylines must be prefixed with `enc:` and followed by a colon (`:`).For example: `origins=enc:gfo}EtohhU:`
        -   You can also include multiple encoded polylines, separated by the pipe character (`|`). For example: `origins=enc:wc~oAwquwMdlTxiKtqLyiK:|enc:c~vnAamswMvlTor@tjGi}L:|enc:udymA{~bxM:`
-   `destinations` — One or more locations to use as the finishing point for calculating travel distance and time. The options for the `destinations` parameter are the same as for the `origins` parameter, described above.
-   `key` — Your application's API key. This key identifies your application for purposes of quota management. Learn how to [get a key](https://developers.google.com/maps/documentation/distance-matrix/get-api-key).
    
    **Note: Google Maps Platform Premium Plan** customers may use either an API key, or a valid client ID and digital signature, in your Distance Matrix requests. Get more information on [authentication parameters for Premium Plan customers](https://developers.google.com/maps/documentation/distance-matrix/get-api-key#premium-auth).

The following example uses latitude/longitude coordinates to specify the destination coordinates:

```
https://maps.googleapis.com/maps/api/distancematrix/json?units=imperial&origins=40.6655101,-73.89188969999998&destinations=40.6905615%2C-73.9976592%7C40.6905615%2C-73.9976592%7C40.6905615%2C-73.9976592%7C40.6905615%2C-73.9976592%7C40.6905615%2C-73.9976592%7C40.6905615%2C-73.9976592%7C40.659569%2C-73.933783%7C40.729029%2C-73.851524%7C40.6860072%2C-73.6334271%7C40.598566%2C-73.7527626%7C40.659569%2C-73.933783%7C40.729029%2C-73.851524%7C40.6860072%2C-73.6334271%7C40.598566%2C-73.7527626&key=YOUR\_API\_KEY  
```

The following example uses plus codes to specify the destination coordinates:

```
https://maps.googleapis.com/maps/api/distancematrix/json?units=imperial&origins=H8MW%2BWP%20Kolkata%20India&destinations=GCG2%2B3M%20Kolkata%20India&key=YOUR\_API\_KEY  
```

The following example shows the same request using an encoded polyline:

```
https://maps.googleapis.com/maps/api/distancematrix/json?units=imperial&origins=40.6655101,-73.89188969999998&destinations=enc:\_kjwFjtsbMt%60EgnKcqLcaOzkGari%40naPxhVg%7CJjjb%40cqLcaOzkGari%40naPxhV:&key=YOUR\_API\_KEY  
```

### Optional parameters

-   `mode` (defaults to `driving`) — Specifies the mode of transport to use when calculating distance. Valid values and other request details are specified in the [Travel Modes](https://developers.google.com/maps/documentation/distance-matrix/overview#travel_modes) section of this document.
-   `language` — The language in which to return results.
    -   See the [list of supported languages](https://developers.google.com/maps/faq#languagesupport). Google often updates the supported languages, so this list may not be exhaustive.
    -   If `language` is not supplied, the API attempts to use the preferred language as specified in the `Accept-Language` header, or the native language of the domain from which the request is sent.
    -   The API does its best to provide a street address that is readable for both the user and locals. To achieve that goal, it returns street addresses in the local language, transliterated to a script readable by the user if necessary, observing the preferred language. All other addresses are returned in the preferred language. Address components are all returned in the same language, which is chosen from the first component.
    -   If a name is not available in the preferred language, the API uses the closest match.
    -   The preferred language has a small influence on the set of results that the API chooses to return, and the order in which they are returned. The geocoder interprets abbreviations differently depending on language, such as the abbreviations for street types, or synonyms that may be valid in one language but not in another. For example, _utca_ and _tér_ are synonyms for street in Hungarian.
-   `region` — The region code, specified as a [ccTLD](https://en.wikipedia.org/wiki/CcTLD) (country code top-level domain) two-character value. Most ccTLD codes are identical to ISO 3166-1 codes, with some exceptions. This parameter will only influence, not fully restrict, results from the geocoder. If more relevant results exist outside of the specified region, they may be included.
-   `avoid` — Introduces restrictions to the route. Valid values are specified in the [Restrictions](https://developers.google.com/maps/documentation/distance-matrix/overview#Restrictions) section of this document. Only one restriction can be specified.
-   `units` — Specifies the unit system to use when expressing distance as text. See the [Unit systems](https://developers.google.com/maps/documentation/distance-matrix/overview#unit-systems) section of this document for more information.
-   `arrival_time` — Specifies the desired time of arrival for transit requests, in seconds since midnight, January 1, 1970 UTC. You can specify either `departure_time` or `arrival_time`, but not both. Note that `arrival_time` must be specified as an integer.
-   `departure_time` — The desired time of departure. You can specify the time as an integer in seconds since midnight, January 1, 1970 UTC. If a `departure_time` later than 9999-12-31T23:59:59.999999999Z is specified, the API will fall back the `departure_time` to 9999-12-31T23:59:59.999999999Z. Alternatively, you can specify a value of `now`, which sets the departure time to the current time (correct to the nearest second). The departure time may be specified in two cases:
    -   For requests where the travel mode is transit: You can optionally specify one of `departure_time` or `arrival_time`. If neither time is specified, the `departure_time` defaults to now (that is, the departure time defaults to the current time).
    -   For requests where the travel mode is driving: You can specify the `departure_time` to receive a route and trip duration (response field: `duration_in_traffic`) that take traffic conditions into account. This option is only available if the request contains a valid API key, or a valid Google Maps Platform Premium Plan client ID and signature. The `departure_time` must be set to the current time or some time in the future. It cannot be in the past.
        
        **Note:** If departure time is not specified, choice of route and duration are based on road network and average time-independent traffic conditions. Results for a given request may vary over time due to changes in the road network, updated average traffic conditions, and the distributed nature of the service. Results may also vary between nearly-equivalent routes at any time or frequency.
        
        **Note:** Distance Matrix requests specifying `departure_time` when `mode=driving` are limited to a maximum of 100 elements per request. The number of _origins_ times the number of _destinations_ defines the number of elements.
    
-   `traffic_model` (defaults to `best_guess`) — Specifies the assumptions to use when calculating time in traffic. This setting affects the value returned in the `duration_in_traffic` field in the response, which contains the predicted time in traffic based on historical averages. The `traffic_model` parameter may only be specified for requests where the travel mode is `driving`, and where the request includes a `departure_time`, and only if the request includes an API key or a Google Maps Platform Premium Plan client ID. The available values for this parameter are:
    -   `best_guess` (default) indicates that the returned `duration_in_traffic` should be the best estimate of travel time given what is known about both historical traffic conditions and live traffic. Live traffic becomes more important the closer the `departure_time` is to now.
    -   `pessimistic` indicates that the returned `duration_in_traffic` should be longer than the actual travel time on most days, though occasional days with particularly bad traffic conditions may exceed this value.
    -   `optimistic` indicates that the returned `duration_in_traffic` should be shorter than the actual travel time on most days, though occasional days with particularly good traffic conditions may be faster than this value.
-   `transit_mode` — Specifies one or more preferred modes of transit. This parameter may only be specified for requests where the `mode` is `transit`. The parameter supports the following arguments:
    -   `bus` indicates that the calculated route should prefer travel by bus.
    -   `subway` indicates that the calculated route should prefer travel by subway.
    -   `train` indicates that the calculated route should prefer travel by train.
    -   `tram` indicates that the calculated route should prefer travel by tram and light rail.
    -   `rail` indicates that the calculated route should prefer travel by train, tram, light rail, and subway. This is equivalent to `transit_mode=train|tram|subway`.
-   `transit_routing_preference` — Specifies preferences for transit requests. Using this parameter, you can bias the options returned, rather than accepting the default best route chosen by the API. This parameter may only be specified for requests where the `mode` is `transit`. The parameter supports the following arguments:
    -   `less_walking` indicates that the calculated route should prefer limited amounts of walking.
    -   `fewer_transfers` indicates that the calculated route should prefer a limited number of transfers.

### Travel modes

For the calculation of distances, you may specify the transportation `mode` to use. By default, distances are calculated for driving mode. The following travel modes are supported:

-   `driving` (default) indicates distance calculation using the road network.
-   `walking` requests distance calculation for walking via pedestrian paths & sidewalks (where available).
-   `bicycling` requests distance calculation for bicycling via bicycle paths & preferred streets (where available).
-   `transit` requests distance calculation via public transit routes (where available). This value may only be specified if the request includes an API key or a Google Maps Platform Premium Plan client ID. If you set the mode to `transit` you can optionally specify either a `departure_time` or an `arrival_time`. If neither time is specified, the `departure_time` defaults to now (that is, the departure time defaults to the current time). You can also optionally include a `transit_mode` and/or a `transit_routing_preference`.

### Traffic information

Traffic information is used when **all** the following apply (these are the conditions required to receive the [`duration_in_traffic`](https://developers.google.com/maps/documentation/distance-matrix/intro#duration_in_traffic) field in the Distance Matrix response):

-   The [travel `mode`](https://developers.google.com/maps/documentation/distance-matrix/intro#travel_modes) parameter is `driving`, or is not specified (`driving` is the default travel mode).
-   The request includes a valid [`departure_time` parameter](https://developers.google.com/maps/documentation/distance-matrix/intro#departure-time). The `departure_time` can be set to the current time or some time in the future. It cannot be in the past.

Optionally, you can include the [`traffic_model`](https://developers.google.com/maps/documentation/distance-matrix/intro#traffic-model) parameter in your request to specify the assumptions to use when calculating time in traffic.

The following URL initiates a Distance Matrix request for driving distances between Boston, MA or Charlestown, MA, and Lexington, MA and Concord, MA. The request includes a departure time, meeting all the requirements to return the `duration_in_traffic` field in the Distance Matrix response.

https://maps.googleapis.com/maps/api/distancematrix/json?origins=Boston,MA|Charlestown,MA&destinations=Lexington,MA|Concord,MA&departure\_time=now&key=YOUR\_API\_KEY  

### Restrictions

Distances may be calculated that adhere to certain restrictions. Restrictions are indicated by use of the `avoid` parameter, and an argument to that parameter indicating the restriction to avoid. The following restrictions are supported:

-   `avoid=tolls`
-   `avoid=highways`
-   `avoid=ferries`
-   `avoid=indoor`

**\* Note**: the addition of restrictions does not preclude routes that include the restricted feature; it biases the result to more favorable routes.

### Unit systems

Distance Matrix results contain `text` within `distance` fields to indicate the distance of the calculated route. The unit system to use can be specified:

-   `units=metric` (default) returns distances in kilometers and meters.
-   `units=imperial` returns distances in miles and feet.

**\* Note**: this unit system setting only affects the `text` displayed within `distance` fields. The `distance` fields also contain `values` which are always expressed in meters.

### Location Modifiers

You can use location modifiers to indicate how drivers should approach a particular location, by using the `side_of_road` parameter to specify which side of the road to use, or by specifying a heading to indicate the correct direction of travel.

#### Specify that calculated routes must pass through a particular side of the road

When specifying a location, you can request that the calculated route go through whichever side of the road the waypoint is biased towards by using the `side_of_road:` prefix. For example, this request will return the distance for a long route so that the vehicle ends on the side of the road to which the waypoint was biased:

https://maps.googleapis.com/maps/api/distancematrix/json?  
origins\=37.7680296,-122.4375126  
&destinations\=side\_of\_road:37.7663444,-122.4412006  
&key\=YOUR\_API\_KEY  

When using `side_of_road:` with encoded polylines, the parameter is applied to every location along the polyline. For example, the two destinations in this request both use the parameter:

https://maps.googleapis.com/maps/api/distancematrix/json?  
origins\=San+Francisco+City+hall  
&destinations\=side\_of\_road:enc:{oqeF\`fejV\[nC:  
&key=YOUR\_API\_KEY  

The `side_of_road:` modifier may only be used with the following restrictions:

-   The [travel `mode`](https://developers.google.com/maps/documentation/distance-matrix/overview#travel_modes) parameter is `driving`, or is not specified (`driving` is the default travel mode).

#### Specify that calculated routes should have a particular heading

When specifying a location, you can request that the calculated route go through the location in a particular heading. This heading is specified with the prefix `heading=X:`, where X is an integer degree value between 0 (inclusive) and 360 (exclusive). A heading of 0 indicates North, 90 indicates East, and so on, continuing clockwise. For example, in this request the calculated route goes east from the origin, then takes a U-turn:

https://maps.googleapis.com/maps/api/distancematrix/json?  
origins\=heading\=90:37.773279,-122.468780  
&destinations\=37.773245,-122.469502  
&key\=YOUR\_API\_KEY  

The `heading=X:` modifier may only be used with the following restrictions:

-   The [travel `mode`](https://developers.google.com/maps/documentation/distance-matrix/overview#travel_modes) parameter is `driving`, `bicycling`, or is not specified (`driving` is the default travel mode).
-   The [`side_of_road`](https://developers.google.com/maps/documentation/distance-matrix/overview#side-of-road) modifier is not specified for the same location.
-   The location is specified with a latitude/longitude value. You may not use `heading` with addresses, Place IDs, or encoded polylines.

## Distance Matrix responses

Responses to Distance Matrix API queries are returned in the format indicated by the `output` flag within the URL request's path.

Two sample HTTP requests are shown below, requesting distance and duration from Vancouver, BC, Canada and from Seattle, WA, USA, to San Francisco, CA, USA and to Victoria, BC, Canada.

This request demonstrates using the JSON `output` flag:

https://maps.googleapis.com/maps/api/distancematrix/json?origins=Vancouver+BC|Seattle&destinations=San+Francisco|Victoria+BC&mode=bicycling&language=fr-FR&key=YOUR\_API\_KEY

This request demonstrates using the XML `output` flag:

```
https://maps.googleapis.com/maps/api/distancematrix/xml?origins=Vancouver+BC|Seattle&destinations=San+Francisco|Victoria+BC&mode=bicycling&language=fr-FR&key=YOUR\_API\_KEY
```

This request will return four elements - two origins times two destinations:

|          From              |  To                   |
| -------------------------- | --------------------- |
| Vancouver to San Francisco | Vancouver to Victoria |
| Seattle to San Francisco   | Seattle to Victoria   |






Results are returned in rows, each row containing one origin paired with each destination.

You can test this by entering the URL into your web browser (be sure to replace `YOUR_API_KEY` with [your actual API key](https://developers.google.com/maps/documentation/distance-matrix/get-api-key)).

Select the tabs below to see the sample JSON and XML responses.

```json
{
  "status": "OK",
  "origin_addresses": [
    "Vancouver, BC, Canada",
    "Seattle, État de Washington, États-Unis"
  ],
  "destination_addresses": [
    "San Francisco, Californie, États-Unis",
    "Victoria, BC, Canada"
  ],
  "rows": [
    {
      "elements": [
        {
          "status": "OK",
          "duration": {
            "value": 340110,
            "text": "3 jours 22 heures"
          },
          "distance": {
            "value": 1734542,
            "text": "1 735 km"
          }
        },
        {
          "status": "OK",
          "duration": {
            "value": 24487,
            "text": "6 heures 48 minutes"
          },
          "distance": {
            "value": 129324,
            "text": "129 km"
          }
        }
      ]
    },
    {
      "elements": [
        {
          "status": "OK",
          "duration": {
            "value": 288834,
            "text": "3 jours 8 heures"
          },
          "distance": {
            "value": 1489604,
            "text": "1 490 km"
          }
        },
        {
          "status": "OK",
          "duration": {
            "value": 14388,
            "text": "4 heures 0 minutes"
          },
          "distance": {
            "value": 135822,
            "text": "136 km"
          }
        }
      ]
    }
  ]
}
```

Note that these results generally need to be _parsed_ if you wish to extract values from the results. Parsing JSON is relatively easy. See [Parsing JSON](https://developers.google.com/maps/documentation/distance-matrix/web-service-best-practices#ParsingJSON) for some recommended design patterns.

<?xml version\="1.0" encoding\="UTF-8"?>  
<DistanceMatrixResponse>  <status>OK</status>  <origin\_address>Vancouver, BC, Canada</origin\_address>  <origin\_address>Seattle, État de Washington, États-Unis</origin\_address>  <destination\_address>San Francisco, Californie, États-Unis</destination\_address>  <destination\_address>Victoria, BC, Canada</destination\_address>  <row>  <element>  <status>OK</status>  <duration>  <value>340110</value>  <text>3 jours 22 heures</text>  </duration>  <distance>  <value>1734542</value>  <text>1 735 km</text>  </distance>  </element>  <element>  <status>OK</status>  <duration>  <value>24487</value>  <text>6 heures 48 minutes</text>  </duration>  <distance>  <value>129324</value>  <text>129 km</text>  </distance>  </element>  </row>  <row>  <element>  <status>OK</status>  <duration>  <value>288834</value>  <text>3 jours 8 heures</text>  </duration>  <distance>  <value>1489604</value>  <text>1 490 km</text>  </distance>  </element>  <element>  <status>OK</status>  <duration>  <value>14388</value>  <text>4 heures 0 minutes</text>  </duration>  <distance>  <value>135822</value>  <text>136 km</text>  </distance>  </element>  </row>  
</DistanceMatrixResponse>  

We recommend that you use `json` as the preferred output flag unless your service requires `xml` for some reason. Processing XML trees requires some care, so that you reference proper nodes and elements. See [Parsing XML with XPath](https://developers.google.com/maps/documentation/distance-matrix/web-service-best-practices#ParsingXML) for some recommended design patterns for output processing.

The remainder of this documentation will use JSON syntax.

### Distance Matrix response elements

Distance Matrix responses contain the following root elements:

-   `status` contains metadata on the request. See [Status Codes](https://developers.google.com/maps/documentation/distance-matrix/overview#status-codes) below.
-   `origin_addresses` contains an array of addresses as returned by the API from your original request. These are formatted by the [geocoder](https://developers.google.com/maps/documentation/geocoding) and localized according to the `language` parameter passed with the request.
-   `destination_addresses` contains an array of addresses as returned by the API from your original request. As with `origin_addresses`, these are localized if appropriate.
-   `rows` contains an array of `elements`, which in turn each contain a `status`, `duration`, and `distance` element.

### Status codes

The `status` fields within the response object contain the status of the request, and may contain useful debugging information. The Distance Matrix API returns a top-level status field, with information about the request in general, as well as a status field for each element field, with information about that particular origin-destination pairing.

#### Top-level status codes

-   `OK` indicates the response contains a valid `result`.
-   `INVALID_REQUEST` indicates that the provided request was invalid.
-   `MAX_ELEMENTS_EXCEEDED` indicates that the product of origins and destinations exceeds the per-query [limit](https://developers.google.com/maps/documentation/distance-matrix/usage-and-billing).
-   `MAX_DIMENSIONS_EXCEEDED` indicates that the number of origins or destinations exceeds the per-query [limit](https://developers.google.com/maps/documentation/distance-matrix/usage-and-billing).
-   `OVER_DAILY_LIMIT` indicates any of the following:
    
    -   The API key is missing or invalid.
    -   Billing has not been enabled on your account.
    -   A self-imposed usage cap has been exceeded.
    -   The provided method of payment is no longer valid (for example, a credit card has expired).
    
    See the [Maps FAQ](https://developers.google.com/maps/faq#over-limit-key-error) to learn how to fix this.
    
-   `OVER_QUERY_LIMIT` indicates the service has received too many requests from your application within the allowed time period.
-   `REQUEST_DENIED` indicates that the service denied use of the Distance Matrix service by your application.
-   `UNKNOWN_ERROR` indicates a Distance Matrix request could not be processed due to a server error. The request may succeed if you try again.

#### Element-level status codes

-   `OK` indicates the response contains a valid `result`.
-   `NOT_FOUND` indicates that the origin and/or destination of this pairing could not be geocoded.
-   `ZERO_RESULTS` indicates no route could be found between the origin and destination.
-   `MAX_ROUTE_LENGTH_EXCEEDED` indicates the requested route is too long and cannot be processed.

### Error messages

When the top-level status code is other than `OK`, there may be an additional `error_message` field within the Distance Matrix response object. This field contains more detailed information about the reasons behind the given status code.

**Note:** This field is not guaranteed to be always present, and its content is subject to change.

### Rows

When the Distance Matrix API returns results, it places them within a JSON `rows` array. Even if no results are returned (such as when the origins and/or destinations don't exist), it still returns an empty array. XML responses consist of zero or more `<row>` elements.

Rows are ordered according to the values in the `origin` parameter of the request. Each row corresponds to an origin, and each `element` within that row corresponds to a pairing of the origin with a `destination` value.

Each `row` array contains one or more `element` entries, which in turn contain the information about a single origin-destination pairing.

### Elements

The information about each origin-destination pairing is returned in an `element` entry. An `element` contains the following fields:

-   `status`: See [Status Codes](https://developers.google.com/maps/documentation/distance-matrix/overview#status-codes) for a list of possible status codes.
-   `duration`: The length of time it takes to travel this route, expressed in seconds (the `value` field) and as `text`. The textual representation is localized according to the query's `language` parameter.
-   `duration_in_traffic`: The length of time it takes to travel this route, based on current and historical traffic conditions. See the `traffic_model` request parameter for the options you can use to request that the returned value is optimistic, pessimistic, or a best-guess estimate. The duration is expressed in seconds (the `value` field) and as `text`. The textual representation is localized according to the query's `language` parameter. The duration in traffic is returned only if all of the following are true:
    
    -   The request includes a `departure_time` parameter.
    -   The request includes a valid API key, or a valid Google Maps Platform Premium Plan client ID and signature.
    -   Traffic conditions are available for the requested route.
    -   The `mode` parameter is set to `driving`.
-   `distance`: The total distance of this route, expressed in meters (`value`) and as `text`. The textual value uses the unit system specified with the `unit` parameter of the original request, or the origin's region.
-   `fare`: If present, contains the total fare (that is, the total ticket costs) on this route. This property is only returned for transit requests and only for transit providers where fare information is available. The information includes:
    -   `currency`: An [ISO 4217 currency code](https://en.wikipedia.org/wiki/ISO_4217) indicating the currency that the amount is expressed in.
    -   `value`: The total fare amount, in the currency specified above.
    -   `text`: The total fare amount, formatted in the requested language.

Below is an example of an `element` containing fare information:

{  "status": "OK",  "duration": {  "value": 340110,  "text": "3 jours 22 heures"  },  "distance": {  "value": 1734542,  "text": "1 735 km"  }  "fare" : {  "currency" : "USD",  "value" : 6,  "text" : "$6.00"  },  
}  

## The `sensor` parameter

The Google Maps API previously required that you include the `sensor` parameter to indicate whether your application used a sensor to determine the user's location. This parameter is no longer required.

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2021-05-14 UTC.

***

Links: [[Google Maps APIs]]

Source: [Overview  |  Distance Matrix API  |  Google Developers](https://developers.google.com/maps/documentation/distance-matrix/overview)