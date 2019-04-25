


# Let's get started {#start}

## Installation
First, download the latest \texttt{mixOmics} version from Bioconductor:

```r
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
 BiocManager::install("mixOmics")
```

Alternatively, you can install the *latest* development version of the package from Github.

```r
install.packages("devtools")
# then load
library(devtools)
install_github("mixOmicsTeam/mixOmics")
```

The `mixOmics` package should directly import the following packages: `igraph, rgl, ellipse, corpcor, RColorBrewer, plyr, parallel, dplyr, tidyr, reshape2, methods, matrixStats, rARPACK, gridExtra`. For *apple mac users*, if you are unable to install the imported library `rgl`, you will need to install the [XQuartz software](https://www.xquartz.org) first.

## Load the package {#start:upload}

```r
library(mixOmics)
```

Check that there is no error when loading the package, especially for the `rgl` library (see above).

## Upload data
The examples we give in this vignette use data that are already part of the package, *which means that the objects are stored as list. However, you do not need to store your data as list, just data frames will do*. To upload your own data, check first that your working directory is set, then read your data from a  `.txt` or `.csv` format, either by using **File > Import Dataset** in RStudio (*although be mindful this option may pose problem with row and col name headers*) or via one of these command lines:


```r
# from csv file
data <- read.csv("your_data.csv", row.names = 1, header = TRUE)

# from txt file
data <- read.table("your_data.txt", header = TRUE)

# then, in the argument in the mixOmics functions, just fill with:
# X = data
```

For more details about the arguments used to modify those functions, type `?read.csv` or `?read.table` in the R console.

## Quick start in `mixOmics` {#start:PCA}

Each analysis should follow this workflow:

1. Run the method
2. Graphical representation of the samples
3. Graphical representation of the variables

Then use your critical thinking and additional functions and visual tools to make sense of your data! (some of which are listed in \@ref(intro:overview)) and will be described in the next Chapters.

For instance, for Principal Components Analysis, we first load the data:

```r
data(nutrimouse)
X <- nutrimouse$gene
```


Then use the following steps:

```r
MyResult.pca <- pca(X)  # 1 Run the method
plotIndiv(MyResult.pca) # 2 Plot the samples
```

<img src="Figures/unnamed-chunk-6-1.png" width="50%" style="display: block; margin: auto;" />

```r
plotVar(MyResult.pca)   # 3 Plot the variables
```

<img src="Figures/unnamed-chunk-6-2.png" width="50%" style="display: block; margin: auto;" />


This is only a first quick-start, there will be many avenues you can take to deepen your exploratory and integrative analyses. The package proposes several methods to perform variable, or feature selection to identify the relevant information from rather large omics data sets. The sparse methods are listed in the Table in \@ref(intro:overview).

Following our example here, sparse PCA can be applied to select the top 5 variables contributing to each of the two components in PCA. The user specifies the number of variables to selected on each component, for example here 5 variables are selected on each of the first two components (`keepX=c(5,5)`): 


```r
MyResult.spca <- spca(X, keepX=c(5,5)) # 1 Run the method
plotIndiv(MyResult.spca)               # 2 Plot the samples
```

<img src="Figures/unnamed-chunk-7-1.png" width="50%" style="display: block; margin: auto;" />

```r
plotVar(MyResult.spca)                 # 3 Plot the variables
```

<img src="Figures/unnamed-chunk-7-2.png" width="50%" style="display: block; margin: auto;" />

You can see know that we have considerably reduced the number of genes in the `plotVar` correlation circle plot.


Do not stop here! We are not done yet. You can enhance your analyses with the following:

- Have a look at our manual and each of the functions and their examples, e.g. `?pca`, `?plotIndiv`, `?sPCA`, ... 

- Run the examples from the help file using the `example` function: `example(pca)`, `example(plotIndiv)`, ...

- Have a look at out [website](http://www.mixomics.org) that features many tutorials and case studies,

- Keep reading this vignette, this is *just the beginning!*

