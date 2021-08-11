Project by Julia Gilmore, Metadata Assistant, University of Victoria (UVic) Libraries 

Completed Summer 2021

<i> Note: The creation of this page was inspired by a similar [Wikidata visualization page](https://yooylee.github.io/experiment-wikidata-canadian-archive-women-in-stem/) from the University of Ottawa's [Canadian Archive of Women in STEM](https://biblio.uottawa.ca/en/women-in-stem/about) project, and [SCUA Wikidata Experimentation](https://elizabethbassett.github.io/uvic-scua-wikidata-experimentation/), a visualization project connecting archival holdings at University of Victoria Special Collections and University Archives (SCUA) in Wikidata, completed by Elizabeth Bassett in July 2020. </i>
<br>

## Visualizing the University of Victoria (UVic) through Wikidata Queries
----  
<br>

## Faculties and Academic Departments 
----  
<br>

### _**Where are the headquarters for the UVic Faculties and Academic Departments located?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23defaultView%3AMap%0A%0ASELECT%20%3Findividual_entity%20%3Findividual_entityLabel%20%3Fcoordinate_location%20%3Foccupant%20%3FoccupantLabel%20WHERE%20%7B%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%20%3Findividual_entity%20wdt%3AP31%20wd%3AQ19844914.%0A%20%20%3Findividual_entity%20wdt%3AP466%20%3Foccupant.%0A%20%20%3Findividual_entity%20wdt%3AP127%20wd%3AQ1458113.%0A%20%20MINUS%20%7B%3Findividual_entity%20wdt%3AP131%20wd%3AQ2000769.%7D%0A%20%20MINUS%20%7B%3Foccupant%20wdt%3AP466%20wd%3AQ16959841.%7D%0A%20%20%0A%20%20OPTIONAL%20%7B%20%3Findividual_entity%20wdt%3AP625%20%3Fcoordinate_location.%20%7D%0A%20%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**What can I study at the University of Victoria?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23defaultView%3ABubbleChart%0A%23%20What%20can%20I%20study%20at%20UVic%3F%20%0A%23%20instance%20of%20academic%20department%0A%23%20located%20in%20Victoria%0A%23%20has%20field%20of%20work%0A%0ASELECT%20DISTINCT%20%3FstudiesLabel%20%28COUNT%20%28%3Ffaculty%29%20as%20%3FCount%29%0AWHERE%0A%7B%0A%20%20%3Ffaculty%20wdt%3AP31%20wd%3AQ180958.%20%23faculty%0A%20%20%3Ffaculty%20wdt%3AP361%20wd%3AQ1458113.%20%23%20part%20of%20University%20of%20Victoria%0A%20%20%3Ffaculty%20wdt%3AP101%20%3Fstudies%20.%20%23%20field%20of%20work%0A%20%20%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22%20.%20%7D%0A%7D%20%0A%0AGROUP%20BY%20%28%3FstudiesLabel%29%20%0AORDER%20BY%20DESC%20%28%3FCount%29" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**Can you tell me more about the different UVic Faculties?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AGraph%0ASELECT%20%3Fitem%20%3FitemLabel%20%3FlocationLabel%20%3FdepartmentLabel%0AWHERE%20%0A%7B%0A%20%20%23%20Item%20Property%20Value%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ180958.%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20faculty.%0A%20%20%3Fitem%20wdt%3AP361%20wd%3AQ1458113.%20%23%20and%20are%20part%20of%20the%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP276%20%3Flocation.%0A%20%20%3Fitem%20wdt%3AP527%20%3Fdepartment.%0A%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%0A%0A%7D%0A%0A%0A%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**Which UVic Faculties and Academic Departments are listed in LC and VIAF?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#SELECT%20%3Fitem%20%3FitemLabel%20%3FLibrary_of_Congress_authority_IDLabel%20%3FVIAF_IDLabel%20WHERE%20%7B%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%0A%20%20%7B%3Fitem%20wdt%3AP31%20wd%3AQ2467461.%7D%0A%20%20UNION%0A%20%20%7B%3Fitem%20wdt%3AP31%20wd%3AQ180958.%7D%0A%20%20%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP244%20%3FLibrary_of_Congress_authority_ID.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP214%20%3FVIAF_ID.%20%7D%0A%7D%0AORDER%20BY%20DESC%20%28%3FLibrary_of_Congress_authority_IDLabel%29%20%28%3FVIAF_IDLabel%29" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**Which undergraduate UVic Faculties have the most departments?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23defaultView%3ABarChart%0A%0A%23UVic%20Faculties%20with%20most%20number%20of%20departments%0A%23%20instance%20of%20faculty%0A%23%20part%20of%20University%20of%20Victoria%0A%23%20has%20part%20-%20academic%20department%0A%0ASELECT%20DISTINCT%20%3FitemLabel%20%28COUNT%20%28%3Fdepartment%29%20as%20%3FCount%29%0AWHERE%0A%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ180958.%20%23faculty%0A%20MINUS%20%7B%3Fitem%20wdt%3AP31%20wd%3AQ11587546.%20%7D%20%23%20graduate%20faculty%0A%20%20%3Fitem%20wdt%3AP361%20wd%3AQ1458113.%20%23%20part%20of%20-%20University%20of%20Victoria%0A%20%20OPTIONAL%20%7B%3Fitem%20wdt%3AP527%20%3Fdepartment%20.%7D%20%23%20has%20part%20-%20academic%20department%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22%20.%20%7D%0A%7D%20%0A%0AGROUP%20BY%20%28%3FitemLabel%29%20%0AORDER%20BY%20DESC%20%28%3FCount%29" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**What is the social media presence for the various Faculties and Departments?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23Social%20Media%20Presence%20of%20UVic%20Academic%20Departments%0ASELECT%20%3Fitem%20%3FitemLabel%20%3FTwitter_usernameLabel%20%3FFacebook_IDLabel%20%3FInstagram_usernameLabel%20%0AWHERE%20%0A%7B%0A%20%20%23%20Item%20Property%20Value%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%20%23%20and%20are%20located%20in%20Victoria%0A%20%7B%20%3Fitem%20wdt%3AP31%20wd%3AQ2467461.%20%7D%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20academic%20department.%0A%20%20UNION%0A%20%20%7B%3Fitem%20wdt%3AP31%20wd%3AQ180958.%20%7D%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20faculty%0A%20%20%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP2002%20%3FTwitter_username.%20%7D%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP2013%20%3FFacebook_ID.%20%7D%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP2003%20%3FInstagram_username.%20%7D%0A%20%0A%7D%0AORDER%20BY%20DESC%20%28%3FTwitter_usernameLabel%29%20%28%3FFacebook_IDLabel%29%0A%0A%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**Which Faculty or Department has the most Twitter followers?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#SELECT%20%3Fitem%20%3FitemLabel%20%3FTwitter_followers%0AWHERE%0A%7B%0A%20%20%20%20%7B%20%3Fitem%20wdt%3AP31%20wd%3AQ2467461.%7D%20%23%20instance%20of%20academic%20department%20%0A%20%20%20%20%20UNION%0A%20%20%20%20%20%7B%3Fitem%20wdt%3AP31%20wd%3AQ180958.%7D%20%23%20instance%20of%20faculty%20%0A%20%20%20%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132%20.%20%23%20located%20in%20Victoria%0A%20%20OPTIONAL%20%20%20%7B%20%3Fitem%20p%3AP2002%20%3FTwitter_username.%0A%20%20%20%20%3FTwitter_username%20pq%3AP3744%20%3FTwitter_followers.%20%7D%0A%0A%20%20OPTIONAL%20%7B%3Fitem%20wdt%3AP2013%20%3FFacebook_ID.%7D%0A%20OPTIONAL%20%7B%3Fitem%20wdt%3AP2003%20%3FInstagram_ID.%7D%0A%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AORDER%20BY%20DESC%20%28%3FTwitter_followers%29" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

## Exploring the University of Victoria Campus 
----  
<br>

### _**When were the UVic Campus Buildings built?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ATimeline%0ASELECT%20%3Fitem%20%3Flaunchdate%20(SAMPLE(%3Fimage)%20AS%20%3Fimage)%20%3FitemLabel%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914%3B%0A%20%20%20%20wdt%3AP571%20%3Flaunchdate.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage.%20%7D%0A%20%20%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%0A%20%20%3Fitem%20wdt%3AP127%20wd%3AQ1458113.%0A%7D%0AGROUP%20BY%20%3Fitem%20%3FitemLabel%20%3Flaunchdate" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

_This timeline depicts all Campus Buildings where dates of inception are known. The list is not exhaustive, as information for some Campus Buildings was not publicly available at the time of the project. Dates refer to when the buildings were built - not when they were dedicated to specific namesakes. In some instances, buildings have been renamed or had namesakes removed (e.g. Landsdown Residence #1, Fraser Building). All former namesakes are still included in this timeline. _

Sources: 

[University of Victoria: Maps & buildings](https://www.uvic.ca/search/maps-buildings/index.php/)

UVic Campus component of University of Victoria Art Collections (UVAC) 2011 exhibit: [The Emergence of Architectual Modernism in Victoria](https://uvac.uvic.ca/Architecture_Exhibits/UVic_campus/)


### _**What does the UVic campus look like?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AImageGrid%0ASELECT%20%3Fitem%20%3FitemLabel%20%3Fimage%20%3Fcoordinate%0AWHERE%0A%7B%0A%20%20%20%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23%20instance%20of%20university%20building%20%0A%20%20%20%20%20%3Fitem%20wdt%3AP127%20wd%3AQ1458113%20.%20%23%20owned%20by%20University%20of%20Victoria%0A%20%20%20%20%20%3Fitem%20wdt%3AP625%20%3Fcoordinate.%0A%20%20%20%20%20%3Fitem%20wdt%3AP18%20%3Fimage.%0A%0A%20%20%20%20%0A%20%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%7D%0AORDER%20BY%20ASC%20(%3FitemLabel)" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

_Images of the  University of Victoria Campus are also available on Wikimedia Commons under the category: [University of Victoria campus]_(https://commons.wikimedia.org/wiki/Category:University_of_Victoria_campus).

<br>

### _**Which Campus Buildings are named after people?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AMap%0A%23LEED%20Certified%20Buildings%20on%20UVic%20Campus%0ASELECT%20%3Fitem%20%3FitemLabel%20%3Fcoordinate_location%20%3Fcoordinate_locationLabel%20%0AWHERE%20%0A%7B%0A%20%20%23%20Item%20Property%20Value%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23%20all%20the%20items%20that%20have%20instance%20of%20value%20university%20building.%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%20%23%20and%20are%20located%20in%20Victoria%0A%20%20%3Fitem%20wdt%3AP1552%20wd%3AQ1521623.%20%23%20and%20have%20the%20quality%20'Leadership%20in%20Energy%20and%20Environmental%20Design%20%20%20%20%20%20%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%0AOPTIONAL%20%7B%20%3Fitem%20wdt%3AP625%20%3Fcoordinate_location.%20%7D%0A%20%0A%7D%0A%0AORDER%20BY%20(%3Farea)%0A%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**Which Campus Buildings are named after women?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23UVic%20Campus%20Buildings%20with%20female%20namesakes%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%0ASELECT%20DISTINCT%20%3Fitem%20%3FitemLabel%20%3Fnamesake%20%3FnamesakeLabel%20%3Fimage%20%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20%27a%27%20namesake%0A%20%20%3Fnamesake%20wdt%3AP21%20wd%3AQ6581072.%20%23%20and%20namesake%20gender%20is%20female%0A%20%20%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage.%20%7D%0A%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**Which Campus Buildings are LEED Certified and where are they located?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23UVic%20Campus%20Buildings%20with%20female%20namesakes%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%0ASELECT%20DISTINCT%20%3Fitem%20%3FitemLabel%20%3Fnamesake%20%3FnamesakeLabel%20%3Fimage%20%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20%27a%27%20namesake%0A%20%20%3Fnamesake%20wdt%3AP21%20wd%3AQ6581072.%20%23%20and%20namesake%20gender%20is%20female%0A%20%20%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage.%20%7D%0A%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

Source: 

[University of Victoria: Campus Planning and Sustainability](https://www.uvic.ca/sustainability/topics/buildings-grounds/index.php)

### _**What roles and occupations did the Campus Building namesakes hold?**_

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%0A%23UVic%20Campus%20Buildings%20with%20namesakes%20and%20their%20listed%20occupations%20%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%23%20namesakes%20with%20listed%20occupations%0ASELECT%20DISTINCT%20%3FoccupationLabel%20(COUNT%20(%3Fnamesake)%20as%20%3FCount)%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20'a'%20namesake%0A%20%20%3Fnamesake%20wdt%3AP106%20%3Foccupation%20.%20%23%20namesake%20with%20an%20occupation%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20(%3FoccupationLabel)%0AORDER%20BY%20DESC%20(%3FCount)%0A%0A" ></iframe>

<br>

### _**What awards and honours have the Campus Building namesakes received?**_

<iframe style="width: 55vw; height: 50vh; border-style: solid; border-width: thin;" src="https://query.wikidata.org/#%23defaultView%3ABubbleChart%0A%23UVic%20Campus%20Buildings%20with%20namesakes%20and%20awards%20they%20have%20received%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%23%20namesakes%20with%20awards%0ASELECT%20DISTINCT%20%3FawardLabel%20(COUNT%20(%3Fnamesake)%20as%20%3FCount)%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20'a'%20namesake%0A%20%20%3Fnamesake%20wdt%3AP166%20%3Faward%20.%20%23%20namesake%20with%20an%20award%20%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20(%3FawardLabel)%0AORDER%20BY%20DESC%20(%3FCount)%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

### _**What Faculties, Departments, and Campus Building namesakes have holding at University of Victoria Special Collections and University Archives?**_

<iframe style="width: 55vw; height: 50vh; border-style: solid; border-width: thin;" src="https://query.wikidata.org/#%23defaultView%3ATree%0A%23UVic%20Faculties%2C%20Departments%2C%20Buildings%2C%20Building%20namesakes%20whose%20archives%20are%20held%20at%20University%20of%20Victoria%20Special%20Collections%20and%20University%20Archives%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%0ASELECT%20%3Fbuilding%20%3FnamesakeLabel%20%3Ffaculty%20%3FfacultyLabel%20%3Fdepartment%20%3FdepartmentLabel%20%0AWHERE%20%7B%0A%20%20%7B%3Fbuilding%20wdt%3AP31%20wd%3AQ19844914.%0A%20%20%3Fbuilding%20wdt%3AP127%20wd%3AQ1458113.%20%23university%20building%0A%20%20%3Fbuilding%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20%27a%27%20namesake%0A%20%20%3Fnamesake%20wdt%3AP485%20wd%3AQ47518588.%7D%0A%20%20UNION%0A%20%20%7B%3Ffaculty%20wdt%3AP31%20wd%3AQ180958.%0A%20%20%3Ffaculty%20wdt%3AP485%20wd%3AQ47518588.%7D%0A%20%20UNION%0A%20%20%7B%3Fdepartment%20wdt%3AP31%20wd%3AQ2467461.%0A%20%20%3Fdepartment%20wdt%3AP485%20wd%3AQ47518588.%7D%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AORDER%20BY%20DESC%20%28%3FbuildingLabel%29%20%3FfacultyLabel%20%3FdepartmentLabel%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>

_This tree depicts all faculties, departments, and campus building namesakes who are the creators of fonds are located at UVic Special Collections and University Archives. Many of the campus building namesakes are subject access points for various fonds within UVic Archives, however they are not the creators of these fonds and thus, have been omitted from these search results._ 


_SPARQL query used to generate the table:_

```
SELECT ?university_building ?inception WHERE {
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
  ?university_building wdt:P31 wd:Q19844914.
  OPTIONAL {  }
  OPTIONAL {  }
  ?university_building wdt:P131 wd:Q2132;
    wdt:P127 wd:Q1458113.
  LIMIT { ?university_building wdt:P571 ?inception. }
}
----
<br>


