# NetworkAnalysis
# Project Description: use network analysis capabilities in R to understand/ discover how a defined group of subject matter experts (SMEs) is performing (interacting). 

* status in progress *

# R code #
---
title: "Social Network Analysis for Project SMEs with RStudio. (work in progres)"
author: "Wieteska, Michal"
output:
  pdf_document: default
  html_notebook: default
  html_document: default
---

* The of this project is an analysis of SMEs (Subject Matter Experts) invited to the project to provide specialty expertise with regards to project scope/ deliverables. The approach take here isusing  "social network analysis" concept (see wikipedia link below) with the aim to understand a community by mapping the relationships. These relationships connect them as a network, and then trying to draw out key individuals, groups within the network, associations between the individuals, outline connections intensivity etc.
A network is simply a number of nodes that are connected by links. These nodes are people (here SMEs) and the links are any social connection between them; here based on interaction justified by working on the same project/ theme.

* A general concept: see wikipedia: https://en.wikipedia.org/wiki/Social_network_analysis 
   * for key therms explanation see wikipedia https://en.wikipedia.org/wiki/Vertex_(graph_theory)
   * for a specific concepts see: https://en.wikipedia.org/wiki/HITS_algorithm

# Starting with RStudio

# Proper pdf encoding
```{r, echo=FALSE}
pdf.options(encoding='ISOLatin2')
```

# Remove all lists
```{r}
ls()
rm(list = ls())
```


# Install
install.packages("igraph")

# Load needed packages
```{r}
library(igraph)
```


# Read data - manual file location/ selection
```{r}
SMEnetw <- read.csv(file.choose(), header = T, sep = ";", fileEncoding="UTF-8-BOM")
SME_analysis <- data.frame(SMEnetw$SMEstart, SMEnetw$SMEend, SMEnetw$ContactFrequency)
library(igraph)
SMEnetwork <- graph.data.frame(SME_analysis, directed = TRUE)
```


# Network analysis key definitions & functions (igraph package)
* Data structure: str(SMEnetw)
* Edge (link between nodes), example: edge_density(SMEnetwork, loops = T), example: ecount(SMEnetwork)
* Vertex (node apex, point of connection for links), example: vcount(SMEnetwork)
* Reciprocity, example: reciprocity(SMEnetwork)   
* Closeness, example: closeness(SMEnetwork, mode='all', weights = NA)
* Betweennes - a Unique links to others in the network i.e. who gets most connections, example: betweenness(SMEnetwork, directed=TRUE, weights = NA)
* Degree - Connected to many individuals, number of connections: degree(SMEnetwork)
* Matrix  - contingency table: SMEnetwork[]
* Authority/ authority - an authority SME to be someone who is followed by many other hub SMEs, while a hub SME to be one who follows many authority SMEs 
   * Hubs (outbound links)
   * Authorities (inutbound links) 
* See number of 
   * all connections: degree(SMEnetwork, mode='all')
   * incoming connections: degree(SMEnetwork, mode='in')
   * outcoming connections: degree(SMEnetwork, mode='out')
   * see a network diameter: diameter(SMEnetwork, directed=F, weigths=NA)


# Imported data view/ examination to understand data structure
```{r}
str(SMEnetw)
head(SMEnetwork)
tail(SMEnetwork)
degree(SMEnetwork)
SMEnetwork[]
nrow(SMEnetw)
length(unique(SMEnetwork$SMEstart))
```


# A basic vs simplified graph (removed loops in the graph, multiple edges)
```{r}
par(mfrow=c(1,2))
plot(SMEnetwork)

SMEnetwork_nl <- simplify(SMEnetwork, remove.multiple = T, remove.loops = T)
plot(SMEnetwork_nl, edge.arrow.size=.4) # no loops
```

# Modified basic plot
```{r}

V(SMEnetwork)$ContactFrequency <- degree(SMEnetwork)

plot(SMEnetwork, 
     vertex.color = rainbow(53),
     vertex.shape="sphere",
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.5,
     layout=layout.fruchterman.reingold)
```

* Network very dense with a couple of outliers, seems like a key interactions ara happening within 1 group



# A view on outliers (probe)
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.kamada.kawai,
     main="Outliers",
     cex.main=0.2,
     font.main=2)
