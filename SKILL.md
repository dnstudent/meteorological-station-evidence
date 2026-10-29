---
name: meteorological-station-evidence
description: Investigate evidence about meteorological station sites, historical relocations, coordinates, elevations, and associated buildings or landmarks from incomplete records. Prioritize Italy and nearby countries while supporting worldwide research; produce a cited Markdown report and GeoLibre map. Use for station identity and siting research, rather than weather forecasts or routine observation downloads.
---

# Meteorological Station Evidence

Find and assess evidence about a station, especially where and at what elevation it stood during the relevant period. A supported location suggestion is useful; finding a definitive point is not a condition of success. A documented building, locality, or unresolved set of alternatives can be the honest result.

Work worldwide, prioritizing Italian and neighbouring sources when relevant. Treat the user's historical coordinates and elevations as clues with limited reliability. Preserve them literally rather than silently replacing them with catalogue values.

## Frame the investigation

Extract available names/aliases, identifiers, operator/network, country/region, dates, coordinates, elevation, observer, addresses, buildings, basin, and original document/page. Separate supplied facts from your interpretations. For spreadsheet input, retain sheet and row/cell references.

Ask whether the user has existing station registries they can provide as additional evidence, and encourage them to explain how to interpret those registries. If the agent harness can access files on the user's machine without an upload, also ask whether they have a digital elevation model (DEM) available and where it can be found. Continue independent research while awaiting their reply.

Ask useful follow-up questions when they can resolve a consequential ambiguity: target period, two places with the same name, coordinate notation, or an unreadable source. Start useful research from incomplete information and continue independent leads while awaiting answers. Do not require the user to know facts you can investigate.

The target is the site during the period of interest. Distinguish dated sites, instruments, and networks; neither a reused station identifier nor a long merged observation series proves an unchanged location. Keep competing identities or relocations separate until evidence connects them.

## Select pertinent sources

For an Italian case, consult [the vetted Italian source preset](references/italian-sources.md) and select entries by geography, responsible network, and historical period **before querying them**. It is a source directory, not a checklist.

- A Naples station belongs with relevant Campania and national sources. ARPA Lombardia requires a specific documented connection to that case.
- Consider historical hydrological compartments, basin coverage, border changes, and cross-region operators when evidence makes them relevant. A provider's hosting location is not its dataset's geographic remit.
- If a relevant registry has no match, examine aliases, former operators, contemporary records, and relevant archives. Do not sweep unrelated regional registries.
- Discover suitable national/local sources for unlisted regions and neighbouring countries. Do not assume the Italian preset is complete or query its endpoints for unrelated countries.

**Registry inclusion rule:** every registry represented as usable in the preset must have demonstrated agent retrieval of actual station data. At use time, recheck the relevant endpoint and inspect the payload. HTTP success, portal text, a documented export, and search snippets alone do not establish data access. A downloaded inventory PDF can qualify for its stated subset; it does not become a live database. Preserve endpoint, access date, format, scope, and important parsing limits. Add a new preset registry only after retrieving and inspecting actual records.

**Wider evidence remains welcome.** The preset is a starting point, not a closed list of permissible sources. Use local histories, institutional narratives, newspapers, photographs, postcards, correspondence, observer biographies, theses, heritage records, historical maps, place-name descriptions, and other geographical or historical hints even when they provide no formal database. Prefer contemporary/primary evidence when available; assess authorship, date, provenance, specificity, and independence for other accounts. Treat an uninspected document or search snippet as a lead, not an established fact. A useful clue need not supply numeric coordinates.

Inspect the actual record, scan, or image supporting a claim. Cite its author/institution, title/date, URL, and page/table/record or image locator. Check table headings, units, legends, and footnotes. Verify decisive OCR readings against the page image, especially decimal signs, heights, names, and column alignment.

## Assess the evidence

Build a dated chain from station identity to locality, building/landmark, and any defensible coordinates/elevation. Search aliases and historical names in relevant languages. Compare source dates and coverage rather than voting among repeated numbers.

Use [coordinate and elevation guidance](references/coordinates-and-elevation.md) when interpreting or comparing spatial values. Record transformations separately from literal source values. Numerical precision in a catalogue does not establish measurement accuracy.

For every material interpretation, explain:

- What an inspected source explicitly states, and which station/epoch it describes.
- What maps or images actually show, with edition/capture date when known.
- What you infer, the supporting connection, and the uncertainty or contrary evidence.

Rank multiple suggestions when warranted, with evidence for and against each. Use qualitative confidence with reasons; assess identity, horizontal location, and elevation separately. One specific contemporary site record can outweigh many derivative catalogues. Do not treat copies of one upstream record as independent corroboration or absence from a registry as proof of nonexistence.

