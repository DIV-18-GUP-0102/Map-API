# Flask Map API

I here aims to create an Flask application that will provide API endpoints for various functionalities related to maps and coordinates. For now this application, when provided with coordinates of some places, will make a polygon out of those vertices.

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/MapAPI.git
    ```

2. Navigate to the project directory:

    ```bash
    cd MapAPI
    ```

3. Install the required Python packages:

    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. Run the Flask application:

    ```bash
    python main.py
    ```

2. Access the API endpoint:

    - Endpoint URL: `http://127.0.0.1:5000/create_polygon`
    - Method: POST
    - Request body: JSON object with a key "vertices" containing an array of coordinates

    Example request:

    ```json
    {
        "vertices": [
            [83.122948, 25.280619], 
            [83.002227, 25.322902], 
            [83.026354, 25.377376], 
            [83.088453, 25.383185]
        ]
        
    }

    ```
    The data points should be send as [longitude, latitude], otherwise the location mapped will be haywire.


3. The API will return a JSON response with the following keys:

    - `message`: A status message indicating whether the polygon was created successfully.
    - `polygon`: GeoJSON representation of the created polygon.
    - `map_html`: HTML code for embedding a Folium map visualization of the polygon.
    
    The output will look like: 
    ```powershel
    Polygon created successfully
    Polygon GeoJSON:
    "{\"type\": \"FeatureCollection\", \"features\": [{\"id\": \"0\", \"type\": \"Feature\", \"properties\": {}, \"geometry\": {\"type\": \"Polygon\", \"coordinates\": [[[83.122948, 25.280619], [83.002227, 25.322902], [83.026354, 25.377376], [83.088453, 25.383185], [83.122948, 25.280619]]]}, \"bbox\": [83.002227, 25.280619, 83.122948, 25.383185]}], \"bbox\": [83.002227, 25.280619, 83.122948, 25.383185]}"
    ```
    And If you want you can save and open the rendered map HTML in a web browser like:
    ``` python
    with open('map.html', 'w') as f:
         f.write(response_data['map_html'])
    import webbrowser
    webbrowser.open('map.html')
    ```

## Dependencies

- Flask
- Flask-CORS
- folium
- geopandas
- shapely
- geopy

## Credits

This application was created by Divyansh Gupta.

---
