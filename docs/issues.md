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

