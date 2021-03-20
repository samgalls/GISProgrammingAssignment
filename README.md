# GISProgrammingAssignment
GIS Programming Assignment for FB

1) <b>OSM Extract</b>
 <br />-Retrieved Large OSM Bulk Download from https://download.geofabrik.de/europe/great-britain.html
 <br />-Used the Select by Location tool to locate the detailed polygons in the bulk download associated with the 7mx7m squares in "location_polygons.kml"
 <br />-This selection extracted 12 unique polygons which I then exported to its own Shapefile (OSMSouthernUK.shp and other associated files)
 <br />-Extracted the Shapefile from the Selection to OSMSouthernUK.GEOJson and OSMSouthernUK.KML within QGIS
 <br />-Converted OSMSouthernUK.KML to OSMSouthernUK.KMZ using a web based conversion tool located at https://mygeodata.cloud/converter/kml-to-kmz

2) <b>Polygon Updates</b>
<br />-In the OSMSouthernUK File created poly_Name field and populated with the associated/intersecting location_polygons name ("name" attribute) i.e. LHR2, EU-UK-NEWB etc.
<br />-For EU-UK-CLFT, Merged 2 OSM Polygons together as they shared a common boundary and the EU-UK-CLFT 7x7 polygon resides in both polygons equally. After back checking Google Earth, there appears to be one building/complex despite the OSM file having them as separate entities, thus the merge reflects the actual building.
<br />-Now the OSMSouthernUK File is composed of 11 polygons (rather than 12)
<br />-Deleted LHR4 from OSMSouthernUK as LHR2 (despite not being in the exact same location) intersects the same building polygon.
<br />-The remaining 12 location_polygons polygons did not intersect any buildings within the OSM File. Thus they must be associated with buildings not included in the dataset. So  I uploaded the remaining polys into Google Earth by KML File and then manually adjusted the boundaries of each poly to match those of the building it was located upon.
<br />-Deleted one of the EU-UK-CPHM 7x7 Polygons as they were identical, leaving 11 Polygons that need to be manually updated.
<br />-Extracted the new OSMSouthernUKManual.KML file from Google Earth, converted to OSMSouthernUKManual.GEOJson (for functionality)
<br />-Merged OSMSouthernUKManual.GEOJson with OSMSouthernUK.GEOJson thus creating one file with all 22 Updated Polygons, Location_PolygonsFINAL
<br />-Using Field Calculator, autofilled height for all 22 Polygons with "30" (per Siv) due to lack of data availability

3) <b>Line</b>
<br />-The Line file is a multilinestring feature composed of three lines. The Line appears to be a "Dark Fibre" line according to the 'type' field in the attribute table.
<br />-The issue with the multilinestring is that it has several  locations on the line where 1, 2, or even all 3 of the line sections break off and disconnect from the rest of its coinciding line
<br />-This could cause problems if it's being used to represent a utility conduit because continuity is obviously a very important part of utility lines. Therefore, a large area with essentially a dead zone of sorts with no representation of a conduit would be an issue in maintaining connections especially in the case of long spanning fiber optics lines.
<br />-As of 8:00 PM on 3/19/21 I haven't yet found a way to fix the gaps in the stringline feature. Although using the Topology Checker Tool in QGIS I have determined that there are 825 "dangling ends" throughout the stringline.
