# Go Nowhere?
Final project for my Geospatial Data Analytics class, analyzing the Tesla Supercharger network

## Abstract
The purpose of this project is to analyze the Tesla Supercharger network and propose potential places to build more superchargers. To this end, I obtained a dataset of locations of all the Tesla Superchargers in the mainland United States, and drew an approximately 200 mile buffer around the points. I then ran a K-means clustering algorithm to find areas in the network where lower conceentrations of superchargers exist. With this, I was able to ascertain that there exists very few deadzones in the network, and lower-density areas are away from major cities.

## Inquiry Questions
* Are there any places in the Continental United States where the nearest Tesla Supercharger is more than 200 miles away?
* Where are there places with the lowest quantities or concentrations of superchargers?

## Background and Rationale
Tesla is the world's leading manufacturer of electric cars, and in 2020 alone the company shipped half a million cars. What puts Tesla over other auto makers getting into the EV market is that Tesla has an expansive network of "Superchargers," capable of adding 200 miles of range with 30 minutes of charging. The purpose of this project was to assess this network in its present state, and identify any potential "dead zones" where either there isn't a Supercharger station within 200 miles, or where a Supercharger would be farther away from the next available one.

## Sources
* Supercharger data was obtained from [supercharge.info](supercharge.info/data)
* US boundary shapefiles were obtained from [TIGER/Line®](https://www.census.gov/cgi-bin/geo/shapefiles/index.php)

## Analysis Steps
1. Acquired data from supercharge.info, and cleaned it to only contain active charger locations.
11. Converted data to useable format, and added to QGIS for comparison against Tesla's own map
11. Drew a 2.8986 degrees longitude (approximately 200 miles) buffer around each of the points to draw a map of superchargers
11. Subtracted said buffer from a map of the United States to locate dead zones
11. Ran a K-means clustering algorithm and a K-nearest neighbor algorithm to ascertain low-density zones
11. Calculated the densities of the ten zones the K-algorithms generated

## Results and Images
The dataset of superchargers
![superchargers on qgis](/media/point_map.png)

Compare to the map on Tesla's own website
![superchargers on tesla](/media/tesla_map.png)

The dataset with 2.896 degrees of buffer. Note how further north, the circles become ellipses. (see Limitations subheader below)
![superchargers with ovals](/media/buffer.png)

Finalized render of the deadzone map. Gray areas are outside of the range.
![full rendered map](/media/final_map.png)

Point map with only the gray areas highlited. All of them are near the Canadian border.
![map with only gray area](/media/outside.png)

Important caveat: There are no Superchargers in Alaska
![sorry alaska](/media/full_outside.png)

Original dataset ran through a K-means cluster. Different colors are different zones.
![k-clusters](/media/k_clusters.png)

Boxes drawn around the K-means clusters with a k-nearest neighbor algorithm
![Put them in boxes](/media/cluster_zones.png)

Visualization of the densities of the zones. Darker colors are less dense. The number is how many superchargers are in the zone.
![Glorious data](/media/cluster_density.png)

## Conclusions
My data reveals that, in its present state, the Tesla Supercharger network spans nerarly the entire continental United States. The only deadzones were a small piece of Montana, a park in Minnesota, and two islands north of Michigan.
Further analysis shows that the areas with the lowest number and density of superchargers are all around the Great Plains and Rocky Mountain areas, where there are less major cities.

## Limitations
* The primary limitation with my research is that the buffer around the Supercharger was calculated in degrees and not miles, which results in the buffers being oval shaped, becoming narrower as the points travel north. This could potentially be fixed if the project were to be redone with a new coordinate system.
* My analysis did not factor in any superchargers in Canada, and perhaps the few deadzones that I found could be reached from there.

## Further Research
* Further analysis of the interstate road network could also be a useful tool to identify possible routes where supercharging is not available.
* With a fixed and circular buffer, further research could be done to locate main roads outside of a smaller buffer zone. A more detailed map of main roads that includes so-called "Secondary" roads could aid this analysis.
