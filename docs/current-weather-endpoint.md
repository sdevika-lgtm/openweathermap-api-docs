# Get Current Weather

## Overview

Returns the current weather data for a specified city.

## Endpoint

```GET https://api.openweathermap.org/data/2.5/weather```

## Base URL

```https://api.openweathermap.org```

## Authentication

All requests require a valid API key passed as a query parameter.

## Request Parameters

| Parameter | Type   | Required | Description                        |
|-----------|--------|----------|------------------------------------|
| q         | string | Yes      | City name (e.g. Bangalore)         |
| appid     | string | Yes      | Your unique API key                |

## Sample Request

```bash
curl "https://api.openweathermap.org/data/2.5/weather?q=Bangalore&appid=YOUR_API_KEY"
```

## Sample Response

```json
{
    "coord": {
        "lon": 77.6033,
        "lat": 12.9762
    },
    "weather": [
        {
            "id": 803,
            "main": "Clouds",
            "description": "broken clouds",
            "icon": "04n"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 304.37,
        "feels_like": 306.34,
        "temp_min": 300.94,
        "temp_max": 306.21,
        "pressure": 1007,
        "humidity": 51,
        "sea_level": 1007,
        "grnd_level": 911
    },
    "visibility": 10000,
    "wind": {
        "speed": 6.26,
        "deg": 23,
        "gust": 27.27
    },
    "clouds": {
        "all": 74
    },
    "name": "Bengaluru",
    "cod": 200
}
```
## Response Fields

| Field | Type | Description |
|-------|------|-------------|
| coord.lon | number | Longitude of the city |
| coord.lat | number | Latitude of the city |
| weather.id | number | Weather condition code |
| weather.main | string | Short weather category (e.g. Clouds, Rain) |
| weather.description | string | Detailed weather description |
| weather.icon | string | Icon code for the weather condition |
| base | string | Internal data source used by OpenWeatherMap |
| main.temp | number | Current temperature in Kelvin |
| main.feels_like | number | Perceived temperature in Kelvin |
| main.temp_min | number | Minimum temperature at the time of call |
| main.temp_max | number | Maximum temperature at the time of call |
| main.pressure | number | Atmospheric pressure in hPa |
| main.humidity | number | Humidity percentage |
| main.sea_level | number | Atmospheric pressure at sea level in hPa |
| main.grnd_level | number | Atmospheric pressure at ground level in hPa |
| visibility | number | Visibility in metres. Maximum is 10000 |
| wind.speed | number | Wind speed in metres per second |
| wind.deg | number | Wind direction in degrees |
| wind.gust | number | Wind gust speed in metres per second |
| clouds.all | number | Cloudiness percentage |
| name | string | City name |
| cod | number | HTTP status code of the response |

## Error Responses

| Code | Message | Description |
|------|---------|-------------|
| 401 | Invalid API key | The API key is missing or incorrect |
| 404 | City not found | The city name provided does not exist |
| 429 | Too many requests | You have exceeded your API call limit |