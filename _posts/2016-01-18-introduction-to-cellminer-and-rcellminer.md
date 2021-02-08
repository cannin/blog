---
title: "Introduction to CellMiner and rcellminer"
header:
  teaser: "post_teasers/petri_dish_drugs_900x450.jpg"
  image: "post_teasers/petri_dish_drugs_1600x450.jpg"
categories:
  - r
  - scitech
author: Augustin Luna  
---

The NCI-60 cancer cell line panel has been used over the course of several decades as an anti-cancer drug screen. This panel was developed as part of the [Developmental Therapeutics Program (DTP)](http://dtp.nci.nih.gov/) of the U.S. National Cancer Institute (NCI). Thousands of compounds have been tested on the NCI-60, which have been extensively characterized by many platforms for gene and protein expression, copy number, mutation, and others. The purpose of the [CellMiner](http://discover.nci.nih.gov/cellminer) project has been to integrate data from multiple platforms used to analyze the NCI-60 and to provide a powerful suite of tools for exploration of NCI-60 data.

The CellMiner project makes much of its work transparent in the community by providing data downloads for the datasets used by the project. The [rcellminer R package](https://www.bioconductor.org/packages/release/bioc/html/rcellminer.html) adds to this effort by providing additional functionality to help R users access the CellMiner data, including both NCI-60 molecular profiling and drug response data. The package allows programmatic access to CellMiner’s gene and protein expression, copy number, whole exome mutations, as well as activity data for ∼21K compounds, with information on their structure, mechanism of action and repeat screens. In addition to the provided data, R functions simplify the visualization of compound structures, drug compound activity patterns and molecular feature profile. Lastly, several web applications have been embedded into the rcellminer R package that allow interactive data exploration.

The presentation below gives a brief overview of both the CellMiner and rcellminer. One introductory topic covered in the presentation how users can use rcellminer to run a “pattern comparison” analysis to quickly identify genes that by gene expression, copy number alterations, etc. and/or compounds screened on the NCI-60 that significantly correlate with a user-defined pattern of interest over the NCI-60 (e.g. the presence of drug activity only in renal cell lines). The presentation also provides links to additional [rcellminer tutorial material](https://www.bioconductor.org/packages/release/bioc/vignettes/rcellminer/inst/doc/rcellminerUsage.html).

{% include slides.html
  title="CellMiner and rcellminer"
  prefix="http://slides.lunean.com/uspWorkshop/cellminer"
%}
