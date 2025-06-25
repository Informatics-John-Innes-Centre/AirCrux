# Technical Issues in Drone-Based Plant Phenomics

This page documents key technical challenges reported by the UK plant phenomics community related to drone-based workflows.

---

## 1. PPK Processing of TIFF Images

**Problem:**  
Post-processed kinematic (PPK) workflows are typically optimized for JPEG outputs from drones. However, many scientific workflows require georeferenced TIFF images (e.g., for multispectral or high-resolution RGB data). Converting PPK data to correctly geotag TIFFs can be cumbersome or poorly documented, with toolchains often lacking support for direct integration.

**Needs:**  
- Open tools or workflows that support direct PPK tagging of TIFF images  
- Guidance on aligning EXIF-based corrections with TIFF metadata standards  
- Better documentation and support from vendors on exporting imagery compatible with research-grade processing  

---

## 2. Calibrating Drone Data Using Reflectance Panels in OpenDroneMap

**Problem:**  
While OpenDroneMap (ODM) supports basic radiometric calibration, workflows for using reflectance panels (e.g., with known surface reflectance values) are not well supported or clearly documented. This makes it difficult to normalize data across time or sites for phenomics studies.

**Needs:**  
- Support in ODM for automated or semi-automated panel-based calibration  
- Community guidance or scripts for integrating reflectance panel data into processing  
- Validation tools to check whether calibration has improved data quality

- ---

## 3. Creating KML Files for Targeted Flight Plans in DJI Drones

**Problem:**  
Researchers often need to capture close-up images of individual 2x4m field plots, separate from broader mapping missions. This requires generating a KML file from QGIS with points at the center of each plot, which can be used to guide a DJI drone to take targeted photos at lower altitudes. However, translating QGIS output into a DJI-compatible KML format—especially with proper coordinate precision and altitude settings—is error-prone and poorly documented.

**Needs:**  
- Clear workflow for generating correctly formatted KML files in QGIS  
- Ability to set custom flight altitudes for individual waypoints  
- Compatibility guidance for importing KMLs into DJI flight planning tools (e.g., DJI GS Pro, DJI Pilot 2)  
- Example templates or scripts to simplify this process for repeated trials


---

## 4. Automatically Generating Shapefile Polygons Around Field Trial Plots

**Problem:**  
Creating accurate plot-level shapefiles (e.g. 2x4 m rectangles) over field trials is a repetitive and error-prone task when done manually. Automating this step—especially when trial designs are regular (grid-based) or have known metadata (e.g., plot IDs, row/column structure)—would save time and improve consistency across trials and teams.

**Needs:**  
- Tools or scripts that can generate plot polygons based on trial layout parameters (e.g., number of rows/columns, plot size, buffer width)  
- Integration with QGIS or other GIS platforms  
- Ability to align generated plots with field boundaries or drone imagery using reference points or georeferenced basemaps  
- Support for exporting directly to shapefile/GeoJSON with plot IDs and metadata embedded

**Bonus:**  
- GUI or user-friendly interface for non-programmers  
- Ability to import CSV layout plans and generate polygons automatically  

---

## 5. Mapping AI-Derived Results from Raw Drone Imagery Back to Plot-Level Data

**Problem:**  
High-resolution drone frames (raw images) often capture crop features—like wheat heads or lodging—with much greater clarity than stitched orthomosaics, which can suffer from motion blur or stitching artifacts, especially in windy conditions. However, most downstream analysis pipelines (e.g., spatial statistics, phenotypic summaries) expect data aligned to orthomosaics or plot shapefiles.

This creates a disconnect: results derived from individual frames (e.g. using AI models for wheat head detection) need to be mapped or projected back into a geospatial context that matches the trial layout.

**Needs:**  
- Methods to geolocate detections from raw images and assign them to field plots  
- Tools to project detections into a common spatial coordinate system without requiring a stitched mosaic  
- Integration with standard shapefiles or plot layouts to enable summary statistics per plot  
- Solutions that account for drone orientation, lens distortion, and altitude metadata to improve accuracy

**Bonus:**  
- Frameworks that let users train/validate models on raw images and still export orthomosaic-style plot summaries  
- Examples or case studies demonstrating this approach in real-world trials
