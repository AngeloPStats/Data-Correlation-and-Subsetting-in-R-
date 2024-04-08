# Data-Correlation-Subsetting-in-R-
This exercise involves data analysis using R code. We incorporate variable correlation in our design matrix to proceed with further analysis.


```
Download the winequality-red data from https://archive.ics.uci.edu/dataset/186/wine+quality

I have renamed it as vinodf

```



    install.packages("readr")
    
    install.packages("dplyr")
    
    install.packages("corrplot")
    
    install.packages("RcolorBrewer")
    
    library(dplyr)
    
    library(readr)
    
    library(corrplot)
    
    library(RColorBrewer)
    
    vinosdf = read.csv("wdata.csv", h=T, sep = ",")
    
    head(vinosdf)
    
    
    vdf= vinosdf %>%
        group_by(quality) %>%
        summarise(across(where(is.numeric), ~ mean(.x, na.rm = TRUE)))
    
    head(vdf)
    
    
    
    CorrelMatrix = cor(vdf)
    
    CorrelMatrix = round(CorrelMatrix,1)
    
    ## Visualizing the correlation matrix for red wines
    
    brewer.pal(9, "Set1")
    
    
    colores = colorRampPalette( brewer.pal(7, "Set1"))
    
    
    corrplot(CorrelMatrix, method="color", col=colores(30),  
             type="upper", order="hclust", 
             addCoef.col = "black", 
             tl.col="black", tl.srt=90, 
             diag=FALSE
    )



```
## Download the winequality-red data from https://archive.ics.uci.edu/dataset/186/wine+quality
## I have rename it as vinodf

## Here are my REFERENCES:

## Dataset: https://archive.ics.uci.edu/dataset/186/wine+quality

## https://dplyr.tidyverse.org/reference/summarise_all.html

## https://stackoverflow.com/questions/74125738/getting-a-color-name-in-an-r-color-palette

## http://www.sthda.com/english/wiki/visualize-correlation-matrix-using-correlogram#google_vignette


```
