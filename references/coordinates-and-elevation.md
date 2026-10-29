# Interpreting spatial clues

Read when source coordinates, elevations, or competing sites need interpretation.

## Coordinates and historical conventions

Retain literal notation, units, source date/page, and stated reference system. Establish axis order, hemisphere/sign, decimal separator, angular notation, and reference meridian from the source's legend or institutional documentation. Historical records can use a local meridian, degrees/minutes, or a projected grid. A string such as `3.54` must not be assumed to mean either 3.54 decimal degrees or 3°54′ without context.

Inspect likely transcription/OCR errors and copied metadata without silently repairing them. Keep plausible interpretations as alternatives if evidence cannot settle them. Check province, basin, terrain, distances, landmarks, and the dated station history for consistency; being inside a municipality is insufficient identification.

For projected `(x,y)` establish CRS, datum, units, axis order, and zone. A label such as UTM 32T or Gauss–Boaga alone may leave essential information unresolved. For a local meridian or datum, use a documented transformation rather than an unexplained constant offset. Record original values, chosen transformation/assumptions, target CRS, and resulting coordinates separately. Where a required CRS is unknown, preserve the source coordinates and describe the limitation.

GeoLibre uses geographic WGS84 `[longitude, latitude]`. Transform justified source coordinates with explicit axis order; do not merely relabel a CRS. Source precision and transformation uncertainty limit the meaningful output precision.

Low decimal resolution describes a spatial footprint, not a precise station position. If rounding is established, a rounding cell can be shown. If truncation, OCR error, or coordinate convention is unknown, explain those alternatives rather than assuming a symmetric error box. Use an approximate map marker only with an explicit role such as original estimate, locality centroid, or candidate building.

## Elevation and vertical references

Keep these distinct:

- Recorded station/site elevation, with its date, units, and stated vertical reference.
- Instrument altitude or height above local ground/roof, including the reference point.
- Ground elevation estimated from a topographic contour, spot height, DTM, or DEM/DSM.

Do not add/subtract heights unless the source defines their relationship. Historical elevations can be poorly estimated; modern catalogue elevations can also be approximate or copied. A mismatch may indicate a move, different reference point, transcription problem, terrain variation, or source error. Investigate before declaring a correction.

When available and useful, sample a suitable topographic/terrain source at a supported candidate. Record dataset/edition, resolution or map scale, vertical datum if known, sample method, and whether it describes ground or surface/buildings. Avoid spurious decimals. Report a plausible range where slope, cell size, or uncertain horizontal position dominates. A nearby contour/spot height can support an elevation suggestion without identifying the station.

DEM output is supporting geographical evidence, not a measured historical station elevation. Assess horizontal-location confidence and elevation confidence independently. Do not tune a location until its terrain height matches a doubtful historical number.

## Competing sites

Keep each candidate/site epoch associated with its own evidence and values. Explain why one is better supported: a dated address, observer's institution, mapped building, known move, basin position, or comparable documentary connection. Identify the discriminating evidence still missing. Do not force a numerical ranking or average coordinates from distinct plausible sites.
