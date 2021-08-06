Project by Julia Gilmore, Metadata Assistant, University of Victoria (UVic) Libraries 

Completed Summer 2021

<i> Note: The creation of this page was inspired by a similar [Wikidata visualization page](https://yooylee.github.io/experiment-wikidata-canadian-archive-women-in-stem/) from the University of Ottawa's [Canadian Archive of Women in STEM](https://biblio.uottawa.ca/en/women-in-stem/about) project, and [SCUA Wikidata Experimentation](https://elizabethbassett.github.io/uvic-scua-wikidata-experimentation/), a visualization project connecting archival holdings at University of Victoria Special Collections and University Archives (SCUA) in Wikidata, completed by Elizabeth Bassett in July 2020. </i>
<br>

## Visualizing the University of Victoria (UVic) through Wikidata Queries
----  

<br>

### _**When were the UVic Campus Buildings built?**_ 

<iframe style="width: 55vw; height: 50vh; border-style: solid; border-width: thin;" src="https://query.wikidata.org/#%23defaultView%3ATimeline%0ASELECT%20%3Fitem%20%3Flaunchdate%20%28SAMPLE%28%3Fimage%29%20AS%20%3Fimage%29%20%3FitemLabel%20WHERE%20%7B%0A%20%20%3Fitem%20wdt%3AP31%20wd%3AQ19844914%3B%0A%20%20%20%20wdt%3AP571%20%3Flaunchdate.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22.%20%7D%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3Fimage.%20%7D%0A%20%20%0A%20%20%3Fitem%20wdt%3AP131%20wd%3AQ2132.%0A%20%20%3Fitem%20wdt%3AP127%20wd%3AQ1458113.%0A%7D%0AGROUP%20BY%20%3Fitem%20%3FitemLabel%20%3Flaunchdate" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

<br>


This timeline depicts all Campus Buildings where dates of inception are known. The list is not exhaustive, as information for some Campus Buildings was not publicly available at the time of the project. 

Sources: 

[University of Victoria: Maps & buildings](https://www.uvic.ca/search/maps-buildings/index.php/)

University of Victoria Art Collections (UVAC) 2011 exhibit: [The Emergence of Architectual Modernism in Victoria; UVic Campus](https://uvac.uvic.ca/Architecture_Exhibits/UVic_campus/)


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

