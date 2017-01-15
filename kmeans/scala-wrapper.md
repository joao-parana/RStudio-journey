Scala Wrapper
================
João Antonio Ferreira
15 de janeiro de 2017

-   [R Markdown](#r-markdown)
-   [Preparação do ambiente](#preparacao-do-ambiente)
    -   [Lendo o Dataset](#lendo-o-dataset)
    -   [Investigando no grafico](#investigando-no-grafico)
    -   [Rodando o KMeans para k = 8](#rodando-o-kmeans-para-k-8)

R Markdown
----------

Este é um documento R Markdown. Markdown é um formato simples para gerar documentos HTML, DOCX e PDF.

Preparação do ambiente
----------------------

Preparando o ambiente para rodar o KMeans da implementação R com o mesmo dataset da implementação Spark

``` r
options(max.print=50)
```

``` r
remove.packages(c("ggplot2", "data.table"))
install.packages('ggplot2', dep = TRUE)
install.packages('data.table', dep = TRUE)
```

### Lendo o Dataset

``` r
myOriginalDataset <- read.delim('/data/prepared-3D_spatial_network.csv', header = TRUE, sep = ',') 
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 3.3.2

### Investigando no grafico

``` r
altPlot <- qplot(longitude, latitude, data = myOriginalDataset, colour = altitude)
altPlot
```

![](geo-plus-altitude.png)

### Rodando o KMeans para k = 8

``` r
myDataset = as.matrix(cbind(myOriginalDataset$latitude, myOriginalDataset$longitude), ncol=2)
cl = kmeans(myDataset, 8)
cl_factor = factor(cl$cluster)
cl
```

    ## K-means clustering with 8 clusters of sizes 84660, 90422, 86264, 127728, 88248, 141874, 78036, 172526
    ## 
    ## Cluster means:
    ##       [,1]      [,2]
    ## 1 56.87691  8.499683
    ## 2 56.94205  9.308417
    ## 3 56.76062  9.690166
    ## 4 57.44926 10.555215
    ## 5 56.85911 10.146987
    ## 6 57.41014 10.093987
    ## 7 56.82915  8.885834
    ## 8 57.11217  9.842111
    ## 
    ## Clustering vector:
    ##  [1] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
    ## [36] 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
    ##  [ reached getOption("max.print") -- omitted 869708 entries ]
    ## 
    ## Within cluster sum of squares by cluster:
    ## [1] 3356.690 3502.066 2718.040 8757.847 3296.953 5482.231 2908.934 5640.036
    ##  (between_SS / total_SS =  91.4 %)
    ## 
    ## Available components:
    ## 
    ## [1] "cluster"      "centers"      "totss"        "withinss"    
    ## [5] "tot.withinss" "betweenss"    "size"         "iter"        
    ## [9] "ifault"

Os 8 centroides encontrados.

``` r
# myDataset$cluster = cl_factor
centers = as.data.frame(cl$centers)
qplot(V2, V1, data = centers)
```

![](scala-wrapper_files/figure-markdown_github/unnamed-chunk-6-1.png)
