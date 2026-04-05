
# Breathing Easy: Air Quality and Asthma Comparisons Across Kentucky Regions

An analysis of how air quality affects people with asthma across Kentucky regions. This project combines EPA air quality data, CDC data centered on asthma, and real-time PurpleAir sensor readings to explore disparities in medical care access, identify high risk areas, and determine whether the actual occurence of Asthma Peak Week aligns with the industry expected third week of September.


## Run Locally

Clone the project

```bash
  git clone https://github.com/DaviLeeAnn/Air_Quality_and_Asthma_Comparisons
```

Go to the project directory

```bash
  cd Air_Quality_and_Asthma_Comparisons
```

Create a virtual environment and activate it

```bash
  # Windows
  python -m venv venv
  source venv/Scripts/activate

  # Mac
  python3 -m venv .venv
  source .venv/bin/activate
```

Install dependencies

```bash
  pip install -r requirements.txt
```

Start the project file

```bash
  code .
```

When done, deactivate the environment
```bash
  deactivate
  ```
## Data Sources
1. U.S. Environmental Protection Agency (EPA) — Pre-Generated Data Files
- Fields used: PM2.5, Days Ozone, County, State, Year (2022)
- Link: https://aqs.epa.gov/aqsweb/airdata/download_files.html
2. Centers for Disease Control (CDC) — National Environmental Public Health Tracking Network
- Fields used: Annual ER Visits, Asthma-Related Hospitalizations, County, State, Year (2022)
- Link: https://ephtracking.cdc.gov/DataExplorer/
3. PurpleAir API
- Fields used: PM2.5, Humidity, Temperature, Sensor Location (Latitude/Longitude)
- Link: https://community.purpleair.com/t/about-the-purpleair-api/7145
## API Reference

#### Get All Kentucky Sensors
```http
GET https://api.purpleair.com/v1/sensors
```

| Parameter | Type | Description |
| :-------- | :------- | :------------------------- |
| `X-API-Key` | `string` | **Required**. Your PurpleAir read key |
| `fields` | `string` | **Required**. Data fields to return |
| `location_type` | `int` | `0` = outdoor, `1` = indoor |

#### Get Single Sensor
```http
GET https://api.purpleair.com/v1/sensors/${sensor_index}
```

| Parameter | Type | Description |
| :-------- | :------- | :-------------------------------- |
| `X-API-Key` | `string` | **Required**. Your PurpleAir read key |
| `sensor_index` | `int` | **Required**. Index of the sensor to fetch |

#### get_sensors_by_air_quality(threshold)

Returns all Kentucky sensors where PM2.5 exceeds the given threshold.
## Acknowledgements
 The following tools, libraries, and resources were used in this project:
-	Python
-   VSCode
-   Jupyter Notebooks
-	pandas
-	matplotlib
-   seaborn
-	folium
-	requests
-	python-dotenv
-	Claude (Anthropic)
-   readme.so




## Authors

- [@DaviLeeAnn](https://www.github.com/DaviLeeAnn)


## License

[MIT](https://choosealicense.com/licenses/mit/)

