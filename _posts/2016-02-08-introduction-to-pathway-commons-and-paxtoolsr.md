---
title: "Pathway Commons and paxtoolsr: An Introduction"
header:
  teaser: "post_teasers/abstract_network_900x450.jpg"
  image: "post_teasers/abstract_network_1600x450.jpg"
categories:
  - r
author: Augustin Luna  
---

[Pathway Commons](http://www.pathwaycommons.org/) is an aggregation of public pathway databases and provides infrastructure for querying this rich dataset. Pathway Commons databases include: BIND, BioGRID, CORUM, CTD, DIP, DrugBank, HPRD, HumanCyc, IntAct, KEGG, MirTarBase, Panther, PhosphoSitePlus, Reactome, RECON, TRANSFAC. [paxtoolsr](https://bioconductor.org/packages/release/bioc/html/paxtoolsr.html) is a package that builds on the strengths of Pathway Commons and its native [BioPAX](http://biopax.org/) format to provide a set of R functions for interacting with BioPAX OWL files using Paxtools and the querying Pathway Commons (PC) molecular interaction database that are hosted by the Computational Biology Center at Memorial Sloan-Kettering Cancer Center (MSKCC).

The slides below give a basic introduction to the [Pathway Commons](http://pathwaycommons.org/) database, including information about the aggregated databases, the number of the interactions in Pathway Commons, and the various file formats (e.g. BioPAX and gene sets as Gene Matrix Transposed (.gmt)) that are provided by Pathway Commons. It also describes how the rich content of these pathway databases is simplified into the Simple Interaction Format that is suitable for many research problems. Additionally, in provides a simple example on how to use the Pathway Commons data to conduct an integrative gene set enrichment analysis with cancer cell line data provided by the [CellMiner and the rcellminer R package](http://blog.lunean.com/2016/01/18/introduction-to-cellminer-and-rcellminer/). The example shows how to use a hypergeometric test to perform the enrichment analysis and then perform a multiple testing correction using the widely used Benjamini Hochberg False Discovery Rate (FDR) method. The elemental steps of this analysis are covered in the [Introduction to Statistical Methods in R](http://blog.lunean.com/2016/01/18/introduction-to-statistical-methods-in-r/).

{% include slides.html
  title="Pathway Commons and paxtoolsr"
  prefix="http://slides.lunean.com/uspWorkshop/pathwayCommons"
%}
