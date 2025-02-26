Smart-City: Geographic Information-Based Path Planning and Spatial Analysis

Overview:
This project focuses on utilizing geographic information data for path planning and spatial distribution analysis. The results are visualized through interactive maps to provide insights into the spatial distribution of various locations and optimize travel routes.

Workflow:

Step 1: Data Collection
- Data is collected from OpenStreetMap using the Overpass API.
- Four types of locations are retrieved:
  - library (Libraries)
  - basketball (Basketball courts)
  - shopping_centre (Shopping centers)
  - fitting (Fitness centers)
- The Ripley's K function is computed to measure the spatial distribution of points.

Step 2: Region Division
- The bounding box (BBox) of all data points is calculated and plotted on the map.
- The bounding box is divided into a 30x60 grid (30 rows × 60 columns).

Step 3: Path Planning
- The grid coordinates with the highest K values for each location type are identified as target points.
- The A* algorithm is used to plan the optimal path between these target points.

Step 4: Map Visualization
- The Folium library is used to create interactive maps.
- Points on the path are marked, and lines are drawn to connect them.
- The total distance of the planned route is calculated.

Step 5: Encapsulation as a Callable Function
- The entire workflow is encapsulated in a function called find_path.
- The function takes a list of location types as input and returns:
  - An interactive map displaying the optimized path.
  - The total distance of the planned route.
  - The K-matrix, which represents the spatial distribution analysis.

Key Functions:

1. gather_data_from_api - Fetches data from OpenStreetMap using the Overpass API.
2. ripley_k - Computes the Ripley's K function for spatial distribution analysis.
3. convert_to_numpy - Converts the retrieved data into a NumPy array.
4. compute_k_for_square - Computes K-values for each grid cell.
5. get_color - Maps K-values to colors for visualization on the map.
6. a_star_search - Implements the A* algorithm for path planning.
7. grid_to_latlon & latlon_to_grid - Converts between grid coordinates and latitude/longitude.
8. find_path - The main function that performs path planning, visualization, and K-matrix computation.

Installation & Usage:

Dependencies:
Ensure you have the following Python libraries installed:
pip install numpy folium requests osmapi

Example Usage:

from smart_city import find_path

# Define location types to analyze
location_types = ["library", "basketball", "shopping_centre", "fitting"]

# Run the path planning function
map_result, total_distance, k_matrix = find_path(location_types)

# Display the generated map
map_result.save("map.html")
print(f"Total Distance: {total_distance}")

Output Example:
1. Interactive Map: The function generates a map that visually represents the planned route.
2. Total Distance: The cumulative distance of the optimized route is calculated.
3. K-Matrix: A numerical representation of spatial clustering.

