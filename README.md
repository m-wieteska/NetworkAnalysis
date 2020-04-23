# NetworkAnalysis
# Project Description: use network analysis capabilities in R to understand/ discover how originally defined group of subject matter experts (SMEs) is performing. For that purpose gathered were two datasets: 1st) 1 month after the group was set up, 2nd) 4 months from the set up date. Data represents emails echange streams within SME groups and between indivuduals external to the SMEs group. Data visualization (network) was used to present changes that happened to the originally defined group. 

# Data use: there will be two data sets to compare

* status in progress *
* second data set collected

# R code # v4
---
title: "Network Analysis with R ---> work in progres"
author: "Wieteska, Michal"
output:
  pdf_document: default
  html_notebook: default
  html_document: default
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


# install/ load needed packages
install.packages("igraph")
library(igraph)

# read data - manual selection
```{r}
SMEnetw <- read.csv(file.choose(), header = T, sep = ";", fileEncoding="UTF-8-BOM")
str(SMEnetw)
#fix(SMEnetw)
SME_analysis <- data.frame(SMEnetw$SMEstart, SMEnetw$SMEend, SMEnetw$ContactFrequency)
library(igraph)
SMEnetwork <- graph.data.frame(SME_analysis, directed = TRUE)
```


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
     vertex.shape="sphere",
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.5,
     layout=layout.fruchterman.reingold)

#lot(net2, vertex.shape="none", vertex.label=nodes2$media,

 #    vertex.label.color=V(net2)$color, vertex.label.font=2.5, 

  #   vertex.label.cex=.6, edge.color="gray70",  edge.width=2)

```


# outliers detection (probe)
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.kamada.kawai)
```


# spherical view
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

#star
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
     cex.main=0.5,
     font.main=1,
     layout=layout.graphopt)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter2",
     cex.main=0.5,
     font.main=1,
     layout=layout.kamada.kawai)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter3",
     cex.main=0.5,
     font.main=1,
     layout=layout.sphere)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Iter4",
     cex.main=0.5,
     font.main=1,
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
     vertex.shape="rectangle",
     vertex.label.dist=0.0,
     edge.arrow.mode=0,
     vertex.size = V(SMEnetwork2)$ContactFrequency*0.2,
     layout=layout.graphopt)

```    

# outlining paths
``` {r}
clp <- cluster_label_prop(SMEnetwork)

plot(clp, SMEnetwork,  edge.arrow.size = 0.3)
```


``` {r}

SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
cnet <- cluster_edge_betweenness(SMEnetwork2)



plot(cnet,
     SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.25,
     main="Iter1",
     #cex.main=0.5,
     font.main=1,
     layout=layout.kamada.kawai)
```

```{r}
# greedy method (hiearchical, fast method)
coords = layout_with_fr(SMEnetwork)

c3 = cluster_edge_betweenness(SMEnetwork  * 1.5)

# modularity measure
modularity(c3)

# plot communities with shaded regions
plot_shaded_view <- plot(c3, SMEnetwork, edge.arrow.size = 0.25, layout=coords); plot_shaded_view
```




```{r}

hs <- hub_score(SMEnetwork, weights=NA)$vector

as <- authority_score(SMEnetwork, weights=NA)$vector



par(mfrow=c(1,2))

 plot(SMEnetwork, vertex.size=hs*25, main="Hubs", edge.arrow.size = 0.2)

 plot(SMEnetwork, vertex.size=as*25, main="Authorities", edge.arrow.size = 0.2)
 
 #distances(SMEnetwork)

```



```{r}
par(mfrow=c(1,2))
par(mar=c(0.1,0.1,0.75,0.75))

par(bg="white") # set background

ceb <- cluster_edge_betweenness(SMEnetwork) 
dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")


# greedy method (hiearchical, fast method)
coords = layout_with_fr(SMEnetwork)

c3 = cluster_edge_betweenness(SMEnetwork  * 1.5)

# modularity measure
modularity(c3)

# plot communities with shaded regions
plot_shaded_view <- plot(c3, SMEnetwork, edge.arrow.size = 0.25, layout=coords); plot_shaded_view

```     
# comments: 6 outliers identified for dendrogram (outside green box) and network diagram (outside red area)

# additional analysis - do some some zoom for details


```{r}
par(mfrow=c(1,2), mar=c(0,0,0,0))

l <- layout_with_fr(SMEnetwork)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)


plot(SMEnetwork, main="Highlevel: Authorities", rescale=F, layout=l*0.7, cex.main=0.1)
plot(SMEnetwork, vertex.shape="sphere", vertex.color = rainbow(53), vertex.size=as*25, main="Zooom: Authorities", edge.arrow.size = 0.5, edge.curved=.3, rescale=F, layout=l*4.7)
 # edge.color=c("gold", "blue",  "tomato", "grey", "red", "yellowgreen", "black"), rescale=F, layout=l*4.6)

```
