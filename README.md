![Intro scenery: a glass rain gauge beaded with droplets and a brass barometer in close up on a rooftop mast after a shower, the brass needle steady on its new reading, an orange windsock soft in the background and a city skyline at dawn behind](intro-banner.png)

# Weather-Dashboard-Updater

![Wordmark banner: a rooftop weather station at dawn over a city skyline, an orange windsock stretched full by the wind, spinning anemometer cups, a rain gauge beaded with last night's rain and a brass barometer mounted on the mast](banner.png)

<p align="center"><img src="logo.png" alt="Weather-Dashboard-Updater logo: a flat illustration of a weather station mast on a rooftop, set inside a white frame on pale blue: spinning anemometer cups above, an orange windsock streaming, a brass barometer dial and a glass rain gauge mounted on grey steel" width="200"></p>

Gathers data about the weather from OpenWeatherMap API

[home.openweathermap.org/api_keys](https://home.openweathermap.org/api_keys)

# How to run this script?
Go sign up for OpenWeatherMap to obtain an API key, then run:

```
git clone https://github.com/Epsilon0xCell/Weather-Dashboard-Updater.git
rm -rf weatherupdate.csv # Remove the existing .csv as this includes previous data.
API_KEY = Insert_API_Key
pip install requests pandas
python3 get_weather_data.py
```

The file will be output to a .csv in the current working directory, allowing you to view the weather data in .csv format.

# Improving the structure and appearance of the output
The weather data is now saved in a CSV file (`weatherupdate.csv`) with improved structure and readability. The script `get_weather_data.py` extracts weather data from the OpenWeatherMap API and saves it to a CSV file, with the data well-organized and formatted for easy readability.

# Interpreting the structured weather data
The CSV file contains the following columns:
- `coord_lon`: Longitude of the location
- `coord_lat`: Latitude of the location
- `weather_id`: Weather condition id
- `weather_main`: Group of weather parameters (Rain, Snow, Extreme, etc.)
- `weather_description`: Weather condition within the group
- `weather_icon`: Weather icon id
- `base`: Internal parameter
- `main_temp`: Temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
- `main_feels_like`: Temperature. This temperature parameter accounts for the human perception of weather.
- `main_temp_min`: Minimum temperature at the moment. This is minimal currently observed temperature (within large megalopolises and urban areas), unit: Kelvin.
- `main_temp_max`: Maximum temperature at the moment. This is maximal currently observed temperature (within large megalopolises and urban areas), unit: Kelvin.
- `main_pressure`: Atmospheric pressure (on the sea level, if there is no sea_level or grnd_level data), hPa
- `main_humidity`: Humidity, %
- `visibility`: Visibility, meter
- `wind_speed`: Wind speed. Unit Default: meter/sec, Metric: meter/sec, Imperial: miles/hour.
- `wind_deg`: Wind direction, degrees (meteorological)
- `clouds_all`: Cloudiness, %
- `dt`: Time of data calculation, unix, UTC
- `sys_type`: Internal parameter
- `sys_id`: Internal parameter
- `sys_country`: Country code (GB, JP etc.)
- `sys_sunrise`: Sunrise time, unix, UTC
- `sys_sunset`: Sunset time, unix, UTC
- `timezone`: Shift in seconds from UTC
- `id`: City ID
- `name`: City name
- `cod`: Internal parameter

# Validating the CSV structure
The script now includes a validation step to ensure the CSV file has a consistent structure before appending new data. The `validate_csv_structure` function checks the structure of the existing `weatherupdate.csv` file and removes or corrects any inconsistent rows. This helps prevent errors when reading the CSV file with `pd.read_csv`.
