# TD1: Introduction to Spatial SQL

This guide provides a step-by-step walkthrough for installing PostGIS and setting up your first spatial database. PostGIS extends PostgreSQL to support advanced GIS operations directly within a relational database system.

## Prerequisites

- PostgreSQL installed on your system.
- Internet access to download necessary extensions and tools.

## Steps to Follow

### 1. Install PostgreSQL
1. Visit the [official PostgreSQL download page](https://www.postgresql.org/download/) and select the appropriate version for your operating system (Windows, macOS, or Linux).
2. Follow the installation instructions to set up PostgreSQL on your machine.
3. During installation, define a password for the `postgres` user.

### 2. Install PostGIS
1. During PostgreSQL installation, ensure you select all components, including the **Stack Builder** tool.
2. Launch Stack Builder after installation and select the PostgreSQL version you installed.
3. In the application list, choose **PostGIS** and complete the installation following the on-screen prompts.

### 3. Create Your First Spatial Database
1. Open **pgAdmin 4**, the PostgreSQL database management tool.
2. Connect to the PostgreSQL server using the credentials you set during installation.
3. Right-click on **Databases** and select **Create > Database**.
4. Assign a name to your database (e.g., `spatial_db`) and save it.
5. Open the **Query Tool** for your database and run the following command to enable PostGIS:
   ```sql
   CREATE EXTENSION postgis;
   ```
6. Verify the installation by searching for the `spatial_ref_sys` table under **Schemas > Public > Tables**.

## Next Steps

Once your spatial database is set up, you can proceed to creating tables with spatial columns and performing GIS operations using SQL. Check out **TD2** for more details on creating spatial tables.

## Resources

- [PostGIS Documentation](https://postgis.net/documentation/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
