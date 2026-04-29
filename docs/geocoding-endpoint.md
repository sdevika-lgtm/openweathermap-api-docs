# Get Geocoding Data

## Overview

Converts a city name into geographic coordinates (latitude and longitude). Use this endpoint to get coordinates before calling other OpenWeatherMap endpoints that require lat and lon parameters.

## Endpoint

`GET https://api.openweathermap.org/geo/1.0/direct`

## Base URL
`https://api.openweathermap.org`

## Authentication

All requests require a valid API key passed as a query parameter.

## Request Parameters

| Parameter | Type   | Required | Description                                      |
|-----------|--------|----------|--------------------------------------------------|
| q         | string | Yes      | City name (e.g. Bangalore)                       |
| limit     | number | No       | Number of results to return. Maximum is 5        |
| appid     | string | Yes      | Your unique API key                              |

## Sample Request

```bash
curl "https://api.openweathermap.org/geo/1.0/direct?q=Bangalore&limit=5&appid=YOUR_API_KEY"
```

## Sample Response

```json
[
    {
        "name": "Bengaluru",
        "local_names": {
            "en": "Bengaluru",
            "hi": "बेंगलुरू",
            "fr": "Bangalore",
            "de": "Bangalore"
        },
        "lat": 12.9767936,
        "lon": 77.590082,
        "country": "IN",
        "state": "Karnataka"
    }
]
```

> **Note:** The `local_names` object contains the city name in multiple languages. Only a few are shown here for brevity.

## Response Fields

| Field | Type | Description |
|-------|------|-------------|
| name | string | City name in English |
| local_names | object | City name in multiple languages, keyed by language code |
| lat | number | Latitude of the city |
| lon | number | Longitude of the city |
| country | string | Country code (e.g. IN) |
| state | string | State or region the city belongs to |

## Error Responses

| Code | Message | Description |
|------|---------|-------------|
| 401  | Invalid API key | The API key is missing or incorrect |
| 400  | Nothing to geocode | The city name parameter is missing |
| 429  | Too many requests | You have exceeded your API call limit |

## Usage Tip

Use the `lat` and `lon` values returned by this endpoint as input parameters for the Air Pollution endpoint.
