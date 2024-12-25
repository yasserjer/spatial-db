🗺️ TD-3: SQL Spatial Functions

📚 Exercise Objective

Determine how many parcels are located within 1 km of a fire point.

To explore the ST_xxxx functions, refer to the PostGIS Documentation.

🚀 Context

In this exercise, you will use PostGIS to determine how many parcels in Florida are within a 1 km radius of a fire point, which is defined as the centroid of a given parcel. You will use the shapefile of Florida parcels available online.

🚀 Exercise Steps

1. Import the Shapefile into PostGIS

Download the shapefile.

Open the PostGIS Shapefile Import/Export Manager:

On Windows, press the Windows key, then type "shap" to locate the PostGIS Shapefile Import/Export Manager.

Select your shapefile for Florida parcels.

Import it into a PostgreSQL table.

2. Verify Parcel Data

Execute the following query in pgAdmin to count the total number of parcels:

SELECT count(*) FROM parcels;

Answer: This query returns the total number of parcels in the table.

3. Select the Fire Point (Centroid of Parcel 462273)

Use the following query to find the centroid of the parcel with GID 462273:

SELECT ST_Centroid(geom) AS fire_point
FROM parcels
WHERE gid = 462273;

Answer: This query returns the centroid (fire point) of parcel 462273, which will serve as the reference fire point.

4. Risk Zone Within a 1 km Radius of the Fire Point

In QGIS:

Duplicate the parcel layer and rename it to fire-risk.

Right-click on the layer and select "Filter".

Apply the Filter:

Use the following WHERE clause in the filter expression section:

ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000);

Note: QGIS filter does not expect the first part (SELECT * FROM parcels). Omitting this will result in an error.

Adjust Layer Symbology:

Change the symbology of the fire-risk layer to visually represent the fire risk zones.

Add Another Fire Point (Parcel 460957):

Modify the filter to include both zones by adjusting the query as follows:

ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 1000);

5. Develop Spatial SQL Queries

How many parcels are located within 1 km of both target parcels (GID = 460957 and 462273)?

SELECT count(*) 
FROM parcels 
WHERE ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);

Answer: This query returns the number of parcels within 1 km of either parcel 462273 or 460957.

What is the total area of parcels near the fire?

SELECT SUM(ST_Area(geom)) 
FROM parcels 
WHERE ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
OR ST_DWithin(geom, 
  (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);

Answer: This query calculates the total area of all parcels within 1 km of the fire points.