## Centering the Edges: Sidewalks and Safety

Curb management will be crucial in the coming years for municipalities. Sidewalks and curbs serve as pedestrian passage, bike lanes, and for on-street parking. In a pandemic environment, they are additionally in constant use as ride-hailing service loading, retail and restaurant curbside pickup, parklets/outdoor dining, car-share space, EV charging, ADA spaces and ramps, food trucks, dockless bike and scooter locales, freight delivery and loading, and an increasing share of home deliveries. 
Yet many cities do not maintain digital inventories of their curbs.

## Introduction
Prior Data Development

In early 2018, the Department of Technology’s SFGIS division started to extend earlier right-of-way (RoW) delineation efforts that leveraged the Department of Public Works (PW) basemap and I was brought on as an intern to begin the process. The initial scope was limited to beginning digitization of a planimetric geospatial line layer in order to develop specifications to place a request for proposal. Instead, myself along with my SFGIS supervisor developed and completed the digitization and attribution effort in house.
Features were transcribed at large scale ( > 1:100 on-screen) by hand with reference to four years' AccuPlus 76mm/3-inch orthoimagery accepted as 95% within 60cm absolute horizontally. I used these lines to build polygons around official Assessor blocks. These were then processed by taking the symmetrical difference of those polygons with the ASR blocks to produce the walkable splits of public right away, or sidewalks. 

1. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/lines.JPG" height='220' width='300' alt="lines" />    >>>>>      2. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/polygons.JPG" height='220' width='300' alt="polygons" />
  
3. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/assessorblocks.JPG"  height='220' width='300' alt="assessor blocks" />  >>>>>>  4. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/sidewalks.JPG" height='220' width='300' alt="sidewalks" />

The initial scope of this current project was to utilize the workflow set out by Meli Harvey in her NYC Sidewalk Widths website and published Python notebook. While I could process certain sections of San Francisco, I was unsuccessful at generating a comprehensive sidewalk dataset with attributed widths.
Instead I used the total area of this sidewalk and began to look at pedestrian related traffic accidents, population by 2020 Census tract and current SFMTA Shared Spaces permits, either on the sidewalk or in the form of parklets in the street.

### Traffic Crashes by Supervisor District
<a href="https://tims.berkeley.edu/tools/gismap/"><img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/timcrashgraph.png"></a>

Data from the Transportation Injury Mapping System (TIMS) 

<img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/pedcrashes_2020censustracts.png">

### Embedding a Carto Map:
<iframe width="100%" height="520" frameborder="0" src="https://ifarah.carto.com/builder/f16bfc2b-9f15-4688-83d3-e31562c7823b/embed" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

## References
Census tract 2020 TIGER boundaries, California filtered for San Francisco. https://www.census.gov/cgi-bin/geo/shapefiles/index.php 

Total Population from 2020 ACS Census, table S0101. https://data.census.gov/cedsci/

Crashes in San Francisco from Transportation Injury Mapping System (TIMS), Safe Transportation Research and Education Center, University of California, Berkeley, 2022.  https://tims.berkeley.edu/tools/gismap/

Supervisor District boundaries, DataSF: (https://data.sfgov.org/Geographic-Locations-and-Boundaries/Supervisor-Districts-2012-/keex-zmn4) <i>updated to reflect Supervisor 1 is Chan and Supervisor 7 is Melgar.</i>
