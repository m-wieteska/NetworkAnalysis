# NetworkAnalysis
# Project Description: use network analysis capabilities in R to understand/ discover how originally defined group of subject matter experts (SMEs) is performing. For that purpose gathered were two datasets: 1st) 1 month after the group was set up, 2nd) 4 months from the set up date. Data represents emails echange streams within SME groups and between indivuduals external to the SMEs group. Data visualization (network) waas used to present changes that happened to the originally defined group. 

# Data use: there will be two data sets to compare

* status in progress *
* second data set collected

# R code # 
---
title: "Netwok Analysis with R"  >>>> in progress
author: "Wieteska, Michal"
output:
  pdf_document: default
---
# set proper pdf encoding
```{r, echo=FALSE}
pdf.options(encoding='ISOLatin2')
```

# remove all lists
```{r}
ls()
rm(list = ls())
```


# intall/ load needed packages
install.packages("igraph")
library(igraph)

# read data - manual upload
```{r}
SMEnetw <- read.csv(file.choose(), header = T, sep = ";", fileEncoding="UTF-8-BOM")
str(SMEnetw)
#fix(SMEnetw)
SME_analysis <- data.frame(SMEnetw$SMEstart, SMEnetw$SMEend, SMEnetw$ContactFrequency)
SMEnetwork <- graph.data.frame(SME_analysis, directed = T)
```



E(SMEnetwork)

# see contact frequency
```{r}
V(SMEnetwork)$ContactFrequency <- degree(SMEnetwork)
hist(V(SMEnetwork)$ContactFrequency, breaks = 25, prob = T,
     col = 'dark blue',
     main = 'Connections distribution',
     ylab = 'Frequency',
     xlab = 'Number')
```

# basic plot
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.5,
     layout=layout.fruchterman.reingold)
```


# outliers detection
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.kamada.kawai)
```


# sphere view
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.sphere)
```


# circle
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.circle)
```

#who seems to be the boss?
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(56),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.star)
```



# connect key plots

```{r}
par(mfrow=c(2,2))
par(mar=c(0.25,0.25,0.1,0.1))
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter1",
     font.main=1,
     layout=layout.graphopt)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter2",
     font.main=1,
     layout=layout.kamada.kawai)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter3",
     font.main=1,
     layout=layout.sphere)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter4",
     font.main=1,
     #xlab = 'iter4',
     layout=layout.circle)
```



# Community detection, outlines grahically  community areas

* by dendrogram
```{r}
par(bg="lightblue") # set background

ceb <- cluster_edge_betweenness(SMEnetwork) 
dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
```     
* by network


```{r}


SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
cnet <- cluster_edge_betweenness(SMEnetwork2)

plot(cnet,
     SMEnetwork,
     vertex.size = 13,
     vertex.label.cex = 0.9,
     edge.arrow.size=0.1,
     vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
     layout=layout.graphopt)
```    


``` {r}

SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
cnet <- cluster_edge_betweenness(SMEnetwork2)

plot(cnet,
     SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter1",
     font.main=1,
     layout=layout.kamada.kawai)
```

```{r}
par(mfrow=c(2,1))
par(mar=c(0.15,0.15,0.5,0.5))

par(bg="lightblue") # set background

ceb <- cluster_edge_betweenness(SMEnetwork) 
dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")



SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
cnet <- cluster_edge_betweenness(SMEnetwork2)

plot(cnet,
     SMEnetwork,
     vertex.size = 13,
     vertex.label.cex = 0.9,
     edge.arrow.size=0.1,
     vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
     layout=layout.graphopt)

```     
