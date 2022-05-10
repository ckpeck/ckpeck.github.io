## Centering the Edges: Sidewalks and Safety

Curb management will be crucial in the coming years for municipalities. Sidewalks and curbs serve as pedestrian passage, bike lanes, and for on-street parking. In a pandemic environment, they are additionally in constant use as ride-hailing service loading, retail and restaurant curbside pickup, parklets/outdoor dining, car-share space, EV charging, ADA spaces and ramps, food trucks, dockless bike and scooter locales, freight delivery and loading, and an increasing share of home deliveries. 
Yet many cities do not maintain digital inventories of their curbs.

## Introduction
Prior Data Development

In early 2018, the Department of Technology’s SFGIS division started to extend earlier right-of-way (RoW) delineation efforts that leveraged the Department of Public Works (PW) basemap and I was brought on as an intern to begin the process. The initial scope was limited to beginning digitization of a planimetric geospatial line layer in order to develop specifications to place a request for proposal. Instead, myself along with my SFGIS supervisor developed and completed the digitization and attribution effort in house.
Features were transcribed at large scale ( > 1:100 on-screen) by hand with reference to four years' AccuPlus 76mm/3-inch orthoimagery accepted as 95% within 60cm absolute horizontally. I used these lines to build polygons around official Assessor blocks. These were then processed by taking the symmetrical difference of those polygons with the ASR blocks to produce the walkable splits of public right away, or sidewalks. 

1. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/lines.JPG" height='220' width='300' alt="lines" />    >>>>>      2. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/polygons.JPG" height='220' width='300' alt="polygons" />
  
3. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/assessorblocks.JPG"  height='220' width='300' alt="assessor blocks" />  >>>>>>  4. <img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/sidewalks.JPG" height='220' width='300' alt="sidewalks" />

The initial scope of this current project was to utilize the workflow set out by Meli Harvey in her <a href="https://www.sidewalkwidths.nyc/#16.13/40.722933/-73.956565"> NYC Sidewalk Widths</a> website and <a href="https://github.com/meliharvey/sidewalkwidths-nyc">published Python notebook</a>. While I could process certain sections of San Francisco, I was unsuccessful at generating a comprehensive sidewalk dataset with attributed widths.
Instead I used the total area of this sidewalk and began to look at pedestrian related traffic accidents, population by 2020 Census tract and current SFMTA Shared Spaces permits, either on the sidewalk or in the form of parklets in the street.

### Traffic Crashes by Supervisor District

I intiially used Census tract spatial data and 2020 ACS Census population data, joining the traffic injury data to analyze at a more granular level. For the TIMs data, incidents that occurred on the interstate or freeways were filtered out, as the primary research is concerned with on the ground infrastructure and safety. At a Census tract scale, the occurence of incidents at the street level are concentrated in the downtown but more particularly in the Tenderloin neighborhood.

<img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/supdistr.JPG">

<img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/pedcrashes_2020censustracts.png">

Zooming out to the Supervisor District level, this remained true with District 6 leading in crashes with District 3 which includes North Beach and Nob Hill and District 9 which includes the Mission and Bernal Heights close behind.

<img src "https://github.com/ckpeck/ckpeck.github.io/blob/main/crashesbysupdist.png">

Looking at strictly tabular data, the crash and pedestrian involved crash rates are starkly highest in District 6, even when normalizing for population.

<a href="https://tims.berkeley.edu/tools/gismap/"><img src="https://github.com/ckpeck/ckpeck.github.io/blob/main/timcrashgraph.png"></a>
<img src = "https://github.com/ckpeck/ckpeck.github.io/blob/main/timspedratecrashgraph.png">
<br><small>Data from the Transportation Injury Mapping System (TIMS) </small></br>

Making sure we are not simply evaluation a population map, I explored the levels of population density which is not the highest in District 6 (<small><i>Open space such as Golden Gate Park, McLaren Park, and Lake Merced were not removed from the total area of the supervisor districts</i></small>)

<img src = "https://github.com/ckpeck/ckpeck.github.io/blob/main/populationdensity.png">

I proceeded, attributing the sidewalk polygons through a spatial join with the supervisor districts and summing the total area then joining back to the initial Supervisor District polygons. Here, I normalized by the total population in the district, achieving a ratio of sidewalk area to total residential population. Despite the fact that this area of downtown and SOMA additionally swell during the daytime to accomodate workforce commuters, the ratio of sidewalks to population was lowest here.

<img src = "https://github.com/ckpeck/ckpeck.github.io/blob/main/rateofsidewalkareabypop.png">

## Shared Spaces

## References
Census tract 2020 TIGER boundaries, California filtered for San Francisco. https://www.census.gov/cgi-bin/geo/shapefiles/index.php 

Total Population from 2020 ACS Census, table S0101. https://data.census.gov/cedsci/

Crashes in San Francisco from Transportation Injury Mapping System (TIMS), Safe Transportation Research and Education Center, University of California, Berkeley, 2022.  https://tims.berkeley.edu/tools/gismap/

Supervisor District boundaries, DataSF: (https://data.sfgov.org/Geographic-Locations-and-Boundaries/Supervisor-Districts-2012-/keex-zmn4) <i>updated to reflect Supervisor 1 is Chan and Supervisor 7 is Melgar.</i>
