# Italian station sources: vetted starting preset

Actual station data were retrieved and inspected on **2026-10-26**. Eight live registry routes passed; the separate snapshots below passed only for their stated content. Public GETs required no account or email submission. This is a dated access check, not a guarantee of future availability or historical completeness.

Select by region, network, and period before querying. National reach does not make an agricultural network pertinent to every station. A source hosted in Trentino may hold historical Po-compartment records outside Trentino. An endpoint failure does not make unrelated registries relevant.

## Retrieval and revalidation

Use an available web/data tool, or a permitted direct HTTPS client. During verification, Python standard-library HTTP retrieval and CSV/JSON/XML parsing succeeded where a web reader rejected MIME types or file sizes. Distinguish tool/network restrictions from provider access requirements; use available authorized access without bypassing certificate validation or authentication.

Check for real records rather than login/maintenance HTML; inspect schemas, missing values, CRS, pagination, date meanings, and network/station types. Quoted counts below describe the audit sample and are not acceptance tests. Query limits of two are **audit examples**, not complete inventories: filter for the case or paginate until the relevant search is complete. Use documented field definitions before transforming coordinates or interpreting dates. Preserve source links and access dates in the report.

For unlisted regions, discover current official ARPA/APPA, hydrological-service, civil-protection, or agricultural sources using terms such as `anagrafica stazioni`, `consistenza rete`, `stazioni dismesse`, `rete meccanica`, `scheda stazione`, and the locality/network. Demonstrate actual data retrieval before adding a newly discovered registry to this preset. Non-database historical sources remain usable as evidence without being added as registries.

## Live registry routes

### CREA / Rete Agrometeorologica Nazionale (RAN)

