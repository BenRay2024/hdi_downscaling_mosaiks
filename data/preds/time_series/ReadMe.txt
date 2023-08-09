 # ReadMe.txt # 
 
 TIME SERIES

 Global High Resolution Estimates of the Human Development Index, Version 1.0

## BACKGROUND ON TIME SERIES

We have produced global downscaled estimates of HDI for 2012-2021
by combining existing provincial measures with fine-resolution satellite estimates. 

These values represent our current best estimate of subnational HDI, and are 
appropriate for applications comparing levels of HDI across locations within a 
specific moment in time.  However, these estimates should *not* be used for comparing 
trends in HDI across locations within a province. Doing so would not be fruitful as 
we do not allow the estimated within-province pattern of HDI to vary over time. 

Robust evaluation of our downscaling performance over time is limited by the 
availability of time-series validation data, and experiments indicate that current 
data does not allow us to distinguish performance between our validated approach 
and an approach that estimates local trends in HDI.



GitHub github.com/Global-Policy-Lab:/hdi_downscaling_mosaiks
Email: lsherman@berkeley.edu



## TIME SERIES RASTER DATA
Layer 1: 		HDI Grid Level Estimates for the given year
					- These are the predictions generated from the machine learning model 
					  combining MOSAIKS daytime image and nightlight (NL) features
					  
					- These predictions are clipped to have values that fall within 0 and 1.
					
					- These estimates are centered such that the population-weighted average
					   of the 0.01 x 0.01 degree tile HDI estimates matches the ADM1 data
					   from Smits and Permanyer for the given year (https://globaldatalab.org/shdi).
					   
					- Population density weights come from the Gridded Population of the 
					  World (GPW) V4 (https://sedac.ciesin.columbia.edu/data/collection/gpw-v4).
					  
					- We also use a more precise population mask to ensure we only release 
					estimates where human settlements are known to exist. To do this, we 
					mask our raw model predictions using data from the Human Settlement
	 					Data Layer (at https://ghsl.jrc.ec.europa.eu/).


resolution: 		0.1 x 0.1 degree
no data value:		numpy.nan
raster extent:		[-180,180, -56, 74]





## TIME SERIES TABULAR DATA
Tablular data can be merged with the ADM2 administrative geojson from geoBoundaries 
available here: 
https://www.geoboundaries.org/data/geoBoundariesCGAZ-3_0_0/ADM2/simplifyRatio_100/geoBoundariesCGAZ_ADM2.geojson

Columns:

predicted_adm2_HDI_{year}			- Estimated HDI deviations from the country mean that have been mean-anchored 
						  to the provincial (ADM1) values for the year.

shapeID						- Unique identifier for each ADM2 unit from geoBoundaries
							
	
	
