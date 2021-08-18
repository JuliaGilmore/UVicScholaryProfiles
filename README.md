Project by Julia Gilmore, Metadata Practicum Student, University of Victoria (UVic) Libraries 

Completed Summer 2021

_Note: The creation of this page was inspired by a similar [Wikidata visualization page](https://yooylee.github.io/experiment-wikidata-canadian-archive-women-in-stem/) from the University of Ottawa's [Canadian Archive of Women in STEM](https://biblio.uottawa.ca/en/women-in-stem/about) project, and [SCUA Wikidata Experimentation](https://elizabethbassett.github.io/uvic-scua-wikidata-experimentation/), a visualization project connecting archival holdings at University of Victoria Special Collections and University Archives (SCUA) in Wikidata, completed by Elizabeth Bassett in July 2020._ 
<br>

## Visualizing the University of Victoria (UVic) through Wikidata Queries  

This project was designed for an Information Professional Practicum (IPP) as part of the Master of Information (MI) degree program at the Faculty of Information (University of Toronto). The goal of the project was to support the creation of scholarly profiles and enhance the presence and discoverability of the University of Victoria in Wikidata. It is hoped that the project findings will demonstrate the potential applications of linked data for academic institutions and support future Wikidata initiatives at the University of Victoria.  

The practicum was completed in three stages over the course of July - August 2021, under the direction and supervision of Dean Seaman, Head of Metadata, University of Victoria Libraries. 

Stage 1 - Population of UVic Faculties, Departments, Schools in Wikidata <br>

Stage 2 - Population of UVic Campus Buildings and Building Namesakes <br>

Stage 3 - Querying & Visualization of the completed Wikidata items <br>

_The Wikimedia Foundation has developed an excellent tutorial for writing SPARQL queries, which was an invaluable resource for Stage 3 of the project. The tutorial can be accessed [here]( https://www.youtube.com/watch?v=kJph4q0Im98&ab_channel=WikimediaFoundation)._
<br>

### Faculties and Academic Departments 
----  
#### _**Where are the headquarters for the UVic Faculties and Academic Departments located?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AMap%0A%0ASELECT%20%3Findividual_entity%20%3Findividual_entityLabel%20%3Fcoordinate_location%20%3Foccupant%20%3FoccupantLabel%20WHERE%20%7B%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%20%3Findividual_entity%20wdt%3AP31%20wd%3AQ19844914.%0A%20%20%3Findividual_entity%20wdt%3AP466%20%3Foccupant.%0A%20%20%3Findividual_entity%20wdt%3AP127%20wd%3AQ1458113.%0A%20%20MINUS%20%7B%3Findividual_entity%20wdt%3AP131%20wd%3AQ2000769.%7D%0A%20%20MINUS%20%7B%3Foccupant%20wdt%3AP466%20wd%3AQ16959841.%7D%0A%20%20%0A%20%20OPTIONAL%20%7B%20%3Findividual_entity%20wdt%3AP625%20%3Fcoordinate_location.%20%7D%0A%20%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>
<br>
To create this map visualization, campus buildings were used as the starting point (as they have defined coordinates, while the faculties and departments do not). During the Wikidata population stage of this project, faculties and departments were connected to campus buildings using P466 (occupant). Using this property as a query condition allows faculties and departments to appear in the SPARQL results and be matched to the appropriate buildings. Any other organizations (e.g. Ocean Networks Canada) listed as occupants were omitted from the search using the MINUS function.  
<br>

__SPARQL query used to generate the table:_
_
```
SELECT ?building ?buildingLabel ?coordinate_location ?occupant ?occupantLabel WHERE {
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
  ?building wdt:P31 wd:Q19844914.
  ?building wdt:P466 ?occupant.
  ?building wdt:P127 wd:Q1458113.
  ?building wdt:P625 ?coordinate_location.
  MINUS {?building wdt:P131 wd:Q2000769.}
  MINUS {?occupant wdt:P466 wd:Q16959841.}
}
```
<br>
#### _**What can I study at the University of Victoria?**_

<iframe style="width: 60vw; height: 110vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%0A%23%20What%20can%20I%20study%20at%20UVic%3F%20%0A%23%20instance%20of%20academic%20department%0A%23%20located%20in%20Victoria%0A%23%20has%20field%20of%20work%0A%0ASELECT%20DISTINCT%20%3FstudiesLabel%20%28COUNT%20%28%3Ffaculty%29%20as%20%3FCount%29%0AWHERE%0A%7B%0A%20%20%3Ffaculty%20wdt%3AP31%20wd%3AQ180958.%20%23faculty%0A%20%20%3Ffaculty%20wdt%3AP361%20wd%3AQ1458113.%20%23%20part%20of%20University%20of%20Victoria%0A%20%20%3Ffaculty%20wdt%3AP101%20%3Fstudies%20.%20%23%20field%20of%20work%0A%20%20%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22%20.%20%7D%0A%7D%20%0A%0AGROUP%20BY%20%28%3FstudiesLabel%29%20%0AORDER%20BY%20DESC%20%28%3FCount%29" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

----

This bubble chart visualization collects subject areas listed under P101 (field of work) for all UVic Faculties. 

Note: A separate query was performed for UVic Academic Departments and can be viewed as a [Table](https://w.wiki/3pUN) or [Bubble Chart](https://w.wiki/3qGh).
<br>

__SPARQL query used to generate the table:__

```
SELECT DISTINCT ?studiesLabel (COUNT (?faculty) as ?Count)
WHERE
{
  ?faculty wdt:P31 wd:Q180958. #faculty
  ?faculty wdt:P361 wd:Q1458113. # part of University of Victoria
  ?faculty wdt:P101 ?studies . # field of work
  
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en" . }
} 

GROUP BY (?studiesLabel) 
ORDER BY DESC (?Count)
```
<br>
#### _**Can you tell me more about the different UVic Faculties?**_

<iframe style="width: 60vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AGraph%0ASELECT%20%3Fitem%20%3FitemLabel%20%3FlocationLabel%20%3FdepartmentLabel%0AWHERE%20%0A%7B%0A%20%20%23%20Item%20Property%20Value%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ180958.%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20faculty.%0A%20%20%3Fitem%20wdt%3AP361%20wd%3AQ1458113.%20%23%20and%20are%20part%20of%20the%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP276%20%3Flocation.%0A%20%20%3Fitem%20wdt%3AP527%20%3Fdepartment.%0A%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%0A%0A%7D%0A%0A%0A%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>
<br>
_SPARQL query used to generate the table:_
```
SELECT ?faculty ?facultyLabel ?locationLabel ?departmentLabel
WHERE 
{
  # Item Property Value
  ?faculty wdt:P31 wd:Q180958. # all the items that have instance of value faculty.
  ?faculty wdt:P361 wd:Q1458113. # and are part of the University of Victoria
  ?faculty wdt:P276 ?location.
  ?faculty wdt:P527 ?department.

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```
<br>
#### _**What is the social media presence for the various Faculties and Departments?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ATable%0A%23Social%20Media%20Presence%20of%20UVic%20Academic%20Departments%0ASELECT%20%3Fitem%20%3FitemLabel%20%3FTwitter_usernameLabel%20%3FFacebook_IDLabel%20%3FInstagram_usernameLabel%20%0AWHERE%20%0A%7B%0A%20%20%23%20Item%20Property%20Value%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%20%23%20and%20are%20located%20in%20Victoria%0A%20%7B%20%3Fitem%20wdt%3AP31%20wd%3AQ2467461.%20%7D%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20academic%20department.%0A%20%20UNION%0A%20%20%7B%3Fitem%20wdt%3AP31%20wd%3AQ180958.%20%7D%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20faculty%0A%20%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP2002%20%3FTwitter_username.%20%7D%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP2013%20%3FFacebook_ID.%20%7D%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP2003%20%3FInstagram_username.%20%7D%0A%20%0A%7D%0AORDER%20BY%20DESC%20(%3FTwitter_usernameLabel)%20(%3FFacebook_IDLabel)%0A%0A%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT ?item ?itemLabel ?Twitter_usernameLabel ?Facebook_IDLabel ?Instagram_usernameLabel 
WHERE 
{
 { ?item wdt:P31 wd:Q2467461. } # all the items that have instance of value academic department.
  UNION
  {?item wdt:P31 wd:Q180958. } # all the items that have instance of value faculty
   ?item wdt:P131 wd:Q2132. # and are located in Victoria
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }

OPTIONAL { ?item wdt:P2002 ?Twitter_username. }
OPTIONAL { ?item wdt:P2013 ?Facebook_ID. }
OPTIONAL { ?item wdt:P2003 ?Instagram_username. } 
}
ORDER BY DESC (?Twitter_usernameLabel) (?Facebook_IDLabel)
```
<br>
#### _**Which Faculty or Department has the most Twitter followers?**_

<iframe style="width: 50vw; height: 60vh; border: none;" src="https://query.wikidata.org/embed.html#SELECT%20%3Fitem%20%3FitemLabel%20%3FTwitter_followers%0AWHERE%0A%7B%0A%20%20%20%20%7B%20%3Fitem%20wdt%3AP31%20wd%3AQ2467461.%7D%20%23%20instance%20of%20academic%20department%20%0A%20%20%20%20%20UNION%0A%20%20%20%20%20%7B%3Fitem%20wdt%3AP31%20wd%3AQ180958.%7D%20%23%20instance%20of%20faculty%20%0A%20%20%20%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132%20.%20%23%20located%20in%20Victoria%0A%20%20OPTIONAL%20%20%20%7B%20%3Fitem%20p%3AP2002%20%3FTwitter_username.%0A%20%20%20%20%3FTwitter_username%20pq%3AP3744%20%3FTwitter_followers.%20%7D%0A%0A%20%20OPTIONAL%20%7B%3Fitem%20wdt%3AP2013%20%3FFacebook_ID.%7D%0A%20OPTIONAL%20%7B%3Fitem%20wdt%3AP2003%20%3FInstagram_ID.%7D%0A%0A%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AORDER%20BY%20DESC%20(%3FTwitter_followers)" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT ?item ?itemLabel ?Twitter_followers
WHERE
{
    { ?item wdt:P31 wd:Q2467461.} # instance of academic department 
     UNION
     {?item wdt:P31 wd:Q180958.} # instance of faculty 
     ?item wdt:P131 wd:Q2132 . # located in Victoria
  OPTIONAL   { ?item p:P2002 ?Twitter_username.
    ?Twitter_username pq:P3744 ?Twitter_followers. }

  OPTIONAL {?item wdt:P2013 ?Facebook_ID.}
  OPTIONAL {?item wdt:P2003 ?Instagram_ID.}
    
     SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}
ORDER BY DESC (?Twitter_followers)
```
<br>

### Exploring the UVic Campus 

<br>
#### _**When were the UVic Campus Buildings built?**_

<iframe style="width: 65vw; height: 60vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ATimeline%0ASELECT%20%3Fitem%20%3Flaunchdate%20(SAMPLE(%3Fimage)%20AS%20%3Fimage)%20%3FitemLabel%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914%3B%0A%20%20%20%20wdt%3AP571%20%3Flaunchdate.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage.%20%7D%0A%20%20%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%0A%20%20%3Fitem%20wdt%3AP127%20wd%3AQ1458113.%0A%7D%0AGROUP%20BY%20%3Fitem%20%3FitemLabel%20%3Flaunchdate" ></iframe>

<br>
This timeline depicts all campus buildings where dates of inception are known. Note that the timeline visualization for SPARQL queries defaults to January 1, XXXX for items where inception is provided with precision of a year. More detailed start dates are available for buildings dedicated to namesakes (see below). 

Sources: 

[University of Victoria: Maps & buildings](https://www.uvic.ca/search/maps-buildings/index.php/)

UVic Campus component of University of Victoria Art Collections (UVAC) 2011 exhibit: [The Emergence of Architectual Modernism in Victoria](https://uvac.uvic.ca/Architecture_Exhibits/UVic_campus/)
<br>

_SPARQL query used to generate the table:_
```
SELECT ?item ?inception (SAMPLE(?image) AS ?image) ?itemLabel WHERE {
  ?item wdt:P31 wd:Q19844914;
    wdt:P571 ?inception.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
  OPTIONAL { ?item wdt:P18 ?image. }
  
  ?item wdt:P131 wd:Q2132.
  ?item wdt:P127 wd:Q1458113.
}
GROUP BY ?item ?itemLabel ?inception
```
<br>
#### _**What does the UVic campus look like?**_

<iframe style="width: 60vw; height: 60vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AImageGrid%0ASELECT%20%3Fitem%20%3FitemLabel%20%3Fimage%20%3Fcoordinate%0AWHERE%0A%7B%0A%20%20%20%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23%20instance%20of%20university%20building%20%0A%20%20%20%20%20%3Fitem%20wdt%3AP127%20wd%3AQ1458113%20.%20%23%20owned%20by%20University%20of%20Victoria%0A%20%20%20%20%20%3Fitem%20wdt%3AP625%20%3Fcoordinate.%0A%20%20%20%20%20%3Fitem%20wdt%3AP18%20%3Fimage.%0A%0A%20%20%20%20%0A%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AORDER%20BY%20ASC%20(%3FitemLabel)" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>
----
<br>
Images of the  University of Victoria Campus are also available in Wikimedia Commons under the category: [University of Victoria campus](https://commons.wikimedia.org/wiki/Category:University_of_Victoria_campus).

<br>
_SPARQL query used to generate the table:_
```
SELECT ?building ?buildingLabel ?image ?coordinate
WHERE
{
     ?building wdt:P31 wd:Q19844914. # instance of university building 
     ?building wdt:P127 wd:Q1458113 . # owned by University of Victoria
     ?building wdt:P625 ?coordinate.
     ?building wdt:P18 ?image.

     SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}
ORDER BY ASC (?buildingLabel)
```
<br>

#### _**Which Campus Buildings are LEED Certified and where are they located?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AMap%0A%23LEED%20Certified%20Buildings%20on%20UVic%20Campus%0ASELECT%20%3Fitem%20%3FitemLabel%20%3Fcoordinate_location%20%3Fcoordinate_locationLabel%20%0AWHERE%20%0A%7B%0A%20%20%23%20Item%20Property%20Value%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20university%20building.%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%20%23%20and%20are%20located%20in%20Victoria%0A%20%20%3Fitem%20wdt%3AP1552%20wd%3AQ1521623.%20%23%20and%20have%20the%20quality%20'Leadership%20in%20Energy%20and%20Environmental%20Design%20%20%20%20%20%20%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP625%20%3Fcoordinate_location.%20%7D%0A%20%0A%7D%0A%0AORDER%20BY%20(%3Farea)%0A%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>
<br>
The property P1552 (has quality) was selected to indicate LEED certification after performing sample queries to see how this statement appeared most often across Wikidata. 

Source: 

[University of Victoria: Campus Planning and Sustainability](https://www.uvic.ca/sustainability/topics/buildings-grounds/index.php)

<br>
_SPARQL query used to generate the table:_
```
SELECT ?item ?itemLabel ?coordinate_location ?coordinate_locationLabel 
WHERE 
{
  # Item Property Value
  ?item wdt:P31 wd:Q19844914. # all the items that have instance of value university building.
  ?item wdt:P131 wd:Q2132. # and are located in Victoria
  ?item wdt:P1552 wd:Q1521623. # and have the quality 'Leadership in Energy and Environmental Design      
  
SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }

OPTIONAL { ?item wdt:P625 ?coordinate_location. }
}
```
<br>
#### _**What are some of the distinguishing features of the various Campus Buildings?**_

<iframe style="width: 60vw; height: 90vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%0A%23UVic%20Campus%20Buildings%20with%20features%20%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20building%20'has%20part'%0ASELECT%20DISTINCT%20%3FhaspartLabel%20(COUNT%20(%3Fitem)%20as%20%3FCount)%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP527%20%3Fhaspart%20.%20%23%20who%20has%20a%20part%20(e.g.%20laboratory%2C%20green%20roof%2C%20theatre)%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20(%3FhaspartLabel)%0AORDER%20BY%20DESC%20(%3FCount)%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT DISTINCT ?haspartLabel (COUNT (?item) as ?Count)
WHERE {
  ?item wdt:P31 wd:Q19844914. #university building
  ?item  wdt:P127 wd:Q1458113. # owned by - University of Victoria
  ?item wdt:P527 ?haspart . # who has a part (e.g. laboratory, green roof, theatre)

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
GROUP BY (?haspartLabel)
ORDER BY DESC (?Count)
```
<br>
See below (Looking Ahead) for additional suggestions for enhancing this query. 

#### _**How has the UVic campus grown over time?**_

<iframe style="width: 55vw; height: 60vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AMap%0ASELECT%20%3Fitem%20%3FitemLabel%20((xsd%3Ainteger(YEAR(%3Finceptiondate%20)%2F%201))%20*%201%20AS%20%3Finception_year)%20((xsd%3Ainteger(YEAR(%3Finceptiondate%20)%2F%2010))%20*%2010%20AS%20%3Finception_decade)%20(SAMPLE(%3Fimage)%20AS%20%3Fimage)%20%3Fcoordinate%20(%3Finception_decade%20AS%20%3Flayer)%20%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914%3B%0A%20%20%20%20wdt%3AP571%20%3Finceptiondate.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage.%20%7D%0A%20%20%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%0A%20%20%3Fitem%20wdt%3AP127%20wd%3AQ1458113.%0A%20%20%3Fitem%20wdt%3AP625%20%3Fcoordinate.%0A%7D%0AGROUP%20BY%20%3Finceptiondate%20%3Fitem%20%3FitemLabel%20%3Fcoordinate%0AORDER%20BY%20ASC%20(%3Finceptiondate)" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT ?item ?itemLabel ((xsd:integer(YEAR(?inceptiondate )/ 1)) * 1 AS ?inception_year) ((xsd:integer(YEAR(?inceptiondate )/ 10)) * 10 AS ?inception_decade) (SAMPLE(?image) AS ?image) ?coordinate (?inception_decade AS ?layer)  WHERE {
  ?item wdt:P31 wd:Q19844914;
    wdt:P571 ?inceptiondate.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
  OPTIONAL { ?item wdt:P18 ?image. }
  
  ?item wdt:P131 wd:Q2132.
  ?item wdt:P127 wd:Q1458113.
  ?item wdt:P625 ?coordinate.
}
GROUP BY ?inceptiondate ?item ?itemLabel ?coordinate
ORDER BY ASC (?inceptiondate)
```
<br>
This query incorporates multiple layers to represent different decades for construction of the UVic campus (1940-2010). The resulting colour-coded map indicates that the most significant period of campus growth occurred during the 1960s, followed by the 2000s. Campus development was also more centralized around Ring Road during the 1960s. Building additions and extensions are not represented in this query. 
<br>
### What's In A Namesake?
<br> 
#### _**Which Campus Buildings are or were formerly named after people?**_

<iframe style="width: 65vw; height: 80vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ATimeline%0APREFIX%20xsd%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0ASELECT%20%20%3Fnamesake%20%3FnamesakeLabel%20%3Fdedication_start%20%3Fdedication_end%20%3Fimage%20((xsd%3Ainteger(YEAR(%3Finception%20)%2F%201))%20*%201%20AS%20%3Finception_year)%20%3Fbuilding%20%3FbuildingLabel%20WHERE%0A%0A%7B%0A%3Fbuilding%20wdt%3AP31%20wd%3AQ19844914%20.%0A%3Fbuilding%20wdt%3AP127%20wd%3AQ1458113.%0A%3Fbuilding%20wdt%3AP138%20%3Fnamesake.%0A%3Fbuilding%20wdt%3AP571%20%3Finception.%20%20%0A%3Fbuilding%20p%3AP138%20%3Fstatement%20.%20%0A%20%20%3Fstatement%20ps%3AP138%20%3Fnamesake.%0A%20%20OPTIONAL%7B%3Fstatement%20pq%3AP580%20%3Fdedication_start.%7D%0A%20%20OPTIONAL%7B%3Fstatement%20pq%3AP582%20%3Fdedication_end.%7D%0A%20%20OPTIONAL%7B%3Fbuilding%20wdt%3AP18%20%3Fimage.%7D%0A%0ASERVICE%20wikibase%3Alabel%20%7Bbd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AORDER%20BY%20%3Finception%20%3Fdedication_start%20%3Fdedication_end" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>
_SPARQL query used to generate the table:_
```
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
SELECT  ?namesake ?namesakeLabel ?dedication_start ?dedication_end ?image ((xsd:integer(YEAR(?inception )/ 1)) * 1 AS ?inception_year) ?building ?buildingLabel WHERE

{
?building wdt:P31 wd:Q19844914 .
?building wdt:P127 wd:Q1458113.
?building wdt:P138 ?namesake.
?building wdt:P571 ?inception.  
?building p:P138 ?statement . 
  ?statement ps:P138 ?namesake.
  OPTIONAL{?statement pq:P580 ?dedication_start.}
  OPTIONAL{?statement pq:P582 ?dedication_end.}
  OPTIONAL{?building wdt:P18 ?image.}

SERVICE wikibase:label {bd:serviceParam wikibase:language "en". }
}
ORDER BY ?inception ?dedication_start ?dedication_end
```
<br>
----
This timeline visualization depicts former and current namesakes for various campus buildings and the complete calendar start and end dates for these dedications. Buildings without namesakes are not represented in this query. Only dedication start dates are listed for current building namesakes. The separate year (without month or day) refers to when the building was opened (P571: inception). 

#### _**Which Campus Buildings are named after women?**_

<iframe style="width: 55vw; height: 40vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ATree%0A%23UVic%20Campus%20Buildings%20with%20female%20namesakes%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%0ASELECT%20DISTINCT%20%3Fitem%20%3FitemLabel%20%3Fnamesake%20%3FnamesakeLabel%20%3Fimage%20%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20'a'%20namesake%0A%20%20%3Fnamesake%20wdt%3AP21%20wd%3AQ6581072.%20%23%20female%0A%20%20%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage.%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT DISTINCT ?item ?itemLabel ?namesake ?namesakeLabel ?image 
WHERE {
  ?item wdt:P31 wd:Q19844914. #university building
  ?item  wdt:P127 wd:Q1458113. # owned by - University of Victoria
  ?item wdt:P138 ?namesake . # who have 'a' namesake
  ?namesake wdt:P21 wd:Q6581072. # female
  
  OPTIONAL { ?item wdt:P18 ?image. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```
<br>

#### _**What occupations and roles have the Campus Building namesakes held?**_

<iframe style="width: 60vw; height: 85vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%0A%23UVic%20Campus%20Buildings%20with%20namesakes%20and%20their%20listed%20occupations%20%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%23%20namesakes%20with%20listed%20occupations%0ASELECT%20DISTINCT%20%3FoccupationLabel%20(COUNT%20(%3Fnamesake)%20as%20%3FCount)%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20'a'%20namesake%0A%20%20%3Fnamesake%20wdt%3AP106%20%3Foccupation%20.%20%23%20namesake%20with%20an%20occupation%0AMINUS%20%7B%3Fitem%20wdt%3AP3032%20wd%3AQ107578887.%7D%20%23%20adjacent%20building%20-%20Saunders%20Annex%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20(%3FoccupationLabel)%0AORDER%20BY%20DESC%20(%3FCount)%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT DISTINCT ?occupationLabel (COUNT (?namesake) as ?Count)
WHERE {
  ?item wdt:P31 wd:Q19844914. #university building
  ?item  wdt:P127 wd:Q1458113. # owned by - University of Victoria
  ?item wdt:P138 ?namesake . # who have 'a' namesake
  ?namesake wdt:P106 ?occupation . # namesake with an occupation
MINUS {?item wdt:P3032 wd:Q107578887.} # adjacent building - Saunders Annex
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
GROUP BY (?occupationLabel)
ORDER BY DESC (?Count)
```
<br>
### _**What fields have the Campus Building namesakes contributed to?**_

<iframe style="width: 60vw; height: 85vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%0A%23UVic%20Campus%20Buildings%20with%20namesakes%20and%20their%20listed%20fields%20of%20work%20%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%23%20namesakes%20with%20listed%20fields%20of%20work%0ASELECT%20DISTINCT%20%3FfieldofworkLabel%20(COUNT%20(%3Fnamesake)%20as%20%3FCount)%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20'a'%20namesake%0A%20%20%3Fnamesake%20wdt%3AP101%20%3Ffieldofwork%20.%20%23%20namesake%20with%20an%20occupation%0A%20%20MINUS%20%7B%3Fitem%20wdt%3AP3032%20wd%3AQ107578887.%7D%20%23%20adjacent%20building%20-%20Saunders%20Annex%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20(%3FfieldofworkLabel)%0AORDER%20BY%20DESC%20(%3FCount)%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT DISTINCT ?fieldofworkLabel (COUNT (?namesake) as ?Count)
WHERE {
  ?item wdt:P31 wd:Q19844914. #university building
  ?item  wdt:P127 wd:Q1458113. # owned by - University of Victoria
  ?item wdt:P138 ?namesake . # who have 'a' namesake
  ?namesake wdt:P101 ?fieldofwork . # namesake with an occupation
  MINUS {?item wdt:P3032 wd:Q107578887.} # adjacent building - Saunders Annex
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
GROUP BY (?fieldofworkLabel)
ORDER BY DESC (?Count)
```
<br>

#### _**Where did the Campus Building namesakes go to school?**_

<iframe style="width: 60vw; height: 85vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%0A%23UVic%20Campus%20Buildings%20with%20namesakes%20and%20where%20they%20studied%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%23%20namesakes%20with%20listed%20places%20of%20education%0ASELECT%20DISTINCT%20%3FeducationLabel%20(COUNT%20(%3Fnamesake)%20as%20%3FCount)%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20'a'%20namesake%0A%20%20%3Fnamesake%20wdt%3AP69%20%3Feducation%20.%20%23%20and%20where%20the%20namesake%20was%20educated%0A%20%20MINUS%20%7B%3Fitem%20wdt%3AP3032%20wd%3AQ107578887.%7D%20%23%20adjacent%20building%20-%20Saunders%20Annex%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20(%3FeducationLabel)%0AORDER%20BY%20DESC%20(%3FCount)%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

<br>
_SPARQL query used to generate the table:_
```
SELECT DISTINCT ?educationLabel (COUNT (?namesake) as ?Count)
WHERE {
  ?item wdt:P31 wd:Q19844914. #university building
  ?item  wdt:P127 wd:Q1458113. # owned by - University of Victoria
  ?item wdt:P138 ?namesake . # who have 'a' namesake
  ?namesake wdt:P69 ?education . # and where the namesake was educated
  MINUS {?item wdt:P3032 wd:Q107578887.} # adjacent building - Saunders Annex
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
GROUP BY (?educationLabel)
ORDER BY DESC (?Count)
```
<br>
### Looking Ahead - Future Directions for Working with Wikidata at UVic Libraries
----  
There are many possible directions to continue to expand the project beyond the scope of the practicum. These include but are not limited to:

* Initiate a pilot project for populating scholarly profiles for UVic faculty members in Wikidata
   * Connect Wikidata items created for UVic Faculties and Departments during this project

* Increase presence of [Indigenous art at UVic](https://www.uvic.ca/services/indigenous/assets/docs/uvic-iace-indigenous-art-on-campus-brochure2.pdf) and representation of Indigenous artists and art forms in Wikidata

* Increase visual representation of the University of Victoria in Wikidata by:
   * Adding digital objects from UVic Archives' [Historical Photograph Collection](https://archives.library.uvic.ca/hpc/index.php/) to Wikimedia Commons
   * Encouraging UVic faculty, staff, and students to upload photos of the campus to Wikimedia Commons 

* Represent namesakes with archival holdings in SNAC (Social Networks and Archival Context) and connect to Wikidata using the SNAC ARK ID property (P3430)
   * Explore possibility of [SNAC Cooperative Membership](https://portal.snaccooperative.org/node/483) for University of Victoria Special Collections and 
     University Archives 
