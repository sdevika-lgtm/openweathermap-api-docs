# Get 5 Day Weather Forecast

## Overview

Returns weather forecast data for a specified city in 3-hour intervals for 5 days.

## Endpoint

`GET https://api.openweathermap.org/data/2.5/forecast`

## Base URL

`https://api.openweathermap.org`

## Authentication

All requests require a valid API key passed as a query parameter.

## Request Parameters

| Parameter | Type   | Required | Description                        |
|-----------|--------|----------|------------------------------------|
| q         | string | Yes      | City name (e.g. Bangalore)         |
| appid     | string | Yes      | Your unique API key                |
| cnt       | number | No       | Number of timestamps to return. Maximum is 40 |

## Sample Request

```bash
curl "https://api.openweathermap.org/data/2.5/forecast?q=Bangalore&appid=YOUR_API_KEY"
```

## Sample Response
```json
{
    "cod": "200",
    "message": 0,
    "cnt": 40,
    "list": [
        {
            "dt": 1777474800,
            "main": {
                "temp": 305.5,
                "feels_like": 308.96,
                "temp_min": 303.75,
                "temp_max": 305.5,
                "pressure": 1009,
                "sea_level": 1009,
                "grnd_level": 912,
                "humidity": 53,
                "temp_kf": 1.75
            },
            "weather": [
                {
                    "id": 500,
                    "main": "Rain",
                    "description": "light rain",
                    "icon": "10n"
                }
            ],
            "clouds": {
                "all": 75
            },
            "wind": {
                "speed": 1.31,
                "deg": 230,
                "gust": 3.18
            },
            "visibility": 10000,
            "pop": 0.9,
            "rain": {
                "3h": 0.94
            },
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2026-04-29 15:00:00"
        }
    ],
    "city": {
        "id": 1277333,
        "name": "Bengaluru",
        "coord": {
            "lat": 12.9762,
            "lon": 77.6033
        },
        "country": "IN",
        "population": 5104047,
        "timezone": 19800,
        "sunrise": 1777422588,
        "sunset": 1777467836
    }
}
```
## Response Fields
### Top Level Fields

| Field | Type | Description |
|-------|------|-------------|
| cod | string | HTTP status code of the response |
| message | number | Internal parameter |
| cnt | number | Number of timestamps returned |
| list | array | List of forecast data in 3-hour intervals |

### list fields

| Field | Type | Description |
|-------|------|-------------|
| list[].dt | number | Forecast time as a Unix timestamp |
| list[].dt_txt | string | Forecast time in UTC format (e.g. 2026-04-29 15:00:00) |
| list[].main.temp | number | Temperature in Kelvin |
| list[].main.feels_like | number | Perceived temperature in Kelvin |
| list[].main.temp_min | number | Minimum temperature at the time of forecast |
| list[].main.temp_max | number | Maximum temperature at the time of forecast |
| list[].main.pressure | number | Atmospheric pressure in hPa |
| list[].main.sea_level | number | Atmospheric pressure at sea level in hPa |
| list[].main.grnd_level | number | Atmospheric pressure at ground level in hPa |
| list[].main.humidity | number | Humidity percentage |
| list[].main.temp_kf | number | Internal temperature correction factor |
| list[].weather[].id | number | Weather condition code |
| list[].weather[].main | string | Short weather category (e.g. Rain, Clouds) |
| list[].weather[].description | string | Detailed weather description |
| list[].weather[].icon | string | Icon code for the weather condition |
| list[].clouds.all | number | Cloudiness percentage |
| list[].wind.speed | number | Wind speed in metres per second |
| list[].wind.deg | number | Wind direction in degrees |
| list[].wind.gust | number | Wind gust speed in metres per second |
| list[].visibility | number | Visibility in metres. Maximum is 10000 |
| list[].pop | number | Probability of precipitation. Values range from 0 to 1 |
| list[].rain.3h | number | Rain volume in mm for the last 3 hours |
| list[].sys.pod | string | Part of day. d for day, n for night |

### city fields

| Field | Type | Description |
|-------|------|-------------|
| city.id | number | City ID |
| city.name | string | City name |
| city.coord.lat | number | Latitude of the city |
| city.coord.lon | number | Longitude of the city |
| city.country | string | Country code (e.g. IN) |
| city.population | number | City population |
| city.timezone | number | Timezone offset from UTC in seconds |
| city.sunrise | number | Sunrise time as a Unix timestamp |
| city.sunset | number | Sunset time as a Unix timestamp |
## Error Responses

| Code | Message | Description |
|------|---------|-------------|
| 401  | Invalid API key | The API key is missing or incorrect |
| 404  | City not found | The city name provided does not exist |
| 429  | Too many requests | You have exceeded your API call limit |


