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

