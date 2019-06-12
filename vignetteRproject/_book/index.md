--- 
title: 'mixOmics vignette'
author: 'Kim-Anh Le Cao, Sebastien Dejean, Al J Abadi'
package: mixOmics
date: '\today'
site: bookdown::bookdown_site
output: 
  bookdown::gitbook
  BiocStyle::html_document
documentclass: book
bibliography: ["mybib.bib"]
biblio-style: apalike
link-citations: true
github-repo: mixOmicsTeam/mixOmics
description: "Vignette for the R package mixOmics"

header-includes:
  - \usepackage{color}
  
---

# Preface {-}

`mixOmics` is an R toolkit dedicated to the exploration and integration of biological data sets with a specific focus on variable selection. The package currently includes nineteen multivariate methodologies, mostly developed by the `mixOmics` team (see some of our references in \@ref(intro:pubs)). Originally, all methods were designed for omics data, however, their application is not limited to biological data only. Other applications where integration is required can be considered, but mostly for the case where the predictor variables are continuous (see also \@ref(intro:datatypes)). 