- **Pertinence:** CREA/RAN agricultural provenance; verify station status and relevant period.
- **Institutional provenance:** [official RAN map](https://agrometeorological.crea.gov.it/RAN.html) references this [public CSV](https://generic44.blob.core.windows.net/public-repo/RAN/anagrafica_stazioni.csv).
- **Demonstrated:** HTTP 200; CSV parsed into 53 rows with `StationId`, `StationName`, `Status`, `Latitude`, `Longitude`, `Altitude`, `Location`, `Locality`, and `StartDate`.
- **Handling:** 29 rows were `Active`, 24 `To activate`; 9 lacked altitude and 52 lacked start date. Planned sites and blanks must remain explicit. This current roster does not demonstrate historical sites or continuous siting.

### Lombardia / ARPA

- **Pertinence:** Lombardia stations and sensors; choose dated identities rather than matching names alone.
- **Provenance:** [ARPA data guide](https://www.arpalombardia.it/temi-ambientali/meteo-e-clima/guida-richiesta-dati/), [regional dataset metadata](https://www.dati.lombardia.it/api/views/nf78-nj6b.json).
- **Demonstrated full export:** [ARPA semicolon CSV](https://idro.arpalombardia.it/manual/AnagraficaSensoriWEB.csv), HTTP 200, 1,462 sensor rows / 390 station IDs. Observed station/sensor identity, municipality, province, `Quota`, `UTM Nord`, `UTM Est`, and sensor-series dates.
- **Demonstrated alternative:** [regional JSON, two-row example](https://www.dati.lombardia.it/resource/nf78-nj6b.json?$limit=2), with `idstazione`, `nomestazione`, `lat`, `lng`, `quota`, `location`, and date/history fields. Use filtering/pagination for the actual case.
- **Handling:** sensor rows are not unique stations or relocation episodes. Do not infer an EPSG code from generic UTM labels; prefer documented geographic-coordinate fields or establish the projected CRS before conversion.

### Piemonte / ARPA

- **Pertinence:** Piemonte meteorological network; nested histories can help separate station and sensor epochs.
- **Provenance:** [official station map](https://www.arpa.piemonte.it/rischi_naturali/snippets_arpa_graphs/map_meteoweb/?rete=stazione_meteorologica) references the [station JSON](https://utility.arpa.piemonte.it/meteoidro/stazione_meteorologica/).
- **Demonstrated:** HTTP 200 JSON, `count=336`, station `results`, `next=null`; records include denomination, locality/address, code, municipality/province, `longitudine_e_wgs84_d`, `latitudine_n_wgs84_d`, `quota_stazione`, station dates, and nested sensor histories/support heights.
- **Handling:** follow `next` if present. Distinguish station, measurement point, and sensor identity; dates alone do not establish an unchanged physical site. Indexed service warnings did not prevent this actual data retrieval.

### Veneto / ARPAV

- **Pertinence:** Veneto network; filter station types to the meteorological evidence needed.
- **Provenance/access:** [official XML directory](https://meteo.arpa.veneto.it/?page=xml), [station XML](https://meteo.arpa.veneto.it/meteo/dati_meteo/xml/stazioni.xml).
- **Demonstrated:** HTTP 200; 192 `STAZIONE` elements with `IDSTAZ`, `NOME`, `X`, `Y`, `QUOTA`, type, municipality/province, and station-resource link.
- **Handling:** the document declares **EPSG:4258**. Honor it; do not silently relabel it WGS84/EPSG:4326. Parse XML from bytes with its encoding declaration. Current/mixed station types, including a mobile entry, do not establish a historical relocation chronology.

### Emilia-Romagna / Arpae Dext3r metadata

- **Pertinence:** geography and operator/network represented by Arpae; filter mixed meteorological, hydrometric, maritime, and other networks.
- **Provenance:** [official application JavaScript](https://simc.arpae.it/dext3r/js/dext3r.js) references the [public station JSON](https://simc.arpae.it/meteozen/rt_data/stations).
- **Demonstrated:** HTTP 200; 1,829 records with ID/name, network, height, GeoJSON geometry, administrative/basin information, owner, manager, and categories.
- **Handling:** use **`geometry.coordinates`**, observed as decimal `[lon, lat]`. Top-level `lon`/`lat` were scaled integers; for one Brisighella record these were `1175545`/`4421978`, versus geometry `[11.755449,44.219775]`. Do not guess a scaling formula.
- **Access distinction:** this metadata GET needed no email/login. The separate observation-extraction UI requests email delivery; the preset does not authorize or require that submission. Retain [Arpae's metadata-accuracy warning](https://simc.arpae.it/dext3r/doc/GuidaDext3r.html).

### Provincia autonoma di Trento / Meteotrentino

- **Pertinence:** Trentino station identity and current/closed-site clues.
- **Provenance:** [service directory](https://dati.meteotrentino.it/service.asmx), [method documentation](https://dati.meteotrentino.it/service.asmx?op=listaStazioniJson).
- **Demonstrated:** [station JSON](https://dati.meteotrentino.it/service.asmx/listaStazioniJson), HTTP 200; `sites` list with 207 records, including 95 nonblank `fine` values. Fields include `codice`, `nome`, `nomebreve`, `quota`, `latitudine`, `longitudine`, `est`, `north`, `inizio`, and `fine`.
- **Handling:** closed/historical entries occur despite the operation's description emphasizing automatic monitoring. The earliest observed start, 1920-09-01, does not promise complete coverage since then. Keep separate site records distinct; an interval does not prove stable siting. A missing Content-Type header did not prevent JSON parsing.

### Toscana / Servizio Idrologico Regionale (SIR)

- **Pertinence:** relevant SIR network/locality, basin, sensor types, and historical coverage.
- **Provenance:** [station-search page and precision warning](https://www.sir.toscana.it/consistenza-rete); its public application constructs parameterized requests below.
- **Demonstrated detail:** [example station TOS01000025](https://www.sir.toscana.it/open_layers/ajax_stations.php?id=TOS01000025), HTTP 200 JSON with ID/name, lon/lat, manager/history flag, and HTML `description` containing locality, quota, coordinate convention, and sensors.
- **Demonstrated list:** [bounded meteorological example](https://www.sir.toscana.it/open_layers/ajax_stations.php?bbox=8.5,42.2,13.5,44.6&zoom=8&regions=TOS&models=sir&types=pluvio,termo), HTTP 200, 467 features. Replace bounds, filters, and IDs to fit the actual case.
- **Handling:** a bare endpoint failed while parameterized GETs worked. Returned custom feature objects are not standard GeoJSON; construct geometry explicitly and parse site/elevation text from HTML. The operator warns that coordinate/elevation precision varies by map/GPS method. Public metadata GETs worked despite a login panel elsewhere.

### Campania / thermal-sensor inventory

- **Pertinence:** Campania thermal-sensor stations; this subset does not represent every network or historical station.
- **Provenance:** [institutional catalogue entry](https://dati.regione.campania.it/catalogo/datasetdetail/1e147fdd-26ee-4b96-b755-c7c7db5517e4).
- **Demonstrated:** [CKAN JSON, two-record example](https://dati.regione.campania.it/ckan/api/3/action/datastore_search?resource_id=49e10343-87b8-4a11-bff5-3973be69ae86&limit=2), HTTP 200; `success=true`, `total=100`, field definitions and records inspected. Fields include `Cod_stazione`, `NOME`, municipality/province, sensor/network, `Latitudine_WGS84`, `Longitudine_WGS84`, and `QUOTA_SITO`.
- **Handling:** coordinate strings are **DMS with decimal commas**, e.g. `41° 05' 33,8"`, rather than decimal degrees. Paginate/query the records needed. Do not invent meanings for `ANNO` or the misleadingly named timestamp field `Sensore`. Use the public endpoint, not any internal-address help link in a response.

## Accessible document snapshots and cross-checks

These provide actual data/evidence, with narrower scope than live catalogues. Select only relevant material and cite the inspected page or record.

### Sardegna / ARPAS SIRA site-summary snapshot

[Official network page](https://portal.sardegnasira.it/en/rete-meteo-climatica-dati-ambientali) links this [four-page inventory PDF](https://portal.sardegnasira.it/documents/21213/200223/Rete_Unica-scheda%2Bstazioni.pdf/9bbf3d0f-1d98-46e8-a5b3-71a5b843b9ed). HTTP 200; actual station tables extracted. Includes code, municipality, locality/placement, site description, type, measured quantities, and start date. Named aqueducts, road-maintenance houses, and former railway sites can be useful leads. **Numeric coordinates/elevations were not demonstrated in this PDF.** Its network configuration is a snapshot; no live SIRA query is claimed verified.

### Arpae / 2016 administrative inventory

[DET-2016-228 PDF](https://apps.arpae.it/documento/DET2016228#page=29), HTTP 200; actual PDF pages 29–31 inspected. Listed agricultural/urban/local stations have names, municipality/province, quota, and UTM coordinates. This is a dated subset, not all historical Arpae stations. The inspected coordinate table gives zone/band without establishing a datum: verify the CRS before transforming.

### NOAA / GHCN-Daily inventory

[Official product/documentation](https://www.ncei.noaa.gov/products/land-based-station/global-historical-climatology-network-daily), [fixed-width station inventory](https://www.ncei.noaa.gov/pub/data/ghcn/daily/ghcnd-stations.txt). HTTP 200; Italian station ID/name/latitude/longitude/elevation records streamed and inspected. Use documented field widths and country/network definitions; filter to the relevant case. Direct streaming worked when a web reader rejected the approximately 11.44 MB file. It is a cross-check, not evidence that the latest catalogue point applies throughout an observation series or that values are independent of the original operator.

### Historical Po/Parma annals: demonstrated specimen

[Meteotrentino annals catalogue](https://www.meteotrentino.it/pubblicazioni/pubblicazioni-meteorologia/annali-idrologici/) links this [Parma 1974 Part I scan](https://www.meteotrentino.it/wp-content/uploads/2025/02/PARMA_1974_PARTE1.pdf#page=6). HTTP 200, approximately 13.35 MB, 279 pages; PDF page 6 rendered and visually inspected. The station table distinguishes name/basin, quota above sea level, instrument height, and observation start year. The scan lacks a usable initial text layer; OCR alone lost cell associations, so verify relevant rows visually.

The specimen demonstrates accessible historical evidence, not a requirement to use 1974 for other periods. Follow catalogue links to the relevant compartment/year and inspect that document. Geographic relevance follows historical basin/compartment coverage, which can span several modern regions.

## Preset boundary

Only demonstrated data routes are included above. An institutional reputation, documented holdings, or an accessible catalogue description does not establish automated access to station data. Reassess failed routes only when pertinent; promote them into the preset after actual records are retrieved. This boundary concerns registry usability, **not whether a non-database source can provide a valuable historical hint**. Discover and assess such evidence freely within the investigation's scope.
