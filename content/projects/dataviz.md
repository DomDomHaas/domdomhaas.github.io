
### ICP Forest Defoliation


I have also enjoyed making the visualization of the defoliation of forests, based on European research data form ICP Forest Program. I liked the combination of map and chart visualization. The project had an additionally challenge the data could not be published at the time, therefore I have rendered multiple images to create an animation as gif file.

![ICP Forest Defoliation](/images/projects/envidat/icp_forest_defoliation_1990-2022.gif)
<small><a href="https://envidat.ch/#/metadata/icp-forests-defoliation-and-symptoms-data-set" target="_blank">ICP Forest Defoliation 1990-2022</a></small>


### Dataset Publication Report

The Dataset Publication Report provides a history of the dataset published on EnviDat. I've prototyped with an [observable notebook](https://observablehq.com/@domdomhaas/envidat-dataset-publication-report) and later integrated into EnviDat: https://envidat.ch/#/organizations. This is a form of dashboard, not with the focus of a single user but of a research unit. Therefore, the chart at the top show the history datasets grouped by research units, further down is a list of the organizations which have datasets on EnviDat. The list will be extended when one is selected not only the datasets are shown in the list but also the publication history in a chart.


![Dataset Publication Report](/images/projects/envidat/dataviz_organizations.webp)
<small><a href="https://envidat.ch/#/organizations" target="_blank">Dataset Publication Report visualization</a></small>


### Greenland Climate Network on EnviDat


In the first years of EnviDat we made a specific implementation for the [Greenland Climate Network on EnviDat](https://envidat.ch/#/metadata/gcnet). The data was pulled from satellites, process and stored in a PostgreSQL DB, accessible via Django API, visualized by the vue.js frontend. There were two use cases: first station status, to quickly see if station is online and recent data comes in. The second a detailed view of the different parameters per station. With a click on the chart-icon a full screen view opens and visualizes parameters of a station as timelines. (Only historical data is available by now, since the project is continued by GEUS [https://doi.org/10.22008/FK2/VVXGUT](https://doi.org/10.22008/FK2/VVXGUT) ).



### GenDib Metadata Portal

GenDib is a metadata portal which links the locations on the map with the paper and data entries. As it has similarities with EnviDat, I've supported their software engineer, specifically for the filtering functionalities and the usage of openlayers for the visualizations on the map.


![GenDib Metadata Portal](/images/projects/envidat/dataviz_gendib.webp)
<small><a href="https://gendib-srv.wsl.ch/" target="_blank">GenDib Metadata Portal as WSL</a></small>
