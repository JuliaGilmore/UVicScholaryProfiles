Project by Julia Gilmore, Metadata Assistant, University of Victoria Libraries | Summer 2021

The goal of this project is to experiment with ways that the University of Victoria (UVic) Libraries can use Wikidata to support the creation of scholarly profiles. 

_Note: The creation of this page was inspired by a similar [Wikidata visualization page](https://yooylee.github.io/experiment-wikidata-canadian-archive-women-in-stem/) from the University of Ottawa's [Canadian Archive of Women in STEM](https://biblio.uottawa.ca/en/women-in-stem/about) project, and a previous UVic Wikidata visualization project (https://elizabethbassett.github.io/uvic-scua-wikidata-experimentation/) connecting archival holdings at University of Victoria Special Collections and University Archives (SCUA), completed by Elizabeth Bassett, Special Collections and Archives Assistant, in July 2020. 
<br>

## Visualizing the University of Victoria (UVic) through Wikidata Queries
----  

<br>

### _**When were the UVic Campus Buildings built?**_ 

<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#SELECT%20%3Funiversity_building%20%3Fof%20%3FofLabel%20%3Funiversity_buildingLabel%20WHERE%20%7B%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%20%3Funiversity_building%20wdt%3AP31%20wd%3AQ19844914.%0A%20%20OPTIONAL%20%7B%20%20%7D%0A%20%20OPTIONAL%20%7B%20%3Funiversity_building%20wdt%3AP571%20%3Fof.%20%7D%0A%20%20%3Funiversity_building%20wdt%3AP127%20wd%3AQ1458113.%0A%7D%0ALIMIT%20100" ></iframe>

<br>

This timeline depicts all Campus Buildings where dates of inception are known. Note that the list is not exhaustive, as this information may not be available for all UVic Campus Buildings. 

<br>

_SPARQL query used to generate the table:_

```
SELECT ?university_building ?of ?ofLabel ?university_buildingLabel WHERE {
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
  ?university_building wdt:P31 wd:Q19844914.
  OPTIONAL {  }
  OPTIONAL { ?university_building wdt:P571 ?of. }
  ?university_building wdt:P127 wd:Q1458113.
}
LIMIT 100

<br>

