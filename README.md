# GISProgrammingAssignment
GIS Programming Assignment for FB

1) OSM Extract
 -Retrieved Large OSM Bulk Download from https://download.geofabrik.de/europe/great-britain.html
 -Used the Select by Location tool to locate the detailed polygons in the bulk download associated with the 7mx7m squares in "location_polygons.kml"
    -This selection extracted 12 unique polygonsn which I then Extracted to its own Shapefile (OSMSouthernUK.shp and other associated files)
 -Extracted the Shapefile from the Selection to OSMSouthernUK.GEOJson and OSMSouthernUK.KML within QGIS
 -Converted OSMSouthernUK.KML using an internet converter located at https://mygeodata.cloud/converter/kml-to-kmz
