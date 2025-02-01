# Capstone Project: The Best Neighborhood for Families in Madrid
**Applied Data Science Capstone by IBM**

## Table of Contents
1. [Business Problem](#business-problem)  
2. [Data](#data)  
3. [Methodology and Analysis](#methodology-and-analysis)  
4. [Results and Discussion](#results-and-discussion)  
5. [Conclusion](#conclusion)  
6. [Project Structure](#project-structure)  
7. [How to Run](#how-to-run)  
8. [References](#references)

---

## Business Problem
In this project, we aim to determine the best neighborhood in Madrid for outdoor family life. Specifically, we focus on the following criteria:

1. The district that has the **largest total green areas (in m²)**, visualized via a *choropleth map*.  
2. Neighborhoods within those districts that feature the **most playgrounds** and other family-friendly outdoor venues.  

Additionally, we create a heatmap of **venues** (using the Foursquare API) for any specified venue category (e.g., dog runs, playgrounds, sports facilities). By overlaying these points on the map of districts with green areas, we highlight districts that both have extensive green space and relevant venues.

---

## Data
This analysis uses two main data sources:

1. **Madrid Green Areas Data**  
   - Obtained from the official [Ayuntamiento de Madrid Open Data platform](https://datos.madrid.es/portal/site/egob).
   - Includes district names and total green area size (in m²).  
   - Data is converted into a DataFrame, filtered, and sorted to create a bar chart (district vs. green area).

2. **Foursquare Venue Data**  
   - Sourced via the [Foursquare API](https://foursquare.com/developers/).  
   - Used to locate relevant venues (playgrounds, dog runs, etc.) in Madrid’s neighborhoods.
   - Results are transformed into a DataFrame with latitude, longitude, venue name, and category, which are then used to create a heatmap.

**Geospatial Data**  
- A JSON file containing the **district boundaries** (or “frontiers”) of Madrid is used to create a choropleth map.  
- The keys and nested structure of this file must be explored to link district names in the JSON to the district names in our green area DataFrame.

---

## Methodology and Analysis
1. **Comparing Districts by Green Areas**  
   - Load, clean, and sort green area data from the Madrid open data source.  
   - Visualize as a **bar chart** to identify the districts with the largest green spaces.

2. **Creating a Choropleth Map**  
   - Import the GeoJSON file with district boundaries.  
   - Merge the green area DataFrame with the GeoJSON data.  
   - Render a **choropleth** using [Folium](https://github.com/python-visualization/folium), shading each district based on its green area in m².

3. **Extracting Venue Data via Foursquare**  
   - Use the Foursquare API with an access token or client credentials.  
   - Search for venues in specified categories (e.g., “Playground,” “Dog Run”).  
   - Store the results (name, coordinates, category) in a DataFrame.

4. **Creating a Venue Heatmap**  
   - Transform the venue coordinates into a Folium **HeatMap** overlay.  
   - Visualize how the intensity of the chosen venue category distributes across Madrid’s districts.  
   - Compare these clusters with the **choropleth** (green areas) map to make final recommendations.

---

## Results and Discussion
- **Green Areas**: The bar chart and choropleth map reveal which districts have the highest m² of green space.  
- **Venue Heatmap**: The heatmap indicates hotspots for the chosen venue category (e.g., playgrounds).  
- **Combined Insights**: By overlaying the venue heatmap on the choropleth map, we identify districts that are both green and highly equipped with family-friendly venues—ideal for families seeking outdoor activities.

---

## Conclusion
- The chosen district(s) with ample green space often show a concentration of **outdoor family facilities** (e.g., playgrounds, parks).  
- Users can **repeat the analysis with different Foursquare venue categories**, making the methodology adaptable for various use cases (dog runs, sports facilities, etc.).  
- This approach helps new residents, urban planners, or policymakers quickly visualize which parts of Madrid are best suited for family-friendly, outdoors-oriented lifestyles.

---

## References
1. **Open Data Madrid**  
   - Ayuntamiento de Madrid Official Open Data Portal:  
     [https://datos.madrid.es/portal/site/egob](https://datos.madrid.es/portal/site/egob)
2. **Foursquare Developer Documentation**  
   - [https://foursquare.com/developers/](https://foursquare.com/developers/)
3. **Folium Library**  
   - GitHub: [https://github.com/python-visualization/folium](https://github.com/python-visualization/folium)
4. **IBM Applied Data Science Capstone**  
   - [https://www.coursera.org/learn/applied-data-science-capstone](https://www.coursera.org/learn/applied-data-science-capstone)

---
