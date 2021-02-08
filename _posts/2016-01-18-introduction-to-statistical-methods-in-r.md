---
title: "Introduction to Statistical Methods in R"
header:
  teaser: "post_teasers/statistics_bayes_900x450.jpg"
  image: "post_teasers/statistics_bayes_1600x450.jpg"
categories:
  - r
author: Augustin Luna  
---

Data analyses are the product of many different tasks, and statistical methods are one key aspect of any data analysis. There is a common workflow in the related areas of informatics, data mining, data science, machine learning, and statistics. The workflow tasks include data preparation, the development of predictive mathematical models, and the interpretation and preparation of analysis results (including the development of visualizations to communicate findings).

The presentation provides information on the last two steps of this workflow and reproducible code examples and presents a walk-through of many common statistical methods (including regression, clustering (e.g. K-means and hierarchical), and dimensionality reduction (e.g. principal component analysis (PCA)) used to explore data with examples in R.

Novice users are shown how to navigate the resulting R object to extract specific elements of interest, such as correlation p-values, regression coefficients, etc. The presentation additionally tries to tackle of some of the key concerns about these introductory methods by providing guidance on the interpretation of analyses results, such as understanding the approximately 10 values returned in a simple linear regression; the importance of and how to [deal with missing values through imputation](http://bioconductor.org/packages/release/bioc/html/impute.html) in real world problems; determining the quality of clustering results; and understanding the data transformations that take place in dimension reduction methods. Also provided is information about more sophisticated methodologies, such as regularized regression methods: LASSO, Ridge, and Elastic Net regression, and packages to make use of these more advanced methods in R, such as [glmnet for regularized regression](https://cran.r-project.org/web/packages/glmnet/index.html).

Usage of these statistical methods for modeling can help users to understand their data sets, and these methodologies can be coupled with other aspects of [R and RStudio](http://blog.lunean.com/2016/01/17/introduction-to-r-and-rstudio/) to [develop interactive analyses using the Shiny R package](http://blog.lunean.com/2016/01/18/introduction-r-shiny/).

{% include slides.html
  title="Statistical Methods in R"
  prefix="http://slides.lunean.com/uspWorkshop/statisticalMethods"
%}