```
* Comments: 7 outlier identified with diversified number of connections startinf from 1



# 4 different view to get more insight

```{r}
par(mfrow=c(2,2))
par(mar=c(0.25,0.25,0.1,0.1))
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Dense",
     cex.main=0.5,
     font.main=1,
     layout=layout.graphopt)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="Stretched",
     cex.main=0.5,
     font.main=1,
     layout=layout.kamada.kawai)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.6,
     edge.arrow.size = 0.1,
     main="Sphere",
     cex.main=0.5,
     font.main=1,
     layout=layout.sphere)
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.6,
     edge.arrow.size = 0.1,
     main="Circle",
     cex.main=0.5,
     font.main=1,
     layout=layout.circle)
```
* Comments: visually it looks like D, G, R, S and U are actors with the most connections (interactions)


# Community detection (identify, outline grahically community areas)

## by dendrogram
```{r}
par(bg="white") # set background

ceb <- cluster_edge_betweenness(SMEnetwork) 
dendPlot(ceb, mode="hclust")     # plot(hcd, type = "triangle", ylab = "Height")
```     
* Comments: a big group of SMEs sit close interaction identified (green outline)


## by network
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

# Outlining paths - 3 views
``` {r}
par(mfrow=c(1,2))

clp <- cluster_label_prop(SMEnetwork)

plot(clp, SMEnetwork, 
     edge.arrow.size = 0.1,
     main="View A",
     cex.main=0.5,
     font.main=1,)



SMEnetwork1 <- igraph::as_data_frame(SMEnetwork) 
SMEnetwork2 <- graph.data.frame(SMEnetwork1, directed = F)
cnet <- cluster_edge_betweenness(SMEnetwork2)



plot(cnet,
     SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.1,
     main="View B",
     cex.main=0.1,
     font.main=1,
     layout=layout.kamada.kawai)
```

...cont. 
```{r}
# greedy method
coords = layout_with_fr(SMEnetwork)

c3 = cluster_edge_betweenness(SMEnetwork  * 1.5)

# modularity measure
modularity(c3)

# plot communities with shaded regions
plot_shaded_view <- plot(c3, SMEnetwork, edge.arrow.size = 0.25, layout=coords, main="View C"); plot_shaded_view

```


# Identification of Hubs and Authorities
```{r}

hs <- hub_score(SMEnetwork, weights=NA)$vector

as <- authority_score(SMEnetwork, weights=NA)$vector

par(mfrow=c(1,2))

 plot(SMEnetwork, vertex.size=hs*25, main="Hubs", edge.arrow.size = 0.2)

 plot(SMEnetwork, vertex.size=as*25, main="Authorities", edge.arrow.size = 0.2)
 
 #distances(SMEnetwork)

```


# Better zoom
```{r}
par(mfrow=c(1,2), mar=c(0,0,0,0))

l <- layout_with_fr(SMEnetwork)
l <- norm_coords(l, ymin=-1, ymax=1, xmin=-1, xmax=1)


plot(SMEnetwork, main="Highlevel: Authorities", rescale=F, layout=l*0.7, cex.main=0.1)
plot(SMEnetwork, vertex.shape="sphere", vertex.color = rainbow(53), vertex.size=as*25, main="Zooom: Authorities", edge.arrow.size = 0.5, edge.curved=.3, rescale=F, layout=l*4.7)
 # edge.color=c("gold", "blue",  "tomato", "grey", "red", "yellowgreen", "black"), rescale=F, layout=l*4.6)



```

# Additional analysis
```{r}
degree(SMEnetwork)
reciprocity(SMEnetwork)   
closeness(SMEnetwork, mode='all', weights = NA)
betweenness(SMEnetwork, directed=TRUE, weights = NA)
```


* Appendix - Additional view 

## Clustering
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
* comments: 6 outliers identified for dendrogram (outside green box) and network diagram (outside red area)

## Additional network views

* Other views

### Spherical view
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.sphere)
```


### Circle view
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.circle)
```

### Star view
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(56),
     # vertex.size = V(SMEnetwork)$degree*0.4,
     edge.arrow.size = 0.1,
     layout=layout.star)
```
