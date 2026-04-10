
# Breathing Easy: Air Quality and Asthma Comparisons Across Kentucky Regions

An analysis of how air quality affects people with asthma across Kentucky regions. This project combines EPA air quality data, CDC data centered on asthma, and real-time PurpleAir sensor readings to explore disparities in medical care access, identify high risk areas, and determine whether the actual occurance of Asthma Peak Week aligns with the industry expected third week of September.


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

Returns all Kentucky sensors where PM2.5 exceeds the given threshold.## Findings

Analysis focused on four Kentucky counties: Fayette, Pulaski, Pike, and Warren. Data sources included 2022 EPA air quality, CDC asthma outcomes, and real-time PurpleAir sensor data.

**Air Quality Patterns**
- June had the highest average air quality index (~56) across all four counties, consistent with the summer ozone season where heat accelerates ground-level ozone formation.
- September, which contains the industry recognized Asthma Peak Week (third week of September), did not show a notably elevated air quality index relative to the annual average (~40-42). The 2022 data does not confirm mid-September as a uniquely hazardous air quality period in these counties.

**Asthma Outcomes vs. Air Quality**
- Fayette County had the highest asthma related emergency room visits (~1,100) but one of the lower median air quality indeces (~44), while Pulaski had the highest median air quality index (~52) but relatively fewer emergency room visits (~160).
- This disconnect suggests population size is a major confounding factor, as Fayette County is the most populous county in the set by a wide margin likely due to the city of Lexington.
- Fayette County's high emergency room visit count may also reflect its role as a regional referral hub, with high level hospitals drawing transfer patients from surrounding counties for more severe asthma cases.
- Pike County showed the lowest emergency room visits and lowest median AQI, which does align with the expected relationship between air quality and health outcomes.

**Conclusion**

Air quality and asthma outcomes _are_ related, but the relationship is confounded by population size, access to care, and respiratory triggers unrelated to air quality alone. Future analysis could normalize ER visits by county population and incorporate socioeconomic indicators to better isolate the effect of air quality on asthma burden.
## Acknowledgements
 The following tools, libraries, and resources were used in this project:
-	Python
-   VSCode
-   Jupyter Notebooks
-	pandas
-	matplotlib
-   seaborn
-	folium
-   sqlite3
-	requests
-	python-dotenv
-	Claude (Anthropic)
-   readme.so




## Authors

- [@DaviLeeAnn](https://www.github.com/DaviLeeAnn)


## License

[MIT](https://choosealicense.com/licenses/mit/)

