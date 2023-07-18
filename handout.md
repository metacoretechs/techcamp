# REST for success - getting data with APIs
## VALA Tech Camp 2023 handout

### Visual Studio Code

Can be installed from:

<https://code.visualstudio.com>

### Thunder Client

Lightweight API client plug-in for VS Code.

Can be installed from VS Code Marketplace, or from:

<https://www.thunderclient.com>

### Public APIs
<https://github.com/public-apis/public-apis>

#### Universities List
Endpoint: `http://universities.hipolabs.com/search`

Sample API requests:
```
http://universities.hipolabs.com/search?name=Victoria
http://universities.hipolabs.com/search?country=Australia
```

#### VIAF
Documentation: <https://www.oclc.org/developer/api/oclc-apis/viaf/authority-cluster.en.html>

Endpoint: <http://www.viaf.org/viaf/>

Sample API request:
```
http://viaf.org/viaf/102333412/viaf.json
```
### Authentication
#### Trove API
<https://trove.nla.gov.au/about/create-something/using-api/api-technical-guide>

### Parsing JSON

JSONGrid: <https://jsongrid.com>

See below how to parse JSON in OpenRefine or Excel.

### Wikidata
<https://www.wikidata.org/>

Wikidata in Brief handout: <https://upload.wikimedia.org/wikipedia/commons/8/8d/Wikidata-in-brief-1.0.pdf>

Wikidata Query Service in Brief: <https://upload.wikimedia.org/wikipedia/commons/a/ac/Wikidata_Query_Service_in_Brief.pdf>

#### "Simple" queries using Wikidata API

Wikidata statements about Stephen Fry (Q192912):
```
https://www.wikidata.org/w/api.php?action=wbgetentities&ids=Q192912&props=labels|claims&format=json
https://www.wikidata.org/w/api.php?action=wbgetclaims&entity=Q192912&format=json
```

#### Complex queries using SPARQL
Encode spaces in query: <https://www.textfixer.com/html/encode-url.php>

Original query:
```
SELECT ?lang ?langLabel ?human ?humanLabel ?educatedat ?educatedatLabel ?coords
{
  ?lang wdt:P31/wdt:P279* wd:Q9143 .
  ?human wdt:P31 wd:Q5 .
  { ?lang wdt:P287 ?human } UNION { ?lang wdt:P170 ?human } UNION { ?lang wdt:P943 ?human } UNION { ?lang wdt:P178 ?human } .

  ?human wdt:P69 ?educatedat .
  ?educatedat wdt:P625 ?coords .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en,fr" }
}
LIMIT 100
```
<https://query.wikidata.org/#%23Universities%20of%20main%20programming%20language%20authors%0ASELECT%20%3Flang%20%3FlangLabel%20%3Fhuman%20%3FhumanLabel%20%3Feducatedat%20%3FeducatedatLabel%20%3Fcoords%0A%7B%0A%20%20%3Flang%20wdt%3AP31%2Fwdt%3AP279%2a%20wd%3AQ9143%20.%0A%20%20%3Fhuman%20wdt%3AP31%20wd%3AQ5%20.%0A%20%20%7B%20%3Flang%20wdt%3AP287%20%3Fhuman%20%7D%20UNION%20%7B%20%3Flang%20wdt%3AP170%20%3Fhuman%20%7D%20UNION%20%7B%20%3Flang%20wdt%3AP943%20%3Fhuman%20%7D%20UNION%20%7B%20%3Flang%20wdt%3AP178%20%3Fhuman%20%7D%20.%0A%0A%20%20%3Fhuman%20wdt%3AP69%20%3Feducatedat%20.%0A%20%20%3Feducatedat%20wdt%3AP625%20%3Fcoords%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2Cfr%22%20%7D%0A%7D%0ALIMIT%20100>

Submit query via API:
```
https://query.wikidata.org/sparql?query=SELECT%20%3Flang%20%3FlangLabel%20%3Fhuman%20%3FhumanLabel%20%3Feducatedat%20%3FeducatedatLabel%20%3Fcoords %7B %20%20%3Flang%20wdt%3AP31%2Fwdt%3AP279%2A%20wd%3AQ9143%20. %20%20%3Fhuman%20wdt%3AP31%20wd%3AQ5%20. %20%20%7B%20%3Flang%20wdt%3AP287%20%3Fhuman%20%7D%20UNION%20%7B%20%3Flang%20wdt%3AP170%20%3Fhuman%20%7D%20UNION%20%7B%20%3Flang%20wdt%3AP943%20%3Fhuman%20%7D%20UNION%20%7B%20%3Flang%20wdt%3AP178%20%3Fhuman%20%7D%20. %20%20%3Fhuman%20wdt%3AP69%20%3Feducatedat%20. %20%20%3Feducatedat%20wdt%3AP625%20%3Fcoords%20. %20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2Cfr%22%20%7D %7D LIMIT%20100&format
```

## Further reading / advanced topics

Fetching and Parsing Data from the Web with OpenRefine: <https://programminghistorian.org/en/lessons/fetch-and-parse-data-with-openrefine>

JSON API Tutorial: Power BI: <https://psdata.un.org/howto/powerbi_json>

Python API Tutorial: Getting Started with APIs: <https://www.dataquest.io/blog/python-api-tutorial/>