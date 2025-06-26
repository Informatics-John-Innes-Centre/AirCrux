# AirCrux
  AirCrux is a list of technical challenges, limitations, and unresolved issues faced by researchers using drones for plant phenomics in the UK.

NOTE Initial commit made from a brain dump and ChatGPT to flesh it out. Nonsense needs to be fixed.

## Workflow: Current Aerial Data Capture workflow

### Flight & Data Capture

- **Pre-Flight Planning**
  - Define survey area and flight parameters (altitude, overlap, speed).
  - Use a flight planning app to ensure complete coverage.
  - Schedule flights under consistent lighting (preferably mid-morning).

- **Reflectance Panel Calibration**
  - Place the reflectance panel on flat, unobstructed ground before the flight.
  - Take at least one image of the panel with the multispectral camera.
  - Ensure panel is clean and well lit (not in shadow).

- **Flight Execution**
  - Launch and fly the drone over the survey area using predefined flight plan.
  - Capture multispectral images (e.g., Red, Green, NIR).
  - Optionally, take a sky image for irradiance correction if supported.

---

### Processing in Pix4D

- **Import and Setup**
  - Create a new project and load captured images.
  - Select the **Ag Multispectral** template.

- **Reflectance Calibration**
  - Include reflectance panel image for radiometric correction.
  - Verify that the panel is correctly identified and calibrated.

- **Processing**
  - Run Steps 1, 2, and 3 to generate:
    - Georeferenced orthomosaics
    - Reflectance maps for each band
    - Vegetation index layers (e.g., NDVI)

- **Export Outputs**
  - Export NDVI and reflectance maps as GeoTIFF files.

---

### Data Analysis in QGIS (Zonal Statistics)

- **Load Data**
  - Open QGIS and import:
    - NDVI GeoTIFF raster
    - Polygon shapefile (e.g., field plots or zones)

- **Coordinate System Check**
  - Ensure both raster and vector layers use the same CRS.

- **Zonal Statistics Calculation**
  - Open **Zonal Statistics** from the Processing Toolbox.
  - Select:
    - Input raster layer: NDVI map
    - Input vector layer: plot boundaries
  - Choose statistics to calculate (mean, median, std. dev., etc.)
  - Run the tool to append NDVI values to each polygon.

- **Export Results**
  - Save the updated shapefile or export the attribute table to CSV for reporting.

---

### Summary

This workflow allows you to capture multispectral imagery using a drone, process it with Pix4D to generate NDVI maps, and extract statistical insights using QGIS for site-specific analysis or reporting.



## Issues

For detailed technical challenges and feature requests, see [docs/issues.md](docs/issues.md).
