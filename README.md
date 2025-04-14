# JourneyMapper

This Python script fetches transportation routes (driving, transit, or flight) using the Google Maps API and generates corresponding `.kml` files for viewing in Google Earth or similar tools. It supports curved great-circle paths for flights and straight-line paths for driving or transit routes.

## Features

- Fetch transit or driving routes from Google Maps and convert them to KML format.
- Generate great-circle (curved) flight paths using geographic calculations.
- Automatically sanitize file names for safe KML file output.
- Easy configuration of multiple journeys via a list.

## Requirements

- Python 3.7+
- Google Maps API key with access to:
  - Directions API
  - Geocoding API

### Python Dependencies

Install required packages with:

```bash
pip install -r requirements.txt
```

## Usage
Get a Google Maps API Key
Visit Google Cloud Console to create an API key and enable the necessary APIs.

Configure Journeys
Edit the journeys list in the main() function to specify routes. Examples:

Driving route between cities

Transit route between stations

Flight between airports (uses great-circle path)

Run the Script

Run the Script

```bash
python your_script_name.py
```
The script will:

Fetch route or geocode coordinates

Create a .kml file for each journey in the current directory

Print coordinate data and confirmation messages

Example Journey Configurations
```python
journeys = [
    {
        "type": "train",
        "origin": "Croydon Station",
        "destination": "Herne Hill Station"
    },
    {
        "type": "drive",
        "origin": "Basel Switzerland",
        "destination": "Interlaken Switzerland"
    },
    {
        "type": "flight",
        "origin": "Newark international airport",
        "destination": "West palm beach airport",
        "name": "PBI to EWP"
    }
]
```

##Output
The script creates .kml files with the following features:

Transit/Driving Routes: Based on decoded Google Maps polylines

Flight Paths: Smooth curved lines using the WGS84 great-circle route

Each file will be named based on the sanitized origin and destination names, e.g.:

croydon_station_to_herne_hill_station.kml

pbi_to_ewp_flight.kml

##Notes
Walking steps are ignored in transit routes for better map clarity.

Coordinates are printed during geocoding to aid debugging or visualization.
