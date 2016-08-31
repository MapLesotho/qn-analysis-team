#Estimated population for urban council
To make this one work out: 
#Scenario:
Lesotho is an African Country, and usually in African Countries, most families comprise of extended families. So using this Scenario we assume that a maximum number of people per household could be 7, while a minimum number of people per household could be 3.
Therefore we will calculate the average out this as follows:

```bash
3+7 = 10
10/2 = 5 
```
An average number of people per household will be 5: 
To get an estimated population of Urban Council, we will multiply our total number of residential buildings by an average number of people per household. 

```bash
5167 * 5 =25,835 people
NB: But to get our residential buildings, we already have an analysis of a count of mapped buildings (5374), We decided to choose those that could make sense when it comes to residing people and in this case we have (yes = 4493, house = 3 and hut = 671) and sum them up.
4493+3+671 =5167.
```
The estimated total population of urban council is 25,835.

#Building Density
A number of buildings per the area of our planning area

```bash
NB: our area was first in Hactares. We first converted hactares into sqkm to come up with this one (5146.045 hectares = 51.46 sqkm)
5374/51.46 =104.43062573 buildings/square kilometers
```

#Planning Issues in urban council
1. Encroachment of residential structures onto the road reserve, agricultural land uses, flood zones, grazing lands due to urban sprawl or of one land use into another.
With the osm data, we will be able to run queries which will assist in decision making towards problem solving should any dispute or land use conflict arise due to any kind of encroachment. For instance, let us take encroachment of buildings inside of farmlands as an example. We will run queries to analyze if this is the case and how it can help become solved. 
We will first run a query of all buildings inside urban council as follows.

```sql
SELECT building, way
FROM urban_council_polygon
WHERE building is not null
```
Then we will run a second query of farmlands as follows
```sql
SELECT landuse, way
FROM urban_council_polygon
WHERE landuse = 'farmland'
```
Then we will create a 10 meters buffer around the farmlands assuming the agricultural standards say they have a 10 meters zone which is a building restricted area

```sql
SELECT landuse, ST_Union (ST_Buffer (way,10))
FROM urban_farmlands
GROUP BY landuse
```
Then we intersect the buildings table with the buffer around the landuse using the ST_Intersect function as follows:

```sql
SELECT ub.building, ub.way, fb.landuse
FROM urban_building as ub, farmland_buffer as fb 
WHERE fb.landuse = 'farmland' AND (ST_Intersects (ub.way, fb.st_union))
```
Then we can view the results in QGIS and have it as a map which can be used to enforce development control standards. 
Or which can be used to assess the severity of the problem if exists. Using this analysis, (We found 71 buildings that are encroaching farmlands in Urban Council). we have uploaded a project from QGIS called encroachment of buildings around farmlands in urban coucil, which displays this as a map.

2. Lack of consultation by stakeholders to the physical planning offices in their planning process
Open street mapping uses the latest update of imagery which was a big problem with Arc GIS, Arc GIS even lacked imagery at some places, so now we can boldly approach different stakeholder departments sharing ideas, information, and encouraging open source movement therefore.
3. Political influences in the enforcement process of planning legislation and legal framework
Lesotho’s national base map is complete, so now we are striving for its quality and we will use these maps for further production of maps, in this case we can produce a master plan. This master plan will serves as our legal document which will help in the enforcement. This could not be done before.
4. Lack of green and public spaces
Qacha Urban council lacks public spaces. Osm data can help us identify available open spaces which we can use to suggest possible locations for provision of green spaces to be done by the ministry of tourism


