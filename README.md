# PG-Inventory
PG-Inventory is a GIS toolbox developed in ArcGIS Pro to help divide paleoglacier outlines based on their drainage areas and generate basic and derived attributes of paleogalcier outlines. The toolbox includes three tools: 1) divide glacier outlines for watersheds; 
2) add basic glacier attributes, and 3) add derived attributes for palaeoglaciers. All these tools are written with Python in ArcGIS Pro with a user-friendly interface that allows users to process a large set of data.

![image](https://github.com/user-attachments/assets/b12b03ae-a40e-4f7b-8304-2a514114e7e1)

## Divide glacier outlines for watersheds 
The ‘Divide glacier outlines for watersheds’ tool divides the (paleo)glacier outlines based on drainage areas. The inputs of this tool include a digital elevation model (DEM), an input glacier outline (polygon) file,
and a minimum elevation range (relief) to form a glacier. The program uses several hydrological tools, including fill (fill sinks), flow direction, and basin functions to derive all drainage basins within each glacial 
outline. Then, the elevation range (local relief) for each drainage basin is calculated and the basins with less elevation ranges than the specified minimum elevation range are gradually merged to their touched drainage 
basins with greater elevation ranges than the specified minimum elevation range. This step is repeated until all basins with small elevation ranges are merged to their nearby basins with large elevation range. 
The output of this tool is the divided glacier outlines. Note that manual check and adjustment are needed to ensure the quality of the divided glacier outlines. 

![image](https://github.com/user-attachments/assets/3e4c3099-df19-4698-8353-9c6cbad3d676)

## Add basic glacier attributes
The ‘Add basic glacier attributes’ tool generates the basic paleoglacier attributes (Fig. 2b). The inputs of this tool include the divided glacier outlines, the glacial stage of the outline, an (optional) age point file, 
dating method, the age field name, and the ICED SiteID if the age point file is derived from the ICE-D dataset. This tool first generates a PGI_ID based on the glacial stage and the latitude and longitude of the centroid 
of each outline (polygon) and then derives attributes listed in Table 1. If the age point file is provided, this tool will also generate the age-related attributes in Table 1. Note that this tool only creates fields but 
does not fill the attributes that require manual input. The users need to manually input these fields.

![image](https://github.com/user-attachments/assets/13605d94-0b46-4cc8-8073-2abb0e63dc4c)
 

## Add derived glacier attributes
The ‘Add derived glacier attributes’ tool generates the derived attributes of palaeoglaciers (Fig. 2c). The inputs of this tool include the divided glacier outlines, the reconstruction method, the reconstructed ice surface 
raster, and the reconstructed ice thickness raster for paleoglaciers. Other inputs also include the elevation bins for AAR and AABR methods to calculate the ELAs and the AAR and AABR ratios. This tool derived all attributes 
listed in Table 2 based on provided reconstruction method, ice surface and ice thickness rasters. The methods to derive A3D, R3d2D, Z_min, Z_max, Z_range, Z_mean, Z_mid, Mean_slope, Mean_aspect, Hypsomax, and HI are based 
on the methods described in Li et al. (2024). The mean, std, median and max thickness are derived based on zonal statistics of the ice thickness raster for each paleoglacier outline. This tool also incorporates the four 
methods described in (Pellitero et al. 2015) to derive the ELA of the palaeoglacier, MGE, AAR, AA, and AABR. The Accumulation Area Ratio (AAR) method determines the ELA based on the ratio between the accumulation area and 
the total surface of a glacier. In the absence of a regional/local value, a recent study by Oien et al. (2021) recommended to use the global median and mean value of 0.58. The Area-Altitude Balance Ratio (AABR) method 
considers the distribution of glacier hypsometry with more weight to elevations furthest from the ELA. It is a more advanced and robust method (Osmaston, 1975; Furbish and Andrews, 1984; Oien et al., 2021). 
Oien et al. (2021) recommended the use of a global median value of 1.56 for AABR calculation. The Area-Altitude (AA) method is a simplified version of the AABR method, with an area-altitude balance ratio of 1, in which 
the ELA corresponds to its area-weighted median elevation. The Mean Glacier Elevation (MGE) method uses the mean elevation of a glacier to represent the ELA. These methods require an elevation bin for calculation. The 
default values for this tool are an elevation bin of 20 m, an AAR ratio of 0.58, and an AABR ratio of 1.56.

![image](https://github.com/user-attachments/assets/66f42062-f233-4420-ad5f-dd5bd93ef6ca)

