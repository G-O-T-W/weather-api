# Weather Data API

A Flask-based web application that provides access to historical weather data. This API serves temperature data for specific stations and dates. It includes routes for fetching daily, annual, and station-specific temperature data, as well as a simple HTML page displaying available weather stations.

## Dataset Information

The weather data used in this project is sourced from the **European Climate Assessment & Dataset (ECA&D)**, created on 19-06-2022. The dataset contains daily surface air temperature and precipitation data for stations across Europe. The following citation must be acknowledged when using this data:

> Klein Tank, A.M.G. and Coauthors, 2002. Daily dataset of 20th-century surface air temperature and precipitation series for the European Climate Assessment. *Int. J. of Climatol.*, 22, 1441-1453. Data and metadata available at [https://www.ecad.eu](https://www.ecad.eu)

### File Format

- **STAID**: Station identifier (5 characters)
- **STANAME**: Station name (40 characters)
- **CN**: Country code (2 characters, ISO 3166)
- **LAT**: Latitude in degrees, minutes, and seconds (+: North, -: South)
- **LON**: Longitude in degrees, minutes, and seconds (+: East, -: West)
- **HGTH**: Station elevation in meters
- **Missing Value Code**: -9999

The weather station files (e.g., `TG_STAIDXXXXXX.txt`) contain daily temperature data, with `STAID` being the unique station identifier.

## Features

- **Retrieve Temperature by Station and Date**: Fetch temperature data for a specific weather station on a given date.
- **Station Data Overview**: Get the records of temperature data for a specific station.
- **Annual Data for a Station**: Retrieve temperature data for an entire year for a specific weather station.

## API Endpoints

- `/api/v1/<station>/<date>/`: Fetches temperature for a specific station on a given date.
  - **Parameters**:
    - `station`: The station ID.
    - `date`: The date in `YYYY-MM-DD` format.
  - **Example**: `/api/v1/12345/2024-01-01/`

- `/api/v1/<station>/`: Fetches the records of temperature data for the given station.
  - **Parameters**:
    - `station`: The station ID.
  - **Example**: `/api/v1/12345/`

- `/api/v1/annual/<station>/<year>/`: Fetches temperature data for the entire year for a specific station.
  - **Parameters**:
    - `station`: The station ID.
    - `year`: The year for which data is to be fetched.
  - **Example**: `/api/v1/annual/12345/2023/`

## File Structure

- `main.py`: The main Flask application that contains all the routes.
- `data-small/`: Directory containing weather station data files.
  - `stations.txt`: File containing station IDs and names.
  - `TG_STAIDXXXXXX.txt`: Files containing temperature data for individual stations.
- `templates/`: Directory containing the HTML templates for rendering web pages.
  - `home.html`: HTML file that lists the available weather stations.

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/weather-data-api.git
   cd weather-data-api
2. Install dependencies:
   ```bash
   pip install Flask pandas
   ```
4. Ensure you have your weather data files in the data-small/ directory. The file stations.txt should contain station IDs and names, and individual station files should be named in the format TG_STAIDXXXXXX.txt (where XXXXXX is the station ID).
5. Run the Flask application:
   ```bash
   python3 main.py
   ```
## Technologies Used

- **Flask**: A lightweight web framework used to build the API.
- **Pandas**: Used for reading and processing CSV files containing weather data.
- **HTML**: Basic templating for rendering the list of weather stations.
