---
title: "CBioPortal and cgdsr: An Introduction"
header:
  teaser: "post_teasers/cbioportal_900x450.jpg"
  image: "post_teasers/cbioportal_1600x450.jpg"
categories:
  - r
author: Augustin Luna  
---

The [cBio Cancer Genomics Portal](http://cbioportal.org/) is an open-access resource for interactive exploration of multidimensional cancer genomics data sets, currently providing access to data from more than 100 cancer studies. The cBio Cancer Genomics Portal significantly lowers the barriers between complex genomic data and cancer researchers who want rapid, intuitive, and high-quality access to molecular profiles and clinical attributes from large-scale cancer genomics projects and empowers researchers to translate these rich data sets into biologic insights and clinical applications.

The slides below preview many of the website features found on the CBioPortal website, including view genomic alterations as [oncoprints](http://www.cbioportal.org/faq.jsp#what-are-oncoprints) (a compact way of viewing genomic alterations across a large number of study patients), viewing study summaries, and accessing details patient data, such as, histology images and pathology reports. Additionally, the slides provide introductory material for the usage of CBioPortal from R using the cgdsr package. cgdsr simplifies access to the [web application programming interface (API)](http://www.cbioportal.org/web_api.jsp) provided by the project. This is a REST-based API, that allows software to query the database using parameters appended onto the URL. Using the cgdsr package mirrors closely the way a user would manually interact with the CBioPortal website by searching and selecting the cancer studies of interest, the genetic profiles for a given study, and the case sets for the cancer study.

FIXME: cBioPortal: http://slides.lunean.com/uspWorkshop/cbioportal
