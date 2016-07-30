# nyc-libraries

NYC libraries location data for all five boroughs.

## Contents

The data is provided in two formats:
 * GeoJSON: `data/geojson/nyc-libraries.geojson`
 * Shapefile: `data/shp/nyc-libraries.shp`

## Methodology

 1. The [Library](https://data.cityofnewyork.us/Business/Library/p4pf-fyc4) dataset from NYC OpenData was joined with [MapPLUTO](http://www1.nyc.gov/site/planning/data-maps/open-data/dwn-pluto-mappluto.page#mappluto) for each borough by `BBL`.
 2. The resulting shapefile contained 216 features and inspecting the sites for each library system we found 224 libraries. The missing "libraries" in the shapefile were found to be distinct library functions at locations that were already in the shapefiles, so we did not add these "libraries" to the data. (For example, Bedford Learning Center is a library service hosted at Bedford Library.) Find a full list of these under `Missing Libraries`.
 3. We added a new field, `public`, which is `yes` when the owner is public and `NULL` otherwise.
 4. We added a new field, `OwnerFixed`, which attempts to provide a more consistent owner name for each feature. Abbreviations were expanded, capitalization was fixed. This was only done for libraries on property that is publicly owned. Where multiple city agencies were listed in `OwnerName` (eg, "DCAS/DEPARTMENT OF ED"), we chose the agency that was more specific (eg, Department of Education).
 5. We edited some of the `name` fields. For example, some of the names from the original data indicate that the library is under renovation. Our edits ensure that `name` only contains names.
 6. Two libraries in Queens (Elmhurst and Kew Gardens Hills) were listed with their temporary locations. As we are only interested in their permanent locations the temporary locations were replaced with their permanent locations.

### Missing Libraries

These libraries were found on the websites of the library systems but are not included in this dataset as they are colocated with another library location in the dataset.

 * Brooklyn:
  * Bedford Learning Center
  * Business & Career Center
  * Eastern Parkway Learning Center
  * Flatbush Learning Center
  * New Lots Learning Center
 * Queens:
  * Central Library-Children's Library Discovery Center
  * Central Library-The Archives
  * Job Information Center
