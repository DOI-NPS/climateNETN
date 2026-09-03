# climateNETN
This package stores, compiles, summarizes and visualizes climate data for NETN park centroids. 
Package primarily relies on NOAA gridded climate data (see www.ncei.noaa.gov for more information), 
which include monthly gridded data from 1895 through to present day and 2 sets of normals- 1901 to 2000 (20th century), 
and 1991 to 2020 (30-year normal). Climate data are compiled for NETN park centroids. 
See <a href="https://katemmiller.github.io/waterNETN/"> https://katemmiller.github.io/waterNETN/</a> 
(user guide for both waterNETN and climateNETN) </a> for details on how to use the functions in this package.

The R package can be installed using `pak::pkg_install('doi-nps/climateNETN')`. Previous archived versions of this R package can be found at <a href="www.github.com/katemmiller/climateNETN">www.github.com/katemmiller/climateNETN</a>

This package includes the following functions: 
<ul>
<li>getClimDaymet: Download daily Daymet gridded climate data directly from REST</li>
<li>getClimDrought: Download weekly county-level drought index</li>    
<li>getClimNOAA: Download monthly gridded NOAA climate data</li>       
<li>getClimWStat: Download daily data from nearest weather station</li>      
<li>plotClimAnom: Plot climate anomalies from baseline normal</li>
<li>plotClimBar: Plot climate trends as bar plot</li>      
<li>plotClimComps: Plot climate comparisons between monthly historical normals and user-specified year</li>
<li>plotClimCumPrecip: Plot cumulative precipitation relative to historic normals</li>
<li>plotClimDrought: Plot weekly drought based on county-level drought index</li>
<li>plotClimRel: Plot climate data relative to average value from historic normals</li>
<li>plotClimTrend: Plot monthly climate trends for a given time period</li>
<li>sumStatsTable: Summarize monthly climate records</li>    
<li>theme_NETN: ggplot2 theme for climateNETN package</li>   
</ul>

The scripts/ folder contains scripts used to compile monthly climate statistics for each NETN park centroid using NOAA gridded cliamte data.
To update data for the the climate summary report, use the compile_NOAA_1895_present.R script. The last section of code is set up to update for
a new month.

The data/ folder stores data to make the functions run faster, including NETN centroids, NETN climate normals, NETN monthly climate data,
weekly drought statistics, closest weather station to each park, 

The docs/ folder includes the R Markdown files that generate the NETN climate summary. The index.Rmd generates the index.html, which is the 
file used by the gitpage for this repo. 

Steps to update the NETN climate summary for a new month:
<ol>
<li>Update NETN_drought_weekly.rda and NETN_clim_annual.rda by opening scripts/compile_NOAA_1895_present.R. 
Starting at line 67, update the month and year and rerun to end of script. It typically takes about 2 weeks for a new
month of data to be posted. You will receive an error that the data are not available for that time period if
the data have not been posted yet.</li>
<li>Rebuild the climateNETN package to update the data that installs with that package.</li>
<li>Update the params in docs/index.Rmd to cover the latest month of data. Note the end_date is also used
for the drought data.</li>
<li>Knit the index.Rmd, and check that the latest month was included.</li>
<li>Push the latest index.html, index.Rmd, and updated data files to github. A few minutes later the summary report should be updated.</li>
</ol>
