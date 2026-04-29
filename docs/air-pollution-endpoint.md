# Get Air Pollution Data

## Overview

Returns current air quality data for a specified location using latitude and longitude coordinates.

## Endpoint

`GET https://api.openweathermap.org/data/2.5/air_pollution`

## Base URL

`https://api.openweathermap.org`

## Authentication

All requests require a valid API key passed as a query parameter.

## Request Parameters

| Parameter | Type   | Required | Description                        |
|-----------|--------|----------|------------------------------------|
| lat       | number | Yes      | Latitude of the location           |
| lon       | number | Yes      | Longitude of the location          |
| appid     | string | Yes      | Your unique API key                |

## Sample Request

```bash
curl "https://api.openweathermap.org/data/2.5/air_pollution?lat=12.9762&lon=77.6033&appid=YOUR_API_KEY"
```

## Sample Response

```json
{
    "coord": {
        "lon": 77.6033,
        "lat": 12.9762
    },
    "list": [
        {
            "main": {
                "aqi": 3
            },
            "components": {
                "co": 311.68,
                "no": 0,
                "no2": 11.13,
                "o3": 76.33,
                "so2": 5.18,
                "pm2_5": 26.15,
                "pm10": 33.57,
                "nh3": 8.85
            },
            "dt": 1777477024
        }
    ]
}
```

## Response Fields

### Top Level Fields

| Field | Type | Description |
|-------|------|-------------|
| coord.lon | number | Longitude of the location |
| coord.lat | number | Latitude of the location |
| list | array | List containing the air pollution data |

### list fields

| Field | Type | Description |
|-------|------|-------------|
| list[].main.aqi | number | Air Quality Index. Values range from 1 (Good) to 5 (Very Poor) |
| list[].components.co | number | Concentration of carbon monoxide in μg/m³ |
| list[].components.no | number | Concentration of nitrogen monoxide in μg/m³ |
| list[].components.no2 | number | Concentration of nitrogen dioxide in μg/m³ |
| list[].components.o3 | number | Concentration of ozone in μg/m³ |
| list[].components.so2 | number | Concentration of sulphur dioxide in μg/m³ |
| list[].components.pm2_5 | number | Concentration of fine particles in μg/m³ |
| list[].components.pm10 | number | Concentration of coarse particles in μg/m³ |
| list[].components.nh3 | number | Concentration of ammonia in μg/m³ |
| list[].dt | number | Measurement time as a Unix timestamp |

## AQI Scale

| AQI Value | Description |
|-----------|-------------|
| 1 | Good |
| 2 | Fair |
| 3 | Moderate |
| 4 | Poor |
| 5 | Very Poor |

## Error Responses

| Code | Message | Description |
|------|---------|-------------|
| 401  | Invalid API key | The API key is missing or incorrect |
| 400  | Nothing to geocode | Coordinates are missing or invalid |
| 429  | Too many requests | You have exceeded your API call limit |
