# Station evidence report

Write in the user's language. Adapt the sections to the case; use a concise findings section followed by sufficient detail to audit the reasoning. A Markdown evidence table is useful where it clarifies comparisons; no separate machine-readable candidate table is requested.

Use stable relative links **inside the saved report** so its directory travels together. In the final chat response, link actual local files using absolute paths. Do not substitute a generic portal URL for a specific available record/page.

## Suggested structure

### Findings

State the station identity/period under investigation, the evidence found, and what remains unresolved. Distinguish a documented site, a supported location suggestion, and an unresolved locality. Where defensible, give `(longitude, latitude)` with CRS and/or original `(x,y)` with its reference system, plus elevation and its meaning/source. Omit unsupported values rather than filling every field. Label multiple suggestions clearly.

### Original clues

Preserve the user's literal names, identifiers, dates, coordinates, elevation, and document/workbook locators. Explain consequential ambiguity and any clarifications received. Keep these separate from newly retrieved metadata and transformed values.

### Evidence and chronology

For each material source give institution/author, title/date or map/imagery edition, exact URL, access date, page/table/record identifier, and the relevant observation. A short quotation or faithful paraphrase can help, subject to source quotation limits. State whether the material was inspected or remains a lead.

Link station identity to site and period. Identify operator changes, relocations, alias ambiguity, and possible dependence among sources. Distinguish source statements, geographical observations, and your inferences.

### Suggested sites or locality

For each suggestion/site epoch: consistent map ID, coordinates/area/building as justified, elevation type/source, evidence for and against, and separate qualitative assessments of identity, horizontal location, and elevation. Explain uncertainty in concrete terms. A single known structure may be useful even if its instrument position is unknown.

### Map investigation and outputs

Link `station.html` and `station.geolibre.json` using their actual filenames. Describe layers, legend/status meanings, and any locality-centroid or original-estimate markers. Report what was actually inspected in GeoLibre/other maps, edition/capture dates when available, and the inference each observation supports. Mark unavailable interactive inspection or unexamined imagery explicitly.

The report's linked/embedded map must open with the **full GeoLibre interface** and **Google Satellite selected by default**, with normal menus, toolbar, panels, layer controls, and basemap switching available. Avoid map-only, read-only/compact, or hidden-interface exports. Tell the reader they can change backgrounds through the basemap controls. Verify the delivered HTML as well as the editable project: switching backgrounds must work without hiding the station/evidence overlays, and reopening must restore Google Satellite. Report any unavailable provider or untested interaction honestly.

Credit map/imagery providers. State any hosted-viewer/remote-layer internet dependencies. Include a screenshot only when it adds evidence, preserving provenance and attribution; it does not replace the interactive artifacts.

### Limits and next evidence

Record material access failures, selected relevant searches with no useful match, and why accessible leads were exhausted when that is the outcome. Describe the next record/image that could distinguish alternatives. Failed access or no search result does not establish nonexistence. Do not bury contradictory evidence or imply an uninspected document was read.

### References

Use descriptive links with page/record locators where available; keep citations near the claims they support. Include direct data URLs and their institutional provenance when a registry record has no stable individual page. Preserve useful non-database historical sources with the same care about authorship and dates.

## Delivery check

- Does each location/elevation claim trace to inspected evidence or an explicitly supported inference?
- Are source values, transformations, station epochs, and instrument heights distinguishable?
- Are contradictory findings and unsupported precision visible?
- Do map and report identifiers/statuses agree, and do their file links resolve?
- Does map verification accurately state what was rendered or visually inspected?
- Does the delivered map expose the full GeoLibre interface, open on Google Satellite, and allow working basemap changes while preserving evidence overlays?
- Is an unresolved result reported honestly without invented points or elevations?