Offer a point only to the specificity justified by the evidence. A town centre or building centroid may illustrate a locality; label it as such rather than placing the station there. Preserve a supported area/structure description when a point is unjustified. A DEM value or plausible-looking weather enclosure cannot establish historical occupancy.

## Investigate and deliver with GeoLibre

Load the installed **geolibre** skill before map work and follow its current tool/API guidance. Use GeoLibre during investigation as well as for the deliverable. Its project-authoring MCP tools do not themselves pan or inspect a live map: use an available browser/embed client or notebook widget for interactive inspection. Google Maps and Street View can supply additional context when accessible.

Inspect relevant terrain, slopes, ridges, valleys, settlements, paths, institutional grounds, building positions, and dated imagery/map editions. Follow promising visual clues and revisit candidates. Record the particular observation and how it changes the interpretation. Modern imagery establishes present context; historical station occupancy requires a historical connection. Record Street View capture dates when shown; distinguish them from access dates.

Maintain visually distinct layers for supplied estimates, documentary site positions, inferred alternatives, relevant landmarks, and justified uncertainty areas. Use candidate/site identifiers consistently in the report and map. Include dates, status, source links, and uncertainty in readable popups. Put GeoLibre geometry in WGS84 `[longitude, latitude]`; retain original CRS/values in descriptions or properties. Do not imply a circular search radius or confidence area has statistical meaning unless justified.

Provide an editable `.geolibre.json` project **and** an exported HTML viewer. Inline the small case geometries and retain basemap/layer attribution. The HTML can depend on the hosted viewer, remote tiles, and internet access; do not promise offline rendering. A public viewer URL requires an actually hosted, reachable project, not a local path disguised as a URL.

**Full interface in the report map:** every linked or embedded report map must present the full GeoLibre application interface, with menus, toolbar, layer panels, and controls available, including the ability to change the basemap. Use `layout="full"` when creating a Python widget, and check the exported HTML/iframe separately because an exporter may handle layout independently. Keep full-application presentation when constructing viewer URLs; do not apply `maponly`, `layout=viewer`, compact/embed layouts, hidden toolbars/panels, or custom CSS that removes the normal interface. Give an embedded map enough space to use its controls. Follow the current [GeoLibre embedding guidance](https://geolibre.app/user-guide/embedding/); the `embed=1` project-message bridge is compatible with full UI and is distinct from the compact `layout=embed` presentation.

**Default background: Google Satellite.** Select Google Satellite through the current GeoLibre basemap catalogue/Basemaps control and persist it in the delivered project, so both the editable project and report map reopen with that background. The inspected Basemaps control identifies it as `google-satellite`; confirm that entry in the installed version rather than inventing a Python `basemap` alias. Keep the normal basemap chooser available and ensure switching to another background actually replaces or hides Google imagery while preserving the station/evidence overlays. An opaque Google raster permanently covering the chosen basemap does not meet this requirement. Use the supported provider configuration and attribution; if Google imagery cannot load, report that limitation instead of silently substituting another provider or claiming the default was verified.

After editing, describe/validate the project using the chosen GeoLibre surface and, when a viewing surface is available, open the delivered HTML and check rendering, framing, layers, popups, full-interface controls, and the initial Google Satellite background. Change to a different basemap, verify the background changes while evidence overlays remain, then restore Google Satellite and confirm the saved/reopened default. Creating an export is not visual inspection. If interactive inspection is unavailable, state that limitation, preserve the map artifacts, and distinguish unexamined layers or untested controls from observations actually made. If no position is supported, show only defensible supplied/locality context with its status; do not invent a station pin. If even geographic context or map generation is unavailable, deliver the evidence report and identify the unresolved map requirement without fabricating a link.

## Report and finish

Use [the report guide](references/report-guide.md). Save into the workspace's existing reporting convention, normally `reports/<station-slug>/`, with a concise findings section followed by the auditable research record. Link external evidence and both GeoLibre artifacts. For a batch, keep station/epoch findings distinct and add a short Markdown index.

The requested deliverables are Markdown and GeoLibre artifacts. Do not add a separate machine-readable candidate table/export unless the user asks; embedding case geometry and properties in the GeoLibre project is part of the map.

Default to a thorough investigation, adapting to a requested quick pass or time budget. Stop when the evidence adequately supports the useful findings or accessible relevant leads stop producing material progress. Document remaining uncertainty and the next evidence that would distinguish alternatives. Paid access, contacting institutions, and submitting requests with user details require separate authorization.

An investigation that supplies well-referenced evidence and honestly leaves the station's position unresolved is complete research. Never invent coordinates, elevation, sources, inspected imagery, or certainty merely to make the report look finished.
