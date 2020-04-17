# NetworkAnalysis
# Project Description: use network analysis capabilities in R to understand/ discover how originally defined group of subject matter experts (SMEs) is performing. For that purpose gathered were two datasets: 1st) 1 month before the group was set up, 2nd) 4 months from the set up date. Data represents emails echange streams within SME groups and between indivuduals external to the SMEs group. Data visualization (network) waas used to present changes that happened to the originally defined group. 

# status in progress

# R code # 
---
title: "Netwok Analysis with R"
author: "Wieteska, Michal"
output:
  pdf_document: default
  html_notebook: default
  html_document: default
---

```{r, echo=FALSE}
pdf.options(encoding='ISOLatin2')
```

# remove all lists
```{r}
ls()
rm(list = ls())
```

* See github proj description

# set proper pdf encoding
```{r, echo=FALSE}
pdf.options(encoding='ISOLatin2')
```


# read data - manual upload
```{r}
SMEnetw <- read.csv(file.choose(), header = T, sep = ";")
str(SMEnetw)
fix(SMEnetw)
SME_analysis <- data.frame(SMEnetw$SMEstart, SMEnetw$SMEend, SMEnetw$ContactFrequency)
SMEnetwork <- graph.data.frame(SME_analysis, directed = T)
```

# intall/ load needed packages
install.packages("igraph")
library(igraph)

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


```{r}
set.seed(75)
plot(SMEnetwork)
```
```{r}
plot(SMEnetwork,
     vertex.color = rainbow(53),
     vertex.size = V(SMEnetwork)$ContactFrequency*0.4,
     edge.arrow.size = 0.5,
     layout=layout.fruchterman.reingold)
```
