# GISProgrammingAssignment
GIS Programming Assignment for FB

1) OSM Extract
 <br />-Retrieved Large OSM Bulk Download from https://download.geofabrik.de/europe/great-britain.html
 <br />-Used the Select by Location tool to locate the detailed polygons in the bulk download associated with the 7mx7m squares in "location_polygons.kml"
 <br />-This selection extracted 12 unique polygonsn which I then Extracted to its own Shapefile (OSMSouthernUK.shp and other associated files)
 <br />-Extracted the Shapefile from the Selection to OSMSouthernUK.GEOJson and OSMSouthernUK.KML within QGIS
 <br />-Converted OSMSouthernUK.KML using an internet converter located at https://mygeodata.cloud/converter/kml-to-kmz

2) Polygon Updates
<br />-In the OSMSouthernUK File created poly_Name field and populated with the associated/intersecting location_polygons name ("name" attribute)
<br />-For EU-UK-CLFT, Merged 2 OSM Polygons together as they shared a common boundary and the EU-UK-CLFT 7x7 polygon resides in both polygons equally. After back checking Google Earth, there appears to be one building/complex despite the OSM file having them as seperate entities, thus the merge reflects the actual building.
<br />-Now the OSMSouythernUK File is composed of 11 polygons (rather than 12)
<br />-Deleted LHR4 from Location_PolygonsFINAL as LHR2 (despite not being in the exact same location) intersects the same building polygon.
<br />-The remaining 12 location_polygons polygons did not intersect any buildings within the OSM File. Thus they must be associated with buildings not included in the dataset. So  I uploaded the remaining polys into Google Earth by KML File and then manually adjusted the boundaries of each poly to match those of the building it was located upon.
<br />-Deleted one of the EU-UK-CPHM 7x7 Polygons as they were identical, leaving 11 Polygons that need to be manually updated.
<br />-Extracted the new OSMSouthernUKManual.KML file from Google Earth, converted to OSMSouthernUKManual.GEOJson (for functionality)
<br />-Merged OSMSouthernUKManual.GEOJson with OSMSouthernUK.GEOJson thus creating one file with all 22 Updated Polygons
<br />-Using Field Calculator, autofilled height for all 22 Polygons with "30" (per Siv) due to lack of data availability

3) Line
<br />-
