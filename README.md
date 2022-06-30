## Project overview

Do road and traffic characteristics influence the number of serious collisions in a surrounding area? Does the density of liquor resellers?  This project  explores these issues by fitting a generalized linear model via multiple linear regression. The model utilizes a conditional autoregressive (CAR) specification to account for spatially correlated errors of a continuous response, which in this case is the mean response of a poisson distribution conceptualized as a 2d surface.

## Primary language

R

## Highlighted visualizations

- (below) A visual review of the project's aggregation process.  Six panels, clockwise from the top left: (1) raw point processes of select variables of interest; (2) Areal units identified as inelligible for the modeling process because they exist outside the administrative boundary of the law enforcement agency which generated the dataset or because they lack public surface roads to experience recordable traffic collisions; (3) Areal aggregation of serious traffic collisions.  Serves as the project's response variable; (4) Areal aggregation of all traffic lights in the city; (5) Areal aggregation of all potholes in the city reported in the preceeding three years; (6) Areal aggregation of all liquor resellers in the city.

<img src="https://raw.githubusercontent.com/Jon-Does-Stats/project-spatial-poisson-collisons/main/figures/areal_aggregation_summary.png" width=900>

- (below) A visual review of the process mapping road condition indices to individual collisions. The Road condition indices are maintained by the city's public works department as a spatial lines object while automotive collisions are recorded by the city's police department, but only by address. To overcome this and align the road condition values with individual collisions, the visualization describes the transformation of the spatial lines object  into a spatial polygon object to circumscribe nearby traffic collisions. Note: because collision locations were recorded manually by street address or intersection, some records' latitude and longitude coordinates were not able to be pinpointed.  These edge cases are identified as partial matches by the geocoding service and are assigned arbitrary nearby coordinates, sometimes placing them in the ocean. A relatively low number of records fall into this category, and evidence is pursued in the analysis to classify them as missing at random before their removal.

<img src="https://raw.githubusercontent.com/Jon-Does-Stats/project-spatial-poisson-collisons/main/figures/road_condition_assignment.png" width=675>

- (below) Model residuals before and after accounting for spatial autocorrelation.  Notice the significant spatial patterning before implementing conditional autoregressive (CAR) random effects. 

<img src="https://raw.githubusercontent.com/Jon-Does-Stats/project-spatial-poisson-collisons/main/figures/spatial_dependence_illustrated.png" width=675>

- (below) Diagnostic plots of the HGLM-CAR model with all areal units included. 4 panels, clockwise from the top left: (1) Fitted values plotted vs. studentized residuals; (2) Fitted values plotted vs. absolute value of studentized residuals; (3) histogram of residuals; (4) a QQ plot.

<img src="https://raw.githubusercontent.com/Jon-Does-Stats/project-spatial-poisson-collisons/main/figures/diagnostics_full_dataset.png" width=675>

- (below) The two areal unit outliers with the observed collisions within their boundaries.

<img src="https://raw.githubusercontent.com/Jon-Does-Stats/project-spatial-poisson-collisons/main/figures/areal_unit_outliers.png" width=675>

- (below) Diagnostic plots of the HGLM-CAR model with the two areal unit outliers removed.  Note the change in scale, or axes limits, of these diagnostic plots compared to the preview set.  4 panels, clockwise from the top left: (1) Fitted values plotted vs. studentized residuals; (2) Fitted values plotted vs. absolute value of studentized residuals; (3) histogram of residuals; (4) a QQ plot.

<img src="https://raw.githubusercontent.com/Jon-Does-Stats/project-spatial-poisson-collisons/main/figures/diagnostics_outliers_removed.png" width=675>
