🚀 Step 1: Creating a Spatial Table (Points)
📋 SQL Command
Run the following SQL command in pgAdmin to create a points_of_interests table with a Point geometry column:

CREATE TABLE points_of_interests (
  id SERIAL PRIMARY KEY,
  nom VARCHAR(255),
  geom GEOMETRY(Point, 4326)
);
🛠️ Using QGIS to Insert Data
Open QGIS and establish a connection to your database:
Right-click PostgreSQL in the Explorer panel.
Select New Connection, then input the required details and test the connection.
Add the points_of_interests table as a layer:
Double-click the table to load it as a layer.
Switch to Edit Mode:
Add some points on the map.
Save your changes.
🔍 Verifying Data
In pgAdmin, execute the following query to view the data:

SELECT * FROM points_of_interests;
🚀 Step 2: Creating a Spatial Table (Polygons)
📋 SQL Command
Run this SQL command in pgAdmin to create a zones_protegees table with a Polygon geometry column:

CREATE TABLE zones_protegees (
  id SERIAL PRIMARY KEY,
  nom VARCHAR(255),
  geom GEOMETRY(Polygon, 4326)
);
🛠️ Using QGIS to Insert Data
Follow the same steps as in Step 1 to load the zones_protegees table in QGIS.
Draw polygons on the map in Edit Mode and save your changes.
🔍 Verifying Data
In pgAdmin, execute the following query to view the data:

SELECT * FROM zones_protegees;
🚀 Step 3: Creating a Spatial Table (LineStrings)
📋 SQL Command
Run this SQL command in pgAdmin to create a routes table with a LineString geometry column:

CREATE TABLE routes (
  id SERIAL PRIMARY KEY,
  nom VARCHAR(255),
  geom GEOMETRY(LINESTRING, 4326)
);
🛠️ Using QGIS to Insert Data
Load the routes table in QGIS.
Draw lines on the map in Edit Mode and save your changes.
🔍 Verifying Data
In pgAdmin, execute the following query to view the data:

SELECT * FROM routes;
🛠️ Using QGIS to Insert Data
For all spatial tables:

Connect to the PostgreSQL database in QGIS.
Load the desired table as a layer.
Switch to Edit Mode and add spatial data (points, polygons, or lines).
Save the changes to persist data in the database.
🏁 Summary
After completing these steps, you will have:

Created three spatial tables (points_of_interests, zones_protegees, routes) with different geometry types.
Populated them with data using QGIS.
Verified the data using SQL queries in pgAdmin.
Feel free to extend these examples for more complex spatial operations! 🚀