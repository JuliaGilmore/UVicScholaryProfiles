Project by Julia Gilmore, Metadata Assistant, University of Victoria (UVic) Libraries 

Completed Summer 2021

<i> Note: The creation of this page was inspired by a similar [Wikidata visualization page](https://yooylee.github.io/experiment-wikidata-canadian-archive-women-in-stem/) from the University of Ottawa's [Canadian Archive of Women in STEM](https://biblio.uottawa.ca/en/women-in-stem/about) project, and [SCUA Wikidata Experimentation](https://elizabethbassett.github.io/uvic-scua-wikidata-experimentation/), a visualization project connecting archival holdings at University of Victoria Special Collections and University Archives (SCUA) in Wikidata, completed by Elizabeth Bassett in July 2020. </i>
<br>

## Visualizing the University of Victoria (UVic) through Wikidata Queries
----  

<br>

### _**When were the UVic Campus Buildings built?**_ 

<iframe style="width: 55vw; height: 50vh; border-style: solid; border-width: thin;" src="https://w.wiki/3nxb" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>


This timeline depicts all Campus Buildings where dates of inception are known. The list is not exhaustive, as information for some Campus Buildings was not publicly available at the time of the project. 

Sources: 

[University of Victoria: Maps & buildings](https://www.uvic.ca/search/maps-buildings/index.php/)

UVic Campus component of University of Victoria Art Collections (UVAC) 2011 exhibit: [The Emergence of Architectual Modernism in Victoria](https://uvac.uvic.ca/Architecture_Exhibits/UVic_campus/)


<br>

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
<br>

### _**When are the occupations of the UVic Campus Building namesakes?**_ 


src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%0A%23UVic%20Campus%20Buildings%20with%20namesakes%20and%20their%20listed%20occupations%20%0A%23%20instance%20of%20university%20building%0A%23%20owned%20by%20University%20of%20Victoria%0A%23%20namesake%0A%23%20namesakes%20with%20listed%20occupations%0ASELECT%20DISTINCT%20%3FoccupationLabel%20(COUNT%20(%3Fnamesake)%20as%20%3FCount)%0AWHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914.%20%23university%20building%0A%20%20%3Fitem%20%20wdt%3AP127%20wd%3AQ1458113.%20%23%20owned%20by%20-%20University%20of%20Victoria%0A%20%20%3Fitem%20wdt%3AP138%20%3Fnamesake%20.%20%23%20who%20have%20'a'%20namesake%0A%20%20%3Fnamesake%20wdt%3AP106%20%3Foccupation%20.%20%23%20namesake%20with%20an%20occupation%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AGROUP%20BY%20(%3FoccupationLabel)%0AORDER%20BY%20DESC%20(%3FCount)%0A%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>
This table depicts all known occupations for the namesakes of UVic campus buildings. 

<br>

_SPARQL query used to generate the table:_

```
#defaultView:BubbleChart
#UVic Campus Buildings with namesakes and their listed occupations 
# instance of university building
# owned by University of Victoria
# namesake
# namesakes with listed occupations
SELECT DISTINCT ?occupationLabel (COUNT (?namesake) as ?Count)
WHERE {
  ?item wdt:P31 wd:Q19844914. #university building
  ?item  wdt:P127 wd:Q1458113. # owned by - University of Victoria
  ?item wdt:P138 ?namesake . # who have 'a' namesake
  ?namesake wdt:P106 ?occupation . # namesake with an occupation

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
GROUP BY (?occupationLabel)
ORDER BY DESC (?Count)
<br>


